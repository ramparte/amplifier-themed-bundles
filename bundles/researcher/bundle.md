---
bundle:
  name: researcher
  version: 1.0.0
  description: Deep research assistant combining multi-source web research, synthesis, and persistent memory

includes:
  # Core foundation
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Research capabilities
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-deepresearch
  - bundle: git+https://github.com/robotdad/amplifier-bundle-deepresearch
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-rlm
  
  # Memory & context
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
  
  # Strategic advisor
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-sage
---

# Researcher Bundle

@researcher:context/researcher-instructions.md

---

Deep research assistant for comprehensive investigations spanning multiple sources and sessions.

## Capabilities

- Multi-source web research with synthesis
- Long context processing (RLM)
- Cross-session memory persistence
- Strategic research planning with Sage advisor
- Citation and source tracking

## Usage

Start a research session:
```
"Research the history and current state of quantum computing applications"
"Deep dive into competitive landscape for AI coding assistants"
```
