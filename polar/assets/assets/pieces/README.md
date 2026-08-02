# Piece icons

Flat abstract glyphs, redesigned from scratch to prioritize legibility on the
board over resemblance to the physical 3D-printed pieces. The 3D models
(`PolarChess/Renderings/*.jpeg`) were consulted only loosely for inspiration,
not traced.

Each glyph is tied to the piece's name and movement rather than its physical
shape, on the theory that a shape a player can connect to what the piece
*does* is more useful on a board than a shape that matches a tabletop object
they may never see:

- `clone.svg` — a plain dot. The simplest piece gets the simplest, smallest
  glyph.
- `prime.svg` — a crown zigzag. The royal piece.
- `omni.svg` — a four-point compass star. Moves in every direction (it's
  Radial + Arc combined), so it gets the "every direction" glyph.
- `radial.svg` — a ring. Moves around the ring, or straight through the
  center — literally radial.
- `arc.svg` — a bold, right-side-only crescent with pointed top and bottom
  tips, like a thick parenthesis. Built from two arcs sharing the same two
  endpoints (top and bottom tip) instead of two full circles: one more
  curved (the outer edge, close to a semicircle), one flatter (the inner
  edge), both bulging the same direction. Sharing endpoints makes the tips
  pointed by construction, and since neither arc has any geometry left of
  the tips, there's no left-side lobe either.
- `vector.svg` — a bold lightning-bolt zigzag. An earlier version used a
  straight line bending 90 degrees into an arrowhead, which visually showed
  the two-then-one leap but read as a street sign rather than a game piece;
  the zigzag keeps the "sharp direction change" idea without looking like
  signage.

## Conventions

- `viewBox="0 0 100 100"`, so all six compose at a consistent scale.
- `fill="currentColor"` for all six — no hardcoded color. Tint per player in Flutter via
  `ColorFiltered` / `SvgPicture`'s `colorFilter`, rather than shipping separate
  light/dark files.
- No background shape included.

## Contrast on the board — a note for Phase 3

A single-color silhouette won't stay legible against every board square color
on its own (a light piece can wash out on a light square, etc.). Rather than
baking a fixed-color outline into these assets, render each piece on its own
solid-color token disc (consistent per player, independent of the square
underneath) — that's a rendering decision for the board widget, not something
that belongs in the icon files.

## Status

First draft of the redesigned set. Not yet checked at actual board-wedge size
on a real device.
