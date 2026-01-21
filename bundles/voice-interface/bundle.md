---
bundle:
  name: voice-interface
  version: 1.0.0
  description: Voice-first interaction with speech-to-text and real-time voice conversations

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  
  # Voice application
  - bundle: git+https://github.com/robotdad/amplifier-app-voice
  
  # Speech-to-text (local, privacy-first)
  - bundle: git+https://github.com/sadlilas/amplifier-module-tool-stt-whispercpp
  
  # OpenAI Realtime provider
  - bundle: git+https://github.com/robotdad/amplifier-module-provider-openai-realtime
  
  # Whisper transcription
  - bundle: git+https://github.com/robotdad/amplifier-module-tool-whisper
  
  # Audio processing
  - bundle: git+https://github.com/samueljklee/local-audio-segmenter
---

# Voice Interface Bundle

@voice-interface:context/voice-instructions.md

---

## Capabilities

- Speech-to-text input (whisper.cpp - local, private)
- Voice application framework
- OpenAI Realtime API for conversations
- Audio segmentation and processing
- Hands-free operation

## Requirements

- Microphone access
- For local STT: whisper.cpp compiled
- For Realtime: OpenAI API key with Realtime access
