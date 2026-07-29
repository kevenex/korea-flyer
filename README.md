# korea-flyer

A stylized first-person flight over a low-poly South Korea, built as a single self-contained HTML file with Three.js (loaded from a CDN).

Open `index.html` in a modern browser — no build tools, no assets, no server required.

**Live version:** https://kevenex.github.io/korea-flyer/ (deployed automatically from `main` via GitHub Actions)

## Controls
- **W / S** — throttle up / down
- **A / D** or **← / →** — steer (banks on turns)
- **↑ / ↓** — pitch up / down
- **Click** the canvas — optional mouse look (pointer lock)
- **Fly to** buttons (bottom-left) — smoothly animate to a city, framed to show its landmarks

## What you can find

| Place | Landmarks |
|---|---|
| Seoul | N Seoul Tower on Namsan, Lotte World Tower, 63 Building, Gyeongbokgung, the Han River |
| Incheon | Incheon International Airport on its own island, Incheon Bridge |
| Busan | Gwangan Bridge, Busan Tower on Yongdusan, the container port, Haeundae towers |
| Gyeongju | Bulguksa temple, the Daereungwon royal tomb mounds |
| Jeju | Hallasan with its summit crater, Seongsan Ilchulbong |
| Daejeon / Daegu / Gwangju | Hanbit Tower, 83 Tower, a traditional pavilion |

## How the scale works

Geography is at **true scale**. City positions and the coastline are real kilometre
offsets from Seoul (derived from latitude/longitude), so the country has correct
proportions — roughly 300 km east–west by 460 km north–south. One world unit is
100 m.

Heights are deliberately exaggerated, because at 1:1 a 555 m tower is invisible
next to a 450 km country. Each exaggeration is a separate constant at the top of
the file, and helper functions convert real metres into world units — so every
landmark is written with its actual real-world dimensions:

| Constant | Applies to |
|---|---|
| `KM` | world units per kilometre (horizontal, true scale) |
| `VEX` | terrain height (mountains) |
| `SVEX` | structure height (towers, buildings) |
| `SHEX` | chunky structure widths (decks, terminals) |
| `mast()` | very slender masts, which would be hairlines at true scale |
| `HVEX` / `HHEX` | heritage sites, boosted so they read from the air |

City layouts, runway lengths and bridge spans all use `tw()` — true horizontal
scale — so a city covers the ground it really covers.

## Tweaking

Everything worth adjusting sits near the top of `index.html`:

- `CONFIG` — speeds, fog distances, fly-to framing
- `CITIES` — city positions in kilometres, urban radius, base elevation
- `COAST` — the coastline polygon, used for both terrain and the minimap
- `TAEBAEK` / `SOBAEK` — mountain range spines the terrain rises along
- `FLY` — per-city approach bearing, distance and altitude
- `colorForHeight` — the terrain palette, keyed by real elevation in metres

## Performance

The scene renders in ~130 draw calls and ~280k triangles. Each city's blocks are
merged into a single geometry, and the ~14,000 trees are one instanced mesh.
