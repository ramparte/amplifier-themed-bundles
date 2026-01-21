---
bundle:
  name: local-first
  version: 1.0.0
  description: Run Amplifier entirely locally with no cloud dependencies - privacy-first AI

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Local LLM provider (Foundry Local)
  - bundle: git+https://github.com/samueljklee/amplifier-module-provider-foundry-local
  
  # Local storage
  - bundle: git+https://github.com/sadlilas/amplifier-module-storage-localfirst
  
  # Local speech-to-text
  - bundle: git+https://github.com/sadlilas/amplifier-module-tool-stt-whispercpp
  
  # Context management
  - bundle: git+https://github.com/sadlilas/amplifier-module-util-context
  - bundle: git+https://github.com/microsoft/amplifier-module-context-simple
---

# Local-First Privacy Bundle

@local-first:context/local-instructions.md

---

## Capabilities

- Local LLM inference (Foundry Local / Ollama)
- SQLite-based local storage
- Local speech-to-text (whisper.cpp)
- No external API dependencies
- Hardware-optimized performance

## Requirements

- Foundry Local installed, OR Ollama
- Sufficient RAM (8GB+ recommended)
- For STT: whisper.cpp compiled with models

## Privacy Guarantee

All processing stays on your machine. No data leaves your network.
