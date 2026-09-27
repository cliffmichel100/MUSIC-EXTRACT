# akosibiko — Music Stem Separator

A GitHub-ready static frontend for an online music stem separation tool.

## What it does

- Upload/drop an audio file
- Select 2-stem or 4-stem separation
- Shows a polished progress UI
- Displays vocal, drum, bass, instrumental/other stem cards
- Responsive/mobile-friendly
- No build system required
- Works with GitHub Pages

## Important

GitHub Pages can host the frontend, but it does **not** run an AI audio-separation model.

The current `script.js` contains a demo separation flow. For real separation, connect the upload action to a backend that runs a model such as Demucs or another properly licensed source-separation system.

Typical architecture:

Browser → `/api/separate` → audio-separation server → generated WAV stems → browser downloads

Do not upload copyrighted music unless you have the rights or permission to process it.

## GitHub Pages

1. Create a GitHub repository.
2. Upload `index.html`, `style.css`, and `script.js`.
3. In **Settings → Pages**, choose deployment from the `main` branch and `/root`.
4. Open the generated GitHub Pages URL.

## Suggested backend API

`POST /api/separate`

Form field:
- `file`: uploaded audio

Response:
```json
{
  "vocals": "/results/vocals.wav",
  "drums": "/results/drums.wav",
  "bass": "/results/bass.wav",
  "other": "/results/other.wav"
}
```

Replace the demo loop in `script.js` with a `fetch()` request to that endpoint.
