# korea-flyer

A stylized first-person flight over a low-poly Korean peninsula, built with a single self-contained HTML file and Three.js (loaded from a CDN).

Open `index.html` in a modern browser — no build tools, no assets, no server required.

**Live version:** https://kevenex.github.io/korea-flyer/ (deployed automatically from `main` via GitHub Actions)

## Controls
- **W / S** — throttle up / down
- **A / D** or **← / →** — steer (banks on turns)
- **↑ / ↓** — pitch up / down
- **Click** the canvas — optional mouse look (pointer lock)
- **Fly to** buttons (bottom-left) — smoothly animate to a landmark

## Tweaking
All tunables live near the top of `index.html`:
- `CONFIG` — speeds, altitudes, fog, mountain amplitude
- `CITIES` — landmark positions (edit `x` / `z`)
- `PENINSULA` — the outline polygon used for terrain shaping and the minimap
