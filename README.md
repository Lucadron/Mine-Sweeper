<div align="center">

# 💣 Minesweeper — Retro Edition

**Windows 95 aesthetics × Modern web engineering**

React 18 · Web Audio API · Portable HTML

<br>

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![React](https://img.shields.io/badge/React_18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

<br>

[🎮 Play](#installation) · [📸 Screenshots](#screenshots) · [⚙️ Features](#features) · [🏗️ Architecture](#technical-architecture)

<br>

🌐 **[Türkçe README için tıklayın / Read in Turkish](README.TR.md)**

</div>

---

## About

A fully functional recreation of the classic Windows Minesweeper game, written from scratch using modern web technologies. Runs in a single `index.html` file — no server, no build step, no dependency installation required.

## Features

### 🎮 Game Engine
- **First-Click Protection** — The first clicked cell and its 8 neighbors are never mines; mines are placed after the first click
- **BFS Flood Fill** — Queue-based algorithm for opening empty areas with no risk of stack overflow
- **Chording** — Batch-open neighboring cells by clicking (left or middle click) on an already-revealed numbered cell
- **Win/Loss Detection** — Closed cell count = mine count → victory; stepping on a mine → all mines revealed

### 🎛️ Configuration
| Difficulty | Grid | Mines |
|------------|------|-------|
| Beginner | 9×9 | 10 |
| Intermediate | 16×16 | 40 |
| Expert | 30×16 | 99 |
| **Custom** | **9–60 × 9–60** | **1–989** |

### 🎨 Two Themes
- **Neon (Dark)** — Dark blue-purple background, neon-glowing numbers, glow effects
- **Win95 (Gray)** — Classic Windows 95 aesthetic: `inset/outset` 3D borders, blue title bar, `#c0c0c0` background

### 🔊 Sound Effects (Web Audio API)
All sounds are generated procedurally — no external files required:
- Cell open: short, satisfying click + micro bass thump
- Flood fill: ascending cascade melody
- Flag place/remove: metallic click
- **Explosion**: 5-layer cinematic sound — deep bass boom + distorted crunch + white noise shrapnel + sharp crack + delayed echo boom
- Win: C-E-G-C arpeggio fanfare
- Toggle on/off with the 🔊/🔇 button in the top right

### ✨ Game Feel
- Scale + glow effect on hover
- Scale-down press feel on click
- Bounce animation on revealed cells
- Spring animation when planting a flag
- Explosion: screen shake + red flash + particle system
- Win: gold flash + confetti particles

### 📐 Responsive Design
- Grid dynamically fills the entire screen
- Width-first sizing — no side gaps on large grids
- Scroll support when content overflows vertically
- Auto-recalculation on window resize

## Installation

```bash
# Clone the repo
git clone https://github.com/Lucadron/Mine-Sweeper.git

# Open index.html in your browser
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

That's it. No server, no `npm install`, no build.

## Controls

| Action | Control |
|--------|---------|
| Open cell | Left click |
| Place/remove flag | Right click |
| Chording | Left or middle click on a revealed numbered cell |
| New game | Click the 😊 button or the "New Game" button |
| Change theme | 🌙/☀️ button |
| Toggle sound | 🔊/🔇 button |

## Technical Architecture

### Technologies
- **React 18** — via CDN, production build
- **Babel Standalone** — In-browser JSX transpilation
- **Web Audio API** — Procedural sound synthesis
- **CSS Variables** — Theme system

### Performance Optimizations
- Cell memoization with `React.memo` — only changed cells are re-rendered
- Grid calculation and style caching with `useMemo`
- Event handler reference stability with `useCallback`
- Runs smoothly on 60×60 (3600 cell) grids

### Algorithm Complexity
| Operation | Complexity |
|-----------|------------|
| Mine placement | O(W×H) |
| Flood Fill (BFS) | O(W×H) worst case, O(k) average |
| Neighbor counting | O(W×H) |
| Win check | O(W×H) |
| Single click (average) | O(k) where k ≪ N |

### File Structure
```
Mine-Sweeper/
├── index.html    # The entire app — single file, zero dependencies
├── README.md
├── README.TR.md
└── LICENSE
```

## License

MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with 💣 by **Lucadron**

</div>
