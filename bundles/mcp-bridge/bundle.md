---
bundle:
  name: mcp-bridge
  version: 1.0.0
  description: Bridge to Model Context Protocol (MCP) ecosystem - use any MCP-compatible tool server

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # MCP tool integration
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-mcp
  - bundle: git+https://github.com/robotdad/amplifier-module-tool-mcp
  - bundle: git+https://github.com/marklicata/mcp-tool-router
  
  # Plugin compatibility
  - bundle: git+https://github.com/robotdad/amplifier-bundle-plugin-compat
  
  # MCP server (expose Amplifier as MCP)
  - bundle: git+https://github.com/ramparte/amplifier-mcp-server
---

# MCP Bridge Bundle

@mcp-bridge:context/mcp-instructions.md

---

## Capabilities

- Connect to any MCP-compatible tool server
- Route tools between multiple MCP servers
- Expose Amplifier capabilities as MCP server
- Claude Desktop / VS Code Copilot compatibility
- Protocol translation layer

## Use Cases

- Use Claude MCP servers with Amplifier
- Connect to third-party MCP tool providers
- Run Amplifier as an MCP server for other clients
- Mix MCP and native Amplifier tools

## Configuration

MCP servers are configured in settings.yaml:
```yaml
mcp:
  servers:
    - name: filesystem
      command: npx -y @anthropic/mcp-server-filesystem
    - name: github  
      command: npx -y @anthropic/mcp-server-github
```
