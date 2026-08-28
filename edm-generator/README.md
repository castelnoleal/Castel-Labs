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
- Waveform-style visualizer
- Real WAV export
- No API key or server required for the current engine
- Responsive mobile/desktop UI

## How it works

The current engine converts the selected genre, BPM, key, mood, energy, tags and description into an arrangement and synthesizes the result in an `OfflineAudioContext`. This makes the application immediately usable from a static GitHub Pages deployment.

The editor is intentionally structured so a future cloud AI music provider can be added as a second engine without replacing the project/version/tag UI.

## Run

Open `index.html` in a modern browser. For GitHub Pages, publish the `edm-generator` directory as a static site.

## Next AI engine integration

The UI already separates musical intent from rendering. A future MusicGen/JASCO-compatible backend can accept the generated musical specification and return rendered audio. This is preferable to putting a model/API secret directly in the browser.
