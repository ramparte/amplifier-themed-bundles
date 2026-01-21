---
bundle:
  name: information-worker
  version: 1.0.0
  description: Enterprise productivity suite with M365, Slack, and collaboration tools

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Collaboration core
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-collaboration
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-collab-core
  
  # M365 integration
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-m365
  - bundle: git+https://github.com/robotdad/lattice
  
  # Slack
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-slack
  
  # Productivity tools
  - bundle: git+https://github.com/bkrabach/amplifier-bundle-attention-firewall
  - bundle: git+https://github.com/kenotron-ms/standup-helper
  - bundle: git+https://github.com/marklicata/made-activity-tracker
  
  # Memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Information Worker Bundle

@information-worker:context/worker-instructions.md

---

## Capabilities

- M365 integration (Teams, Outlook, SharePoint)
- Slack channel management
- Intelligent notification filtering (Attention Firewall)
- Cross-platform task coordination
- Team activity tracking
- Standup report generation

## Requirements

- Microsoft 365 credentials (for M365 features)
- Slack API token (for Slack features)
- Windows 10/11 (for Attention Firewall)
