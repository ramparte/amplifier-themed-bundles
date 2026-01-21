---
bundle:
  name: full-stack-developer
  version: 1.0.0
  description: Comprehensive development environment with code intelligence, quality tools, and git workflows

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # TypeScript development
  - bundle: git+https://github.com/robotdad/amplifier-bundle-lsp-typescript
  - bundle: git+https://github.com/robotdad/amplifier-bundle-ts-dev
  
  # Python development (from foundation)
  - bundle: amplifier-bundle-python-dev
  
  # Git workflow
  - bundle: git+https://github.com/kenotron-ms/amplifier-git-workflow
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-github
  
  # Memory for project context
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-hooks-project-isolation
  
  # Testing
  - bundle: git+https://github.com/samueljklee/amplifier-bundle-smoke-test
---

# Full-Stack Developer Bundle

@full-stack-developer:context/developer-instructions.md

---

## Capabilities

- Semantic code intelligence (LSP for TypeScript, Python)
- Code quality and linting automation
- Git workflow automation (commits, PRs, branches)
- Testing and benchmarking
- Session-aware memory for project context
- File operations with safety guardrails

## Languages Supported

- TypeScript/JavaScript (full LSP)
- Python (full quality tooling)
- Other languages (basic support)
