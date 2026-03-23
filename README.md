# tg-image-creator

Starter scaffold for a Telegram bot that can do:

- text-to-image via `/imagine <prompt>`
- image edit via photo upload + `/edit <prompt>`
- provider switching (`stability` / `bfl`)
- async provider adapter architecture

## What this starter includes

- `aiogram` bot
- async provider abstraction
- in-memory session store for uploaded images
- local temp-file flow for Telegram image downloads
- starter provider adapters for Stability and Black Forest Labs (BFL)

## Important note about provider APIs

This repo ships with a **clean adapter structure** and request/response parsing stubs that are intended to be finished against the exact provider API docs and model names you choose. Provider APIs evolve, so treat the request builders in `app/providers/*.py` as the implementation starting point rather than a final locked integration.

## Quick start

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python -m app.main
```

## Environment variables

See `.env.example`.

## Telegram flow

1. Send `/start`
2. Send `/imagine cinematic portrait of a Venetian poet in Fiume`
3. Upload a photo
4. Reply with `/edit make it look like a 1920s propaganda poster`

## Next improvements

- Redis session store instead of in-memory storage
- webhook mode with FastAPI
- mask-based edit flow
- inline buttons for redo / aspect ratio / provider switch
- persistent job history
