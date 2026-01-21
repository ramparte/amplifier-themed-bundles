---
bundle:
  name: project-manager
  version: 1.0.0
  description: Project and team coordination toolkit for tech leads and project managers

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Git and PR management
  - bundle: git+https://github.com/kenotron-ms/amplifier-git-workflow
  - bundle: git+https://github.com/kenotron-ms/pr-monitor
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-github
  - bundle: git+https://github.com/marklicata/amplifier-bundle-issues
  
  # Team coordination
  - bundle: git+https://github.com/kenotron-ms/standup-helper
  - bundle: git+https://github.com/marklicata/made-activity-tracker
  
  # Task tracking
  - bundle: git+https://github.com/robotdad/amplifier-bundle-beads
  - bundle: git+https://github.com/ramparte/amplifier-bundle-beads-superpowers
  
  # Memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Project Manager Bundle

@project-manager:context/pm-instructions.md

---

## Capabilities

- PR monitoring and status tracking
- Team activity tracking
- Standup report generation
- Git-backed task persistence (Beads)
- GitHub issue management
- Multi-repo coordination

## Daily Workflow

1. Check PR status across repos
2. Generate standup report
3. Review team activity
4. Triage new issues
5. Update task board
