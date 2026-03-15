# Portfolio Game 🎮
[LIVE HERE](https://plutocrate.github.io/portfolio)

A 2D side-scrolling portfolio website built with React, WebGL, and Canvas 2D.

## Tech Stack
- **React 18** — UI and component tree
- **Vite** — lightning-fast dev server and bundler
- **Canvas 2D** — sprite animation engine
- **WebGL (raw)** — forest glow effect in entry scene
- **Tailwind CSS** — utility styling for UI elements
- **Custom shadcn-style** — dialog and HUD components

## Quick Start

```bash
npm install
npm run dev
```

Then open http://localhost:5173

## Project Structure

```
src/
├── App.jsx                    # Scene orchestrator
├── main.jsx
├── index.css
│
├── scenes/
│   ├── EntryScene.jsx         # Black room + forest glow (first room)
│   ├── ModeSelectScene.jsx    # Terminal in the middle to pick mode
│   ├── AboutScene.jsx         # About me room (normal mode)
│   ├── ProjectsScene.jsx      # Projects room
│   ├── ContactScene.jsx       # Contact room (final)
│   └── ResumeScene.jsx        # Full-page resume (resume mode)
│
├── components/
│   ├── game/
│   │   ├── ForestGlow.jsx     # WebGL forest light shader
│   │   ├── PlayerSprite.jsx   # Animated sprite (Canvas 2D)
│   │   └── SceneTransition.jsx # Black fade between rooms
│   ├── hud/
│   │   └── GameHUD.jsx        # Controls display
│   └── ui/
│       └── ModeSelectDialog.jsx # Mode picker overlay
│
├── hooks/
│   ├── useGameState.jsx       # Global game state (React Context)
│   └── useKeyboard.js         # QWERTY-localized input
│
└── utils/
    ├── constants.js           # Game config values
    ├── keyboard.js            # Physical key → action mapping
    └── audio.js               # Audio manager
```

## Controls

| Key | Action |
|-----|--------|
| A / ← | Move left |
| D / → | Move right |
| E / Enter | Interact |
| Escape | Pause (future) |

All controls use `event.code` (physical key position) so they work
on any keyboard layout (AZERTY, Dvorak, etc.) as QWERTY.

## Customizing Your Resume

Edit `src/scenes/ResumeScene.jsx` — change the `RESUME_DATA` object at the top
with your actual name, experience, projects, etc.

## Adding More Rooms

1. Create a new scene in `src/scenes/`
2. Add a new scene constant to `src/utils/constants.js`
3. Import and render it in `src/App.jsx`
4. In the previous scene, dispatch `SET_SCENE` when player reaches the right edge

## Assets

Place your assets in `public/assets/`:
- `sprites/` — Run_0000.png through Run_0013.png (14 frames, 240×240 px)
- `tiles/` — TileSet.png
- `audio/` — Grass_Running.wav

## Extending

- **Tiles**: To make floor tiles visible, uncomment the tile rendering layer in each scene and use the TileSet.png (the full tileset is 840×840, the content starts at col 130, row 116).
- **Music**: Add a background track with `audioManager.load('music', '/assets/audio/bg.mp3')`.
- **Pixi.js**: The package.json includes pixi.js if you want to migrate the sprite/tile rendering to Pixi for more advanced effects.
# testportfolio
