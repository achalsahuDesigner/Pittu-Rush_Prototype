# Pittu Rush

A 3D browser take on **Pittu** (also called Lagori, Pithoo, Sat Patthar), the Indian
street game. Smash the stack of slabs, then rebuild it in order while the gully kids
hunt you with the ball. Or switch sides and defend the stack yourself.

**Play it:** <add your live link here>

No install, no build step. The whole game is one `index.html` file.

## Running it locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

## Controls

**Builders (attack)**
- Tap / click / `Space` to stop the swinging aim line, then again to stop the power bar
- `WASD` or arrow keys to move, or drag anywhere on the left of the screen on mobile
- `Space` or `Shift` to dash, or the DASH button
- `Esc` or `P` to pause

**Fielders (defend)**
- Drag to aim, release to throw
- Release on a teammate, or press `1`–`3`, to pass
- You cannot move while holding the ball

## Built with

Three.js and cannon.js from a CDN, plain HTML/CSS/JS, no framework and no bundler.
