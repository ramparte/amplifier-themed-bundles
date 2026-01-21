# Voice Interface Instructions

This bundle enables voice-first interaction with Amplifier, supporting both local speech-to-text and real-time conversational AI.

---

## Voice Workflows

### Local Speech-to-Text (whisper.cpp)

For privacy-conscious, offline transcription:

1. **Recording**: Capture audio from microphone
2. **Processing**: whisper.cpp transcribes locally (no data leaves your machine)
3. **Input**: Transcribed text becomes your prompt

Best for:
- Sensitive or confidential work
- Offline environments
- Lower latency requirements
- Privacy-first users

### OpenAI Realtime Conversations

For natural, bidirectional voice conversations:

1. **Connection**: Establishes WebSocket to OpenAI Realtime API
2. **Streaming**: Audio streams both directions in real-time
3. **Interaction**: Natural conversational flow with interruption support

Best for:
- Extended voice sessions
- Natural dialogue
- When internet connectivity is available
- Complex multi-turn conversations

### Audio Segmentation

The local-audio-segmenter handles:
- Voice activity detection (VAD)
- Splitting long recordings into segments
- Silence removal for cleaner transcription
- Optimal chunk sizing for model input

---

## STT Options Comparison

| Feature | whisper.cpp (Local) | OpenAI Realtime |
|---------|---------------------|-----------------|
| Privacy | Full (offline) | Cloud-based |
| Latency | Low | Very low |
| Quality | Excellent | Excellent |
| Cost | Free (compute only) | API charges |
| Languages | 99+ supported | 99+ supported |
| Offline | Yes | No |

---

## Accessibility Considerations

### For Users with Motor Impairments

- Voice input eliminates keyboard dependency
- Hands-free operation for extended coding sessions
- Combine with voice commands for navigation

### For Users with Visual Impairments

- Pair with TTS output for full audio interaction
- Reduces reliance on screen reading software
- Natural conversation flow

### Best Practices

1. **Clear enunciation** improves transcription accuracy
2. **Quiet environment** reduces noise interference
3. **Pause between commands** helps segment recognition
4. **Use wake words** if supported, to prevent accidental activation

---

## Setup Guide

### whisper.cpp Local STT

```bash
# Clone and build whisper.cpp
git clone https://github.com/ggerganov/whisper.cpp
cd whisper.cpp
make

# Download a model (base is good balance of speed/accuracy)
./models/download-ggml-model.sh base.en
```

### OpenAI Realtime

1. Obtain API key with Realtime access from OpenAI
2. Set environment variable: `OPENAI_API_KEY=sk-...`
3. Ensure microphone permissions are granted

---

## Voice Command Patterns

When using voice input, structure commands clearly:

- **File operations**: "Create a new file called utils.py in the src folder"
- **Code changes**: "Add error handling to the parse function"
- **Navigation**: "Show me the test files"
- **Questions**: "Explain how this authentication module works"

Avoid:
- Mumbling or trailing off
- Multiple unrelated requests in one utterance
- Speaking while Amplifier is responding (unless using interruption-enabled Realtime)

---

## Troubleshooting

### Low Transcription Accuracy

- Check microphone input levels
- Reduce background noise
- Try a larger whisper model (small, medium)
- Speak closer to microphone

### High Latency

- Use smaller whisper model for local STT
- Check network connection for Realtime
- Ensure adequate CPU/GPU resources

### Microphone Not Detected

- Verify system permissions
- Check audio device settings
- Restart audio service if needed
