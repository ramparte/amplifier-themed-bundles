---
bundle:
  name: security-analyst
  version: 1.0.0
  description: Security-focused toolkit for code analysis, vulnerability scanning, and security reviews

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Security scanning
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-codeql
  
  # GitHub security integration
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-github
  - bundle: git+https://github.com/marklicata/amplifier-bundle-issues
  
  # Code intelligence for analysis
  - bundle: git+https://github.com/robotdad/amplifier-bundle-lsp-typescript
  - bundle: amplifier-bundle-python-dev
  
  # Code quality (includes security lints)
  - bundle: git+https://github.com/ramparte/amplifier-bundle-metacog-code-quality
  
  # Memory for tracking findings
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-tool-memory
---

# Security Analyst Bundle

@security-analyst:context/security-instructions.md

---

## Capabilities

- CodeQL security scanning
- Code vulnerability analysis
- GitHub security integration (Dependabot, advisories)
- Remediation suggestions with AI
- Security review workflows
- Finding tracking and reporting

## Usage

```
"Scan this codebase for SQL injection vulnerabilities"
"Review the authentication module for security issues"
"Generate a security report for the PR"
```
