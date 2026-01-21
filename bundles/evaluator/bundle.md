---
bundle:
  name: evaluator
  version: 1.0.0
  description: Testing and evaluation toolkit for validating AI systems and ensuring quality

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Evaluation core
  - bundle: git+https://github.com/microsoft/eval-recipes
  - bundle: git+https://github.com/DavidKoleczek/amplifier-module-tool-eval-recipes
  
  # Benchmarking
  - bundle: git+https://github.com/DavidKoleczek/amplifier-app-benchmarks
  
  # Session analysis
  - bundle: git+https://github.com/DavidKoleczek/amplifier-app-session-analyzer
  
  # Smoke testing
  - bundle: git+https://github.com/samueljklee/amplifier-bundle-smoke-test
  
  # Metrics
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-stats
  - bundle: git+https://github.com/marklicata/amplifier-module-tool-iteration-tracker
---

# Evaluator Bundle

@evaluator:context/evaluator-instructions.md

---

## Capabilities

- AI agent benchmarking
- Session analysis and debugging  
- Smoke testing automation
- Multi-trial consistency evaluation
- Performance metrics collection
- Evaluation recipe execution

## Usage

```
"Run benchmark suite against the latest model"
"Analyze the failed session and identify root cause"
"Execute smoke tests for the new bundle"
```
