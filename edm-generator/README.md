# EDM Forge

A mobile-friendly EDM music generator/editor that runs as a static web app.

## Current working features

- 12 EDM genre presets
- BPM, key, mood and energy controls
- Natural-language song direction
- Quick musical tags such as `#biggerdrop`, `#morebass`, `#darker`, `#hardkick`, `#distortedbass` and `#wider`
- Section targeting: Intro, Build, Drop 1, Breakdown and Drop 2
- Iterative improvement and version history
- Browser-side procedural audio generation using Web Audio API
- Real-time playback controls
- Waveform visualizer
- Real WAV export
- No API key or server required for the current engine
- Responsive mobile/desktop UI

## Architecture

The project separates musical intent from rendering. Project state contains genre, BPM, key, mood, energy, description, tags, selected section and version history. This lets a future neural music backend replace or augment the procedural renderer without redesigning the editor.

The browser renderer is the immediate fallback and works without a server. Web Audio provides direct access to audio buffers and scheduling controls.

## AI engine roadmap

A neural provider should be implemented as a server-side adapter rather than exposing model/API secrets in the browser. Meta's AudioCraft MusicGen is one viable research/reference implementation. Its official documentation supports text-to-music and text+melody generation and documents multiple model variants; the medium model is intended for GPU-backed inference, so it should remain an optional server-side engine rather than a browser dependency.

Recommended provider contract:

`POST /api/generate`

Input: project musical specification + selected section + modification instructions.

Output: audio asset URL/bytes + duration + sample rate + provider metadata.

The browser keeps project/version state and uses the provider only for rendering. Section regeneration sends only the selected section's intent while retaining the global project DNA.

## Run

Open `index.html` in a modern browser. For GitHub Pages, publish the `edm-generator` directory as a static site.

## Future upgrades

1. Server-side neural provider adapter.
2. Persistent project save/load.
3. True section-level audio replacement and crossfading.
4. Stems/MIDI export.
5. Waveform selection and trim controls.
6. Complete project-state undo/redo snapshots.
7. Optional user-provided reference audio for supported style/melody conditioning.
