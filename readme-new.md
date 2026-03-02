# live-translate

**Real-time translation from your Mac microphone. Zero gaps.**

https://github.com/mordechaipotash/live-translate/raw/main/assets/demo.mp4

---

Most live translation tools pause recording while they transcribe. You miss words. You miss sentences.

This one records chunk N+1 **while processing chunk N**. Continuous audio capture. Zero gaps.

Used at a live tech meetup. 188 lines of bash.

---

## Install

```bash
git clone https://github.com/mordechaipotash/live-translate
cd live-translate
chmod +x translate.sh
```

## Run

```bash
./translate.sh
```

```
🎤 Hebrew → English Live Translation
Chunk: 30s | Parallel record/process
────────────────────────────────────

🇮🇱 אז מה שאנחנו עושים פה זה בעצם לוקחים את כל ה-API
🇬🇧 So what we're doing here is taking this entire API

🇮🇱 והדבר המגניב הוא שזה רץ לוקאלי, אין צורך בשום שרת ענן
🇬🇧 And the cool thing is that this runs locally, no cloud server needed
```

---

## How It Works

```
🎤 Microphone
    ↓ sox/rec (30s chunks)
📄 WAV File
    ↓ Whisper (local STT)
🇮🇱 Hebrew Text
    ↓ Gemini Flash (translate)
🇬🇧 English Text
    ↓ terminal + JSON log
```

The key: records chunk N+1 in the background while processing chunk N. No pause. No gap.

---

## Configuration

```bash
# Language pair (default: Hebrew → English)
SOURCE_LANG="Hebrew"
TARGET_LANG="English"

# Chunk duration (default: 30s)
CHUNK_SECONDS=30

# Translation model
MODEL="google/gemini-2.5-flash-lite"
```

Works with any language pair Gemini supports.

---

## Dependencies

- `sox` (recording)
- `whisper` or `parakeet-mlx` (transcription)
- OpenRouter API key (translation)

---

## Part of the ecosystem

[brain-mcp](https://github.com/mordechaipotash/brain-mcp) · [local-voice-ai](https://github.com/mordechaipotash/local-voice-ai) · [mordenews](https://github.com/mordechaipotash/mordenews) · [x-search](https://github.com/mordechaipotash/x-search)

## License

MIT
