# 005 — Bento grids

> Entry 005 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*size is the hierarchy*

**What it is.** Named after the Japanese lunch box. Instead of one long column,
the screen breaks into neat blocks of different sizes. A big block for the
main point, smaller blocks around it for supporting details. Every tile is
self-contained and has exactly one job. The asymmetry is the point: bigger
tile, more important content. The layout itself tells you where to look
first, no labels needed.

**Why it feels good.** Each tile is one idea, so your brain never has to hold
the whole page at once. You scan in seconds instead of reading linearly.
Users form a first impression of a dashboard's usefulness in under six
seconds, and spatial weight pre-answers "what matters here" before a word is
read. On a phone, the tiles restack into a single column ordered by priority,
not by their original position, so the hierarchy survives any screen.

**The numbers.**
- Grid: 3 to 5 columns. One hero tile per layout (4 to 6 columns wide,
  2 rows tall).
- Gaps: uniform, 16 to 24 px on desktop, 8 to 16 px on smaller screens.
- Corners: rounded, 12 to 24 px radius. Square corners read as a table.
- 5 to 10 cells per layout. More than that and it stops being scannable.

**Where it fits his apps.** STELLA's main screen (one big tile: pick a model,
pick a job, press go; small tiles: RAM, speed, progress). Forge's deck.
GITDATA's results. Any dashboard or home screen that has to show ten things
at once without shouting.

**Watch out.** Bento fails when every box is the same size, or when the
hierarchy is unclear. Symmetric grids look like spreadsheets. If the sizes
don't mean something, it's just a wall of boxes.

## See also

- [021 Glanceable surfaces](021-glanceable-surfaces.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)

## Sources

- Bento Grid Dashboard Design: Complete Guide 2026 — https://www.orbix.studio/blogs/bento-grid-dashboard-design-aesthetics
- Bento Grid Web Design — https://webpo.space/blog/bento-grid-web-design
