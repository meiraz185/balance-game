# BALANCE! – Build Until It Falls

A click-only 2D physics stacking game. Pick a block from the tabletop, click where to drop it, and keep your tower standing.

## Play locally
Open `index.html` in any modern browser (an internet connection is needed for Matter.js and Google Fonts).

## Deploy to GitHub Pages
1. Create a new repository and upload `index.html` (and this README) to the root.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then **Save**.
4. After a minute the game is live at `https://<your-username>.github.io/<repo-name>/`.

## Controls
- Click / tap a block on the tabletop to pick it (click again to put it back).
- Click / tap in the building area to drop it at that horizontal position.
- **Turn** button, right-click or `R` rotates the picked block 90°.
- `M` toggles sound, `Esc` drops the selection.

## Tech
- Single file: HTML, CSS and vanilla JavaScript drawing to HTML5 Canvas.
- Physics: [Matter.js 0.19.0](https://brm.io/matter-js/) via cdnjs, fixed 120 Hz step in one `requestAnimationFrame` loop.
- Sound: synthesized with the Web Audio API (no audio files).
- 25 blocks across 22 shapes, including compound L- and T-blocks.

## Rules (v4)
- **Build anywhere on the platform.** Every block can go anywhere on the brown wooden platform or on top of other blocks: one tall tower, several structures side by side, or bridges between them. Slight overhangs are fine if the block stays balanced. The preview turns red only where the block would miss the platform and fall to the floor; clicking there shows "Build on the platform!".
- **One fall = game over.** If any placed block touches the floor or drops below the table top, the loss registers at once, placing stops, the fall plays for about 1.7 s and "OOPS! IT FELL!" appears by itself.
- **Win** ("AMAZING BALANCE!") by placing all 25 blocks with none falling, then holding for 5 s while "Hold your balance…" counts down. A fall during the countdown is a loss.
- Game states: PLAYING → LOSING → GAME_OVER, and PLAYING → VICTORY_COUNTDOWN → WIN. Loss always takes priority.
- The **STABLE / WOBBLING / DANGER** pill reads the tower's live velocity and spin; DANGER also lights when a block is slipping over the table edge.
- Your best height is saved in the browser (localStorage) across attempts.
- Resting blocks "sleep" (a Matter.js feature) so a settled tower stays put instead of slowly creeping; any contact or movement wakes them.
