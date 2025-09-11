# PingPong Game

A minimal HTML5 canvas Ping Pong game that runs in any modern browser and scales to phones, tablets, laptops, and desktops.

### Features
- Responsive full-viewport canvas (auto-resizes on window/orientation changes)
- Touch controls on mobile (drag to move the left paddle)
- Mouse controls on desktop (move mouse to control the left paddle)
- Simple AI for the right paddle
- Score display and classic dotted net
- 60 FPS game loop

### Quick Start
- Double-click `index.html` to open it in your browser; or
- Serve locally (recommended for consistent sizing and input):

```bash
# Python 3
python -m http.server 8080
# then visit: http://localhost:8080
```

```bash
# Node.js
npx serve -l 8080
# then visit: http://localhost:8080
```

### Controls
- Desktop: Move your mouse up/down anywhere over the canvas to control the left paddle.
- Mobile/Touch: Drag your finger up/down anywhere on the screen to control the left paddle.

The computer controls the right paddle. A point is scored when the ball passes a paddle.

### Project Structure
```
GAME 1/
  index.html   # Page markup and canvas element
  style.css    # Fullscreen layout and touch behavior
  main.js      # Game logic, rendering, input, and resizing
```

### How it Works (brief)
- The canvas matches the window size and updates on `resize`/`orientationchange`.
- Mouse and touch events update the user paddle; default gestures on the canvas are disabled for smooth control.
- The ball bounces off top/bottom walls and its angle changes based on where it hits a paddle.
- Scores are drawn to the canvas; the right paddle follows the ball with smoothing.

### Customize Gameplay
Tweak these constants near the top of `main.js`:
```js
const paddleWidth = 18,
      paddleHeight = 120,
      paddleSpeed = 8,
      ballRadius = 12,
      initialBallSpeed = 16,
      maxBallSpeed = 50;
```
Adjust the AI follow factor inside `update()` (lower = easier, higher = harder):
```js
com.y += (ball.y - (com.y + com.height / 2)) * 0.1;
```

### Notes
- The page disables scroll/zoom gestures on the canvas to avoid accidental page movements while playing.
- If the canvas does not fully fit on mobile after rotating, reload the page so it re-measures the viewport.
