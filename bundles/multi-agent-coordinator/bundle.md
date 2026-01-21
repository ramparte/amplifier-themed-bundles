---
bundle:
  name: multi-agent-coordinator
  version: 1.0.0
  description: Orchestrate multiple AI agents collaborating via shared context and message passing

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Collaboration core
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-collaboration
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-collab-core
  
  # Orchestration patterns
  - bundle: git+https://github.com/payneio/amplifier-bundle-foreman
  - bundle: git+https://github.com/payneio/amplifier-bundle-observers
  - bundle: git+https://github.com/payneio/amplifier-module-orchestrator-work-coordinator
  - bundle: git+https://github.com/payneio/amplifier-orchestration
  
  # M365 coordination
  - bundle: git+https://github.com/robotdad/lattice
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-m365
  - bundle: git+https://github.com/ramparte/amplifier-bundle-m365-collab
  
  # Context management
  - bundle: git+https://github.com/microsoft/amplifier-module-context-simple
  - bundle: git+https://github.com/sadlilas/amplifier-module-util-context
  
  # Interop
  - bundle: git+https://github.com/DavidKoleczek/interop-router
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
