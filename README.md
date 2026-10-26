# GIMME_CONFIDENCE // Sarvam AI Viva Telemetry

# INSTRUCTIONS
1. edit the .env file with your API key
2. run `pip install -r requirements.txt`
3. run `python main.py`
4. open the generated localhost link through the terminal.

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
