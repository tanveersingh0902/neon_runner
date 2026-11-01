# Neon Cyber Runner

A polished, single-file browser arcade game built with HTML, CSS, vanilla JavaScript, and the Canvas API. Pilot a neon runner through a falling barrage, survive as long as possible, and beat your local best score.

## Play

Open [`index.html`](index.html) in a modern desktop browser, then select **Start Game** (or press <kbd>Enter</kbd>). No installation, build step, server, or package manager is required.

For the most reliable experience, use a current version of Chrome, Edge, Firefox, or Safari. The game loads its display fonts from Google Fonts when online and falls back to system fonts when they are unavailable.

## Controls

| Action | Keyboard |
| --- | --- |
| Move left | <kbd>←</kbd> or <kbd>A</kbd> |
| Move right | <kbd>→</kbd> or <kbd>D</kbd> |
| Jump | <kbd>Space</kbd>, <kbd>↑</kbd>, or <kbd>W</kbd> |
| Start / restart | <kbd>Enter</kbd> |
| Toggle FPS display | <kbd>F</kbd> |
| Mute / unmute | Use the **Sound On/Off** button |

## Features

- Fast Canvas-based gameplay with smooth, frame-rate-independent movement.
- Neon player, animated grid backdrop, and three randomized obstacle styles.
- Jump physics and horizontal boundary protection.
- Obstacle spawning, movement, removal, and rectangular collision detection.
- Survival-based score that increases at 3 points per second.
- Progressive difficulty: obstacles accelerate and appear more frequently over a 90-second ramp, within playability limits.
- Ready, playing, and game-over states with clean restart behavior.
- Persistent best score stored locally in the browser.
- Optional Web Audio API sound effects generated in the browser—no audio files required.
- Responsive layout, keyboard-friendly controls, and a switchable FPS counter for debugging.

## How it works

Everything lives in `index.html`:

| Area | Responsibility |
| --- | --- |
| HTML | Game HUD, canvas, controls, and accessible labels |
| CSS | Responsive futuristic interface, neon effects, and button states |
| JavaScript | Input, game loop, physics, obstacles, rendering, scoring, sound, and storage |

The animation loop uses `requestAnimationFrame`. Each frame updates the active game state using elapsed time, then redraws the canvas. That elapsed-time approach keeps movement and scoring consistent across different display refresh rates.

## Scoring and difficulty

Your score is `floor(seconds survived × 3)`. The game stores the highest completed score under the browser local-storage key `neonRunner_highScore`, so it remains after refreshing or restarting the browser. Clearing site data resets it.

Obstacle speed ramps from roughly 180 to 420 pixels per second and the spawn interval decreases from 1.20 to 0.55 seconds as a run progresses. Up to five obstacles may be active at once.

## Project structure

```text
neon_runner/
├── index.html    # Complete game application
├── README.md     # Project documentation
└── prompts.txt   # Workshop prompts used to develop the game
```

## Manual smoke test

1. Open `index.html` and confirm the start screen, score HUD, and controls are visible.
2. Start a run and hold both left/right movement keys; the runner should stay inside the canvas.
3. Jump with Space, Up, or W; the runner should land cleanly before it can jump again.
4. Let an obstacle hit the runner; the game should freeze, show the final score, and expose **Restart**.
5. Restart and confirm the score, player position, obstacles, and difficulty reset.
6. Beat the displayed best score, end the run, then refresh the page; the new best score should remain.
7. Use the sound button after interacting with the page to verify muting and unmuting.

## Development notes

This project intentionally has no framework or backend. It is suitable for learning the basics of a browser game: input state, delta-time movement, Canvas drawing, collision detection, game-state management, local storage, and Web Audio.

## License

No license has been specified for this project. Add one before distributing or reusing it publicly.
