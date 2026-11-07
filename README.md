# Pittu Rush

A 3D browser take on **Pittu** (also called Lagori, Pithoo, Sat Patthar), the Indian
street game. Smash the stack of slabs, then rebuild it in order while the gully kids
hunt you with the ball. Or switch sides and defend the stack yourself.

**Play it:** https://achalsahudesigner.github.io/Pittu-Rush_Prototype/
(turn on GitHub Pages first: Settings → Pages → Deploy from a branch → `main`, `/ (root)`)

No install, no build step. The whole game is one `index.html` file.

## Modes

- **Solo:** Daily Gully (same street for everyone that day) and Free Play, against bots,
  as Builders or Fielders. Works offline once loaded.
- **Online (beta), up to 8 players, 4 v 4:** one player creates a room and shares the
  5-letter code or the invite link. Friends join from any browser. Empty seats are played by bots.
  - Teams swap every round: one team smashes and rebuilds, the other fields.
  - The first team to win 3 rounds wins the match, followed by a scoreboard and a rematch.
  - Fielders move freely, but once you hold the ball you are rooted until you throw or pass.

## How online works

It is peer-to-peer, so there is no game server and no account. The host's browser runs the
real match (the same simulation as solo, with humans plugged into characters). Everyone
else sends their inputs and draws 20 snapshots a second. Players find each other through
public Nostr relays, using [Trystero](https://github.com/dmotz/trystero) bundled inline,
and then talk over WebRTC.

Things to know:
- **The host's tab has to stay open and in front.** Browsers pause background tabs, and
  the match pauses with it.
- **Some networks block direct connections**, such as strict office Wi-Fi or some mobile
  data. Fixing that properly needs a TURN relay server, which is not set up yet.
- **There is no client-side prediction yet**, so guests feel their own ping when they move.

To test online play on one computer, open the game in two tabs with `?net=local` added
to the URL. Tabs then talk over a BroadcastChannel instead of the internet.

## Running it locally

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

## Controls

**Builders (attack)**
- Tap, click or `Space` to stop the swinging aim line, then again to stop the power bar
  (online, one player throws for the team)
- `WASD` or arrow keys to move, or drag anywhere on the left of the screen on mobile
- `Space` or `Shift` to dash, or use the DASH button
- `Esc` or `P` to pause, or to open the match menu online

**Fielders (defend)**
- Online: `WASD`, arrow keys or the left thumb to move, and walk over a loose ball to pick it up
- Drag to aim, release to throw
- Release on a teammate, or press `1`–`4`, to pass
- You cannot move while holding the ball

## Built with

Three.js and cannon.js from a CDN, plus Trystero for online rooms (inlined). Plain
HTML, CSS and JS, with no framework and no bundler.
