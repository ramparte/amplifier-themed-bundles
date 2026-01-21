---
bundle:
  name: multi-agent-coordinator
  version: 1.0.0
  description: Orchestrate multiple AI agents collaborating via shared context and message passing

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # M365 collaboration (verified working)
  - bundle: git+https://github.com/ramparte/amplifier-bundle-m365-collab
---

# Multi-Agent Coordinator Bundle

@multi-agent-coordinator:context/coordinator-instructions.md

---

## Capabilities

- Multi-instance AI collaboration
- Foreman/worker orchestration patterns  
- M365-based agent coordination (SharePoint message passing)
- Shared context management
- Observer patterns for monitoring
- Multi-provider interoperability

## Patterns

- **Foreman**: One coordinating agent, multiple workers
- **Lattice**: Peer-to-peer via M365
- **Observer**: Monitor and react to agent events
