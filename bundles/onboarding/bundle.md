---
bundle:
  name: onboarding
  version: 1.0.0
  description: Guided onboarding experience for new Amplifier users

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Onboarding materials
  - bundle: git+https://github.com/marklicata/amplifier-onboarding
  - bundle: git+https://github.com/kenotron-ms/amplifier-setup
  
  # Expert resources
  - bundle: git+https://github.com/bkrabach/amplifier-expert-cookbook
  - bundle: git+https://github.com/kenotron-ms/awesome-amplifier
  
  # Careful assistant (asks before acting)
  - bundle: git+https://github.com/ramparte/new-user-assistant
  
  # Presentations
  - bundle: git+https://github.com/kenotron-ms/amplifier-presentation
  
  # Skills system
  - bundle: git+https://github.com/microsoft/amplifier-module-tool-skills
---

# Onboarding Bundle

@onboarding:context/onboarding-instructions.md

---

## For New Users

This bundle is designed to help you learn Amplifier safely:

- **Asks before acting** - Shows plans, gets approval
- **Explains as it goes** - Educational commentary
- **Progressive disclosure** - Introduces features gradually
- **Safe defaults** - Conservative tool usage

## Learning Path

1. Basic commands and chat
2. File operations
3. Git and code workflows
4. Bundle customization
5. Advanced patterns
