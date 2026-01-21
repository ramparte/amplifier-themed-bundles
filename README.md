# Amplifier Themed Bundles

A collection of **15 archetype bundles** for the [Amplifier](https://github.com/microsoft/amplifier) AI agent framework. Each bundle composes ecosystem tools into a cohesive experience for a specific user persona.

## Quick Start

```bash
# Use a bundle directly
amplifier run --bundle bundles/researcher/bundle.md "Help me research quantum computing"

# Or register and set as default
amplifier bundle add bundles/researcher/bundle.md --name researcher
amplifier bundle use researcher
amplifier
```

## Available Bundles

### Tier 1: Production-Ready

| Bundle | Archetype | Description |
|--------|-----------|-------------|
| [**researcher**](bundles/researcher/) | Analyst | Deep research with multi-source synthesis, Sage strategic advisor, and cross-session memory |
| [**designer**](bundles/designer/) | UX/Product | User interviewing (Discovery), design intelligence, GPT-4V vision analysis |
| [**evaluator**](bundles/evaluator/) | QA/Testing | AI benchmarking, eval-recipes, session analysis, smoke testing |
| [**full-stack-developer**](bundles/full-stack-developer/) | Developer | LSP code intelligence (TypeScript + Python), git workflows, quality tooling |
| [**information-worker**](bundles/information-worker/) | Business | M365 + Slack integration, attention firewall, standup generation |

### Tier 2: Advanced Patterns

| Bundle | Archetype | Description |
|--------|-----------|-------------|
| [**autonomous-agent**](bundles/autonomous-agent/) | Power User | Long-running execution with Sage counsel and Foreman worker orchestration |
| [**voice-interface**](bundles/voice-interface/) | Accessibility | Voice-first interaction with whisper.cpp (local STT) and OpenAI Realtime |
| [**security-analyst**](bundles/security-analyst/) | DevSecOps | CodeQL scanning, OWASP guidance, security review workflows |
| [**content-creator**](bundles/content-creator/) | Writer | Blog generation, presentations, doc-evergreen, multi-format output |
| [**multi-agent-coordinator**](bundles/multi-agent-coordinator/) | AI Architect | Foreman/Lattice patterns, M365 agent collaboration, interop routing |
| [**local-first**](bundles/local-first/) | Privacy | 100% local operation with Foundry Local, SQLite storage, whisper.cpp |

### Tier 3: Specialized

| Bundle | Archetype | Description |
|--------|-----------|-------------|
| [**project-manager**](bundles/project-manager/) | Tech Lead | PR monitoring, standup reports, Beads task tracking, GitHub issues |
| [**onboarding**](bundles/onboarding/) | Learner | Guided learning with careful assistant, progressive feature disclosure |
| [**spec-driven-builder**](bundles/spec-driven-builder/) | Entrepreneur | Outcome-focused development with deliberate planning methodology |
| [**mcp-bridge**](bundles/mcp-bridge/) | Integrator | Bridge to MCP ecosystem - use any MCP-compatible tool server |

## Bundle Structure

Each bundle follows the standard Amplifier bundle format:

```
bundles/<name>/
├── bundle.md                    # Main bundle manifest with includes
└── context/
    └── <name>-instructions.md   # Archetype-specific guidance
```

### Example: researcher bundle

```yaml
# bundles/researcher/bundle.md
---
bundle:
  name: researcher
  version: 1.0.0
  description: Deep research assistant

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: git+https://github.com/michaeljabbour/amplifier-module-deepresearch
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-sage
  - bundle: git+https://github.com/michaeljabbour/amplifier-bundle-memory
---
```

## Ecosystem Inventory

This repo includes comprehensive documentation of the Amplifier ecosystem:

| File | Description |
|------|-------------|
| [`amplifier-ecosystem-inventory.yaml`](amplifier-ecosystem-inventory.yaml) | **250+ projects** cataloged with descriptions, readiness levels, and links |
| [`themed-bundle-proposals.yaml`](themed-bundle-proposals.yaml) | Original bundle design proposals with rationale |
| [`capability-gaps.yaml`](capability-gaps.yaml) | **45 identified gaps** with priority and bundle impact analysis |

## Key Contributors

These bundles compose work from across the Amplifier community:

| Contributor | Focus Areas | Notable Repos |
|-------------|-------------|---------------|
| **robotdad** | Providers, LSP, voice | amplifier-app-voice, lsp-typescript, deepresearch |
| **michaeljabbour** | Memory, collaboration, Sage | amplifier-bundle-sage, tool-memory, collaboration |
| **samueljklee** | Core infrastructure, testing | amplifier-foundation, smoke-test, foundry-local |
| **anderlpz** | Design, Discovery | amplifier-bundle-discovery, design-intelligence |
| **payneio** | Orchestration | amplifier-bundle-foreman, orchestration |
| **bkrabach** | Apps, creative tools | cortex, claude-trace-viewer, attention-firewall |
| **cpark4x** | Methodology | outcomist, workspaces3 |
| **ramparte** | Bundles, methodology | deliberate-development, beads-superpowers, dev-memory |
| **DavidKoleczek** | Evaluation | eval-recipes, benchmarks, session-analyzer |
| **marklicata** | Modules, GitHub | tool-github, tool-codeql, module-registry |

## Requirements

- [Amplifier](https://github.com/microsoft/amplifier) installed
- API keys for your chosen providers (Anthropic, OpenAI, etc.)
- Bundle-specific requirements noted in each bundle's README

## Testing Status

| Bundle | Status | Tools Loaded | Notes |
|--------|--------|--------------|-------|
| researcher | | | |
| designer | | | |
| evaluator | | | |
| full-stack-developer | | | |
| information-worker | | | |
| autonomous-agent | | | |
| voice-interface | | | |
| security-analyst | | | |
| content-creator | | | |
| multi-agent-coordinator | | | |
| local-first | | | |
| project-manager | | | |
| onboarding | | | |
| spec-driven-builder | | | |
| mcp-bridge | | | |

*Testing in progress...*

## Capability Gaps

The ecosystem has strong coverage for:
- AI/agent patterns (memory, strategic advisors, orchestration)
- Collaboration (M365, Slack)
- Code intelligence (LSP)
- Research and evaluation

Known gaps (see [`capability-gaps.yaml`](capability-gaps.yaml) for details):
- Database interaction (SQL, NoSQL)
- Cloud resource management (AWS, Azure, GCP)
- CI/CD pipeline integration
- Container orchestration (Kubernetes)
- Data science/ML workflows

## Contributing

1. Fork this repo
2. Add or improve a bundle
3. Test with `amplifier run --bundle bundles/<name>/bundle.md`
4. Submit PR with test results

## License

MIT - See individual included bundles for their respective licenses.

## Related

- [microsoft/amplifier](https://github.com/microsoft/amplifier) - Core framework
- [microsoft/amplifier-foundation](https://github.com/microsoft/amplifier-foundation) - Foundation library
- [microsoft/amplifier-core](https://github.com/microsoft/amplifier-core) - Kernel
