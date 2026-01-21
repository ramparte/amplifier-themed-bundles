---
bundle:
  name: autonomous-agent
  version: 1.0.0
  description: Long-running autonomous execution with strategic planning and worker coordination

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Strategic planning (Sage)
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-sage
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-sage
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-sage-eval
  
  # Orchestration (Foreman pattern)
  - bundle: git+https://github.com/payneio/amplifier-bundle-foreman
  - bundle: git+https://github.com/payneio/amplifier-bundle-observers
  - bundle: git+https://github.com/payneio/amplifier-module-orchestrator-work-coordinator
  
  # Decision memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-decisionmemory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
  
  # Monitoring
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-hooks-sessionindicator
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-iteration-tracker
---

# Autonomous Agent Bundle

@autonomous-agent:context/autonomous-instructions.md

---

## Capabilities

- Long-running autonomous execution
- Strategic planning with Gemini/OpenAI counsel (Sage)
- Worker pool orchestration (Foreman pattern)
- Decision memory and tracking
- Progress monitoring and stuck detection
- Transparent execution logs

## Warning

This bundle enables autonomous operation. Use with appropriate guardrails.
