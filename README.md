# GIMME_CONFIDENCE // Sarvam AI Viva Telemetry

**The Code-Mixed Viva & Disfluency Coach** — Built for the Sarvam AI Buildathon

Technical students in India often think in a mix of native languages and English jargon, causing heavy speech disfluency during vivas and interviews. GIMME_CONFIDENCE diagnoses this in real-time using Sarvam AI's multi-model pipeline.

## What It Does

1. **Context Ingestion** — Upload a technical PDF or pick a demo topic. The app extracts context and generates a grilling viva question (spoken aloud via Sarvam TTS).
2. **Dual-Mode Disfluency Diagnostics** — Record your spoken answer. Sarvam Saaras STT processes it in parallel across `formal`, `codemix`, and `translate` modes.
3. **Algorithmic Diffing + Technical Grilling** — A custom diffing engine tags fillers (umm, matlab, basically…), computes Fluency Score, WPM, and Code-Mix Ratio. Sarvam's LLM evaluates technical accuracy and generates an ideal answer + follow-up question.
4. **Mirror-Me Voice Coach** — Hear the ideal answer in Crisp English, Colloquial Hinglish, and Roman Karaoke script via Sarvam TTS.

## Sarvam AI APIs Used

| API | Model | Purpose |
|-----|-------|---------|
| Speech-to-Text | Saaras v2 | Multi-mode transcription (formal, codemix, translate) |
| Chat Completions | Sarvam-M / 105B | Technical evaluation + ideal answer generation |
| Translation | Mayura v1 | English → Hinglish (modern-colloquial) |
| Transliteration | — | Native script → Roman karaoke |
| Text-to-Speech | Bulbul v2 | Viva questions + ideal answer audio |

## Quick Start

```bash
# 1. Clone and enter the project
cd GIMME_CONFIDENCE

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set your Sarvam API key
cp .env.example .env
# Edit .env and add your key from https://dashboard.sarvam.ai

# 4. Run
uvicorn main:app --reload
```

Open http://localhost:8000 in your browser.

## Project Structure

```
├── .env.example          # Environment template
├── requirements.txt      # Python dependencies
├── main.py               # FastAPI app, routes, async orchestration
├── services/
│   ├── sarvam_client.py  # Async httpx wrapper for all Sarvam APIs
│   ├── disfluency_engine.py  # Token diffing, filler detection, fluency scoring
│   └── pdf_service.py    # PDF extraction + built-in demo presets
└── static/
    ├── index.html        # Single-page studio UI (Tailwind + Alpine.js)
    └── app.js            # WebAudio WAV recorder + API state management
```

## Demo Presets (No PDF needed)

- **Systems & DB**: Async Connection Pooling & Lock Contention in PostgreSQL
- **Deep Learning**: Transformer Attention Mechanisms & KV-Cache Memory Bottlenecks
- **Operating Systems**: Linux Kernel Modules, Page Tables & Interrupt Handling

## Browser Requirements

- Chrome/Edge 80+ (WebAudio API + MediaRecorder)
- Microphone permission required for voice recording
- Text input fallback available if mic is unavailable

## License

MIT
