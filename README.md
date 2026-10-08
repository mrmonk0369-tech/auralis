# Auralis

A single-file language-learning PWA. American English plus Spanish, French, Portuguese, Mandarin and Arabic, with **Sia** (the AI coach), a private in-app content library, a day-by-day path, and real voices.

## What is in this repo

| File | What it is |
|---|---|
| `auralis.html` | The whole app, one self-contained file |
| `index.html` + `sw.js` + `manifest.webmanifest` + icons | The installable PWA build |
| `voice_kit.py` | Free TTS kit (Edge / Kokoro / Piper) for the six languages |
| `generate_audio.py` | Builds a pre-recorded voice pack from the app's own content |

## Running it

Open `auralis.html` directly, or serve the PWA folder over http(s) to get the service worker, offline caching and the install prompt.

## Content

Everything lives inside the app — nothing is fetched from outside.

- Six languages, nine content types each (conversations, golden content, grammar, vocabulary, dialogues, workbook, flashcards, drills, stories)
- **The road to native** — per language: levels and framework, pronunciation, complete A1–C2 grammar, verb conjugation, 450+ words, 80+ phrases, idioms, culture, learner errors and a study plan
- American English volumes 1 and 2, plus the Five-Language Starter Kit

## Voice

The app picks the best voice it can actually use, automatically:

1. a pre-recorded studio clip, if one exists for that line
2. Sia's Gemini voice, if a key is set
3. Google voices, when online
4. Kokoro, on-device
5. the device voice

Failures fall through silently — the learner never sees a voice error.

## Cloud sync

Progress syncs to Supabase (`auralis_progress`, one row per device key, protected by row-level security). The project URL and the publishable key are public client values and are editable in Settings.

## Privacy

No account is required. Progress lives on the device first; the cloud copy is optional and keyed to a random device id.
