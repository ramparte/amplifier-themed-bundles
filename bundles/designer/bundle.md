---
bundle:
  name: designer
  version: 1.0.0
  description: Design-focused toolkit for product designers and UX researchers

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Discovery & user research
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-discovery
  
  # Design intelligence
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-design-intelligence
  - bundle: git+https://github.com/anderlpz/amplifier-embody
  
  # Vision analysis
  - bundle: git+https://github.com/anderlpz/amplifier-app-vision
  
  # Memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Designer Bundle

@designer:context/designer-instructions.md

---

## Capabilities

- Progressive user interviewing (Discovery)
- Design system exploration
- Vision/image analysis (GPT-4V)
- Design principles documentation
- User research synthesis

## Key Agents

- **discovery-interviewer**: Conducts progressive user interviews
- **design-explorer**: Explores and refines design systems
- **vision-analyst**: Analyzes designs and images
