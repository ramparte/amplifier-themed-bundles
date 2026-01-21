# Multi-Agent Coordination Instructions

This bundle enables orchestration of multiple AI agents working together through shared context, message passing, and structured coordination patterns.

## Core Coordination Patterns

### 1. Foreman Pattern

A hierarchical model where one coordinating agent (foreman) manages multiple worker agents.

**When to use:**
- Complex tasks requiring decomposition
- Parallel execution of subtasks
- Quality control and aggregation needs

**Implementation:**
```
Foreman Agent
├── Decomposes task into subtasks
├── Assigns work to worker agents
├── Monitors progress and handles failures
├── Aggregates results
└── Reports completion

Worker Agents
├── Receive assigned subtasks
├── Execute independently
├── Report status and results
└── Request clarification when blocked
```

**Coordination Protocol:**
1. Foreman creates task manifest with subtask definitions
2. Workers claim or are assigned subtasks
3. Workers update status via shared context
4. Foreman polls for completion or receives callbacks
5. Foreman validates and integrates results

### 2. Lattice Pattern (Peer-to-Peer)

Decentralized coordination where agents communicate as equals through M365 infrastructure.

**When to use:**
- No natural hierarchy exists
- Agents have overlapping capabilities
- Resilience to single-agent failure required

**Implementation:**
- Agents publish capabilities to shared registry
- Message passing via SharePoint lists or Teams channels
- Consensus mechanisms for conflict resolution
- Self-organizing task distribution

**Message Types:**
- `ANNOUNCE`: Broadcast capability or status
- `REQUEST`: Ask for help or information
- `RESPONSE`: Reply to a request
- `CLAIM`: Stake ownership of a task
- `RELEASE`: Relinquish a claimed task
- `SYNC`: Request state synchronization

### 3. Observer Pattern

Monitoring agents that watch for events and trigger actions.

**When to use:**
- Reactive workflows triggered by external events
- Audit and logging requirements
- Escalation and alerting needs

**Implementation:**
- Observers subscribe to event streams
- Pattern matching on events triggers handlers
- Can spawn new agents or modify existing workflows
- Maintains event history for debugging

## Context Sharing Strategies

### Shared Context Store

A central repository for coordination state accessible by all agents.

**Structure:**
```yaml
context:
  session_id: "coord-2024-001"
  started_at: "2024-01-15T10:00:00Z"
  
  agents:
    - id: "foreman-1"
      role: "coordinator"
      status: "active"
    - id: "worker-1"
      role: "executor"
      status: "busy"
      current_task: "task-003"
  
  tasks:
    - id: "task-001"
      status: "completed"
      assigned_to: "worker-1"
      result_ref: "/results/task-001.json"
    - id: "task-002"
      status: "in_progress"
      assigned_to: "worker-2"
    - id: "task-003"
      status: "pending"
      dependencies: ["task-001"]
  
  messages:
    - from: "foreman-1"
      to: "all"
      type: "directive"
      content: "Begin phase 2"
      timestamp: "2024-01-15T10:30:00Z"
```

### Context Isolation Levels

1. **Global Context**: Visible to all agents (coordination state, shared resources)
2. **Team Context**: Visible to agent groups (project-specific data)
3. **Private Context**: Agent-only (working memory, intermediate results)

### Context Synchronization

- **Push Model**: Agents broadcast changes immediately
- **Pull Model**: Agents poll for updates at intervals
- **Hybrid**: Critical updates push, bulk data pulls

## Message Passing Protocol

### Via M365 (SharePoint/Teams)

```yaml
# SharePoint List Schema for Messages
columns:
  - MessageId: text (unique)
  - FromAgent: text
  - ToAgent: text (or "broadcast")
  - MessageType: choice [request, response, status, error]
  - Priority: choice [low, normal, high, critical]
  - Payload: multiline text (JSON)
  - CreatedAt: datetime
  - ProcessedAt: datetime
  - ProcessedBy: text
```

### Message Flow Example

```
Agent A                    SharePoint                  Agent B
   |                           |                          |
   |-- POST message ---------> |                          |
   |                           |<---- poll for messages --|
   |                           |-- return new messages -->|
   |                           |                          |-- process
   |                           |<---- POST response ------|
   |<---- poll for responses --|                          |
   |-- process response        |                          |
```

## Orchestration Workflows

### Task Decomposition Workflow

1. **Analyze**: Foreman receives complex task
2. **Decompose**: Break into atomic subtasks
3. **Dependency Map**: Identify task ordering requirements
4. **Assign**: Distribute to available workers
5. **Monitor**: Track progress, handle failures
6. **Aggregate**: Combine results
7. **Validate**: Verify completeness and quality
8. **Report**: Deliver final result

### Error Handling

- **Retry**: Automatic retry with exponential backoff
- **Reassign**: Move failed task to different worker
- **Escalate**: Alert foreman or human supervisor
- **Compensate**: Undo partial work if task fails

### Deadlock Prevention

- Timeout on all waiting operations
- Resource acquisition ordering
- Deadlock detection via dependency graph analysis
- Preemption of lower-priority tasks

## Interoperability

### Multi-Provider Support

The interop-router enables coordination across different AI providers:

- Route tasks to appropriate provider based on capabilities
- Normalize responses for consistent handling
- Fallback chains for reliability
- Cost optimization through provider selection

### Protocol Translation

- Adapt message formats between systems
- Handle capability differences gracefully
- Maintain semantic consistency

## Best Practices

1. **Idempotent Operations**: Design tasks to be safely retryable
2. **Clear Ownership**: Every task has exactly one owner at any time
3. **Explicit State**: Persist all coordination state for recovery
4. **Bounded Waiting**: Never wait indefinitely; use timeouts
5. **Graceful Degradation**: Partial results better than no results
6. **Audit Trail**: Log all coordination events for debugging
7. **Resource Limits**: Cap concurrent agents and tasks
8. **Health Checks**: Regular liveness probes for all agents

## Configuration

```yaml
coordinator:
  max_workers: 10
  task_timeout_minutes: 30
  message_poll_interval_seconds: 5
  retry_max_attempts: 3
  retry_backoff_multiplier: 2
  
  context_store:
    type: "sharepoint"
    site: "https://tenant.sharepoint.com/sites/AgentCoordination"
    list: "CoordinationContext"
    
  message_queue:
    type: "sharepoint_list"
    site: "https://tenant.sharepoint.com/sites/AgentCoordination"
    list: "AgentMessages"
```
