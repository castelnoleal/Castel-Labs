# AI backend adapter

This directory defines the integration boundary for a future neural music renderer.

The browser should never contain private provider credentials. A server endpoint should receive a validated EDM Forge project specification and return a rendered audio asset.

Suggested endpoint:

`POST /api/generate`

```json
{
  "project": { "genre": "Future Bass", "bpm": 150, "key": "F# Minor", "mood": "Euphoric", "energy": 85 },
  "section": "Drop 1",
  "instruction": "#biggerdrop #morebass",
  "mode": "neural"
}
```

Suggested response:

```json
{
  "audioUrl": "/generated/track-section-v2.wav",
  "duration": 8,
  "sampleRate": 32000,
  "section": "Drop 1",
  "engine": "musicgen"
}
```

The browser procedural engine remains the fallback when this endpoint is unavailable.
