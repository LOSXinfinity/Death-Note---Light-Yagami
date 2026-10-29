# Death Note — 新世界の神

An immersive, scroll-driven tribute to *Death Note* built with vanilla HTML, CSS, and JavaScript. No frameworks, no build step — just a single `index.html` that loads frame sequences and renders cinematic chapters as you scroll.

## Experience

| Chapter | Title | Interaction |
|---------|-------|-------------|
| **01** | **嘲笑** — *Kira Laughs* | 35-frame sequence synced to scroll; ember particles rise; "計画通り" flashes at the climax |
| **02** | **監視** — *Surveillance* | Shinigami eyes track your cursor horizontally across 40 measured pupil positions |
| **03** | **ノートの掟** — *Rules* | Notebook pages turn on scroll; 5 Death Note rules reveal vertically in Japanese & English |
| **04** | **闇の中** — *Darkness* | Move the cursor to burn away fog and reveal Ryuk's throne; ghost cursor trail with soft falloff |

## Quick Start

```bash
# Serve locally (required for asset loading)
npx serve .
# or
python -m http.server 8000
```

Open `http://localhost:3000` (or 8000) in a desktop browser. Mobile works but the experience is designed for mouse/pointer interaction.

## Project Structure

```
Death Note Light Yagami/
├── index.html          # Entire app — markup, styles, logic
└── assets/             # Frame sequences (loaded at runtime)
    ├── laugh/          # 35 frames — Kira laughing
    ├── justice/        # 70 frames — Eyes sweeping left→right
    └── note/           # 70 frames — Notebook pages turning
```

> **Note:** The `assets/` folder is not included in this repo. You'll need to provide your own frame sequences named `001.jpg`–`035.jpg` (laugh), `001.jpg`–`070.jpg` (justice), `001.jpg`–`070.jpg` (note), plus `assets/throne.jpg` for the final chapter background.

## Tech Highlights

- **Scroll-linked pinning** — CSS `position: sticky` + JS progress mapping
- **Frame sequences** — Preloaded `Image` objects drawn to `<canvas>` with `drawImage` cover logic
- **Cursor-reactive shaders** — Eyes map cursor X to measured pupil positions; darkness chapter uses `globalCompositeOperation: "destination-out"` for realtime fog reveal
- **Particle system** — Ember spawning scales with scroll progress
- **Reduced-motion safe** — Respects `prefers-reduced-motion`
- **Japanese typography** — `Yuji Syuku`, `Shippori Mincho B1`, `Dela Gothic One`, `Zen Kaku Gothic New` via Google Fonts

## Customization

- Edit frame counts in `data-count` attributes on `[data-frames]` sections
- Swap frame folders by changing `data-frames` values
- Adjust scroll ranges in `map(p, start, end)` calls inside each render function
- Colors, fonts, and timing live in the `:root` CSS variables

## License

Fan tribute — not affiliated with Shueisha, Madhouse, or the *Death Note* IP holders. Assets not included.