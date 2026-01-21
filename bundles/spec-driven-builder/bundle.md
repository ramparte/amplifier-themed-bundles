---
bundle:
  name: spec-driven-builder
  version: 1.0.0
  description: Build products from specifications using outcome-focused development methodology

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Methodology (Chris Park's patterns)
  - bundle: git+https://github.com/cpark4x/outcomist
  - bundle: git+https://github.com/cpark4x/remember-twelve
  
  # Deliberate development (planning-first)
  - bundle: git+https://github.com/ramparte/amplifier-bundle-deliberate-development
  
  # Strategic advisor
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-sage
  
  # Decision tracking
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-decisionmemory
  
  # Memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Spec-Driven Builder Bundle

@spec-driven-builder:context/spec-instructions.md

---

## Philosophy

Build what matters. Ship outcomes, not features.

## Workflow

1. **Outcome Definition** - What success looks like
2. **Specification** - Detailed, testable requirements  
3. **Decomposition** - Break into implementable units
4. **Implementation** - Build from spec, not imagination
5. **Validation** - Verify against original outcome

## Key Principles

- Specs before code
- Outcomes over output
- Transparency in execution
- Iterative refinement
