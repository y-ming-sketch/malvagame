# Neon Meteor Dash

A single-file HTML5 canvas arcade game. Pilot a glowing futuristic ship through a hostile meteor field, dodge lasers and energy mines, collect energy orbs, and survive as long as possible.

No build step. No dependencies. No external images, fonts, or audio files. Everything &mdash; ship, meteors, particles, UI, hearts &mdash; is drawn with code.

## Play it

Open `index.html` directly in any modern browser (Chrome, Firefox, Safari, Edge).

That is the entire setup.

```bash
# from the repo root
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

## Controls

| Action | Input |
| --- | --- |
| Move | `W` `A` `S` `D` or arrow keys |
| Move (alt) | Mouse &mdash; ship glides toward cursor |
| Start / restart | `Space`, `Enter`, or click the button |

Keyboard and mouse are both live at the same time &mdash; whichever you touched last is the active input.

## Gameplay

- **3 hearts.** Each hit costs one. Lose all three and the run ends.
- **Brief invulnerability** after every hit so you can recover.
- **Difficulty scales with time.** Meteors spawn faster and travel faster the longer you survive. Lasers join the mix after ~8 seconds. Energy mines after ~18 seconds.
- **Score sources**:
  - Energy orbs (green, glowing) &mdash; +10 each, with a slight magnet pull.
  - Survival time, displayed live in the HUD.
- **High score** is saved to `localStorage` under the key `nmd-high` and persists between sessions.

## Hazards

| Hazard | Behaviour |
| --- | --- |
| **Meteors** | Jagged rotating asteroids drifting in from the right. Bounce off the top and bottom edges. Fast, frequent, do 1 damage. |
| **Lasers** | Horizontal beams. Show a blinking pink warning line for ~1 second, then fire a thick neon beam across the entire screen for ~0.3s. |
| **Energy mines** | Pulsing purple rings that drift in slowly. Touch them and they explode &mdash; bigger screen shake, bigger particle burst. |

## Visuals

- 3-layer parallax star field with twinkle
- Drifting nebula radial gradients
- Multi-color thrust plume behind the ship
- Expanding shockwave rings on explosions
- Screen shake on damage, brief slow-mo + red flash on hit
- Mint flash on orb pickup
- Vignette + scanline overlay on menus
- Animated start screen (pulsing neon title, shimmer button)
- Game over screen with stats panel and `NEW RECORD` callout
- Live HUD: score (left), survival timer (center), high score (right), 3 hearts + threat meter

## Tech

- Plain HTML, CSS, JavaScript in one file
- HTML5 `<canvas>` 2D context
- Device-pixel-ratio aware rendering for crisp visuals on high-DPI screens
- All visuals procedural; uses `ctx.shadowBlur`, additive blending (`globalCompositeOperation = 'lighter'`), and radial gradients for the neon look
- No external libraries, no images, no fonts beyond the system stack
- Roughly 1,200 lines, fully readable in one scroll

## File layout

```
.
├── index.html   # The entire game
└── README.md    # This file
```

## Notes &amp; limitations

- No audio. The spec called for purely visual output and no external assets, so the game ships silent. Procedural WebAudio SFX could be added without breaking the single-file constraint &mdash; happy to do that on request.
- Mobile touch is not specifically tuned. The mouse code path works on touch devices, but small mine/orb hitboxes can be tricky on phones.
- Best played fullscreen in a desktop browser.

## License

MIT
