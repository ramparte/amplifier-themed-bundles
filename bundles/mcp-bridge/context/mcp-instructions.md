# MCP Bridge Instructions

This bundle enables integration with the Model Context Protocol (MCP) ecosystem, allowing Amplifier to connect with MCP-compatible tool servers and expose its own capabilities as an MCP server.

## MCP Server Configuration

### Configuring MCP Servers in settings.yaml

Add MCP servers to your `settings.yaml` file:

```yaml
mcp:
  # Connection timeout in seconds
  timeout: 30
  
  # Auto-start servers on session init
  auto_start: true
  
  servers:
    # Anthropic official servers
    - name: filesystem
      command: npx -y @anthropic/mcp-server-filesystem
      args:
        - /path/to/allowed/directory
      
    - name: github
      command: npx -y @anthropic/mcp-server-github
      env:
        GITHUB_TOKEN: ${GITHUB_TOKEN}
    
    - name: sqlite
      command: npx -y @anthropic/mcp-server-sqlite
      args:
        - --database
        - /path/to/database.db
    
    # Custom MCP servers
    - name: custom-server
      command: python
      args:
        - -m
        - my_mcp_server
      cwd: /path/to/server
      env:
        API_KEY: ${CUSTOM_API_KEY}
```

### Server Configuration Options

| Option | Description | Required |
|--------|-------------|----------|
| `name` | Unique identifier for the server | Yes |
| `command` | Executable to run | Yes |
| `args` | Command line arguments | No |
| `cwd` | Working directory | No |
| `env` | Environment variables | No |
| `timeout` | Server-specific timeout | No |

## Tool Routing Patterns

### Automatic Tool Discovery

When an MCP server connects, its tools are automatically discovered and registered with a namespace prefix:

```
mcp.<server-name>.<tool-name>
```

Example: A `read_file` tool from the `filesystem` server becomes `mcp.filesystem.read_file`.

### Priority Routing

When multiple servers provide similar tools, configure priority:

```yaml
mcp:
  routing:
    # Prefer native tools over MCP when available
    prefer_native: true
    
    # Server priority for conflicting tools
    priority:
      - filesystem  # First choice
      - github      # Second choice
      - custom      # Fallback
```

### Tool Aliasing

Create shortcuts for frequently used MCP tools:

```yaml
mcp:
  aliases:
    read: mcp.filesystem.read_file
    write: mcp.filesystem.write_file
    search: mcp.github.search_repositories
```

## Running Amplifier as MCP Server

Expose Amplifier's capabilities to other MCP clients (Claude Desktop, VS Code Copilot):

### Starting the Server

```bash
amplifier serve --mcp --port 3000
```

### Configuration

```yaml
mcp_server:
  enabled: true
  port: 3000
  
  # Expose specific tools
  expose_tools:
    - read_file
    - write_file
    - bash
    - grep
    - glob
  
  # Hide internal tools
  hide_tools:
    - recipes
    - todo
```

### Claude Desktop Integration

Add to your Claude Desktop config (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "amplifier": {
      "command": "amplifier",
      "args": ["serve", "--mcp"]
    }
  }
}
```

### VS Code Copilot Integration

Add to your VS Code settings:

```json
{
  "github.copilot.chat.mcpServers": {
    "amplifier": {
      "command": "amplifier",
      "args": ["serve", "--mcp"]
    }
  }
}
```

## Compatibility Notes

### Protocol Version Support

- MCP Protocol 2024-11-05: Full support
- MCP Protocol 2024-10-07: Full support
- Earlier versions: Limited compatibility

### Transport Mechanisms

| Transport | Status | Notes |
|-----------|--------|-------|
| stdio | Supported | Default, most compatible |
| HTTP/SSE | Supported | For networked deployments |
| WebSocket | Experimental | Coming soon |

### Known Limitations

1. **Streaming responses**: MCP streaming is translated to Amplifier's native format
2. **Resource subscriptions**: Not all MCP resource subscription patterns are supported
3. **Prompts**: MCP prompt templates require manual invocation

### Error Handling

MCP errors are mapped to Amplifier error codes:

| MCP Error | Amplifier Handling |
|-----------|-------------------|
| `MethodNotFound` | Tool not available error |
| `InvalidParams` | Parameter validation error |
| `InternalError` | Retry with backoff |
| `ConnectionClosed` | Auto-reconnect (configurable) |

## Security Considerations

### Tool Sandboxing

```yaml
mcp:
  security:
    # Restrict MCP tools to specific directories
    filesystem_roots:
      - /home/user/projects
      - /tmp/amplifier
    
    # Block dangerous operations
    blocked_operations:
      - shell_execute
      - system_command
```

### Authentication

For remote MCP servers:

```yaml
mcp:
  servers:
    - name: remote-server
      url: https://mcp.example.com
      auth:
        type: bearer
        token: ${MCP_AUTH_TOKEN}
```

## Troubleshooting

### Server Won't Start

1. Check the command exists: `which npx`
2. Verify environment variables are set
3. Check server logs: `amplifier logs --mcp filesystem`

### Tools Not Appearing

1. Verify server connection: `amplifier mcp status`
2. Check tool discovery: `amplifier mcp tools <server-name>`
3. Restart the server: `amplifier mcp restart <server-name>`

### Connection Timeouts

Increase timeout values:

```yaml
mcp:
  timeout: 60
  servers:
    - name: slow-server
      timeout: 120
```
