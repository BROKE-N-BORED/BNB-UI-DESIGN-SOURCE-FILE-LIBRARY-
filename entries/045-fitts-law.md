# 045 — Fitts's law

> Entry 045 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Big targets close by are fast; small targets far away are slow, and the math says by how much.*

**What it is.** Fitts's law, published by psychologist Paul Fitts in 1954, predicts how long a pointer (mouse cursor, finger) takes to reach a target. The formula is MT = a + b log2(2D/W): movement time grows with distance (D) and shrinks with target width (W), and the logarithm means doubling the distance adds a fixed amount of time rather than doubling it. The log term is called the index of difficulty, measured in bits. Fitts came to it from studying aircraft cockpit controls in World War II, where reaching the wrong switch had real consequences. It has since been validated across mouse, touch, pen, eye tracking, and physical reaching.

**Why it matters.** The law turns "make buttons bigger" from taste into arithmetic: enlarge the frequent targets and the ones far from where the cursor rests. Screen edges and corners are the famous free win: the cursor cannot overshoot an edge, so a target on one has effectively infinite width in that direction and the slow-down phase disappears. That is why the macOS menu bar lives at the top edge and the Windows taskbar at the bottom, and why the four corners are the highest-value spots on a screen (each benefits from two infinite edges). It also explains why menus that appear at the cursor feel instant: the distance term drops to near zero.

**The key facts.** The index of difficulty is ID = log2(2D/W), so doubling the distance adds exactly one bit of difficulty and doubling the target width removes exactly one bit. The Shannon form, ID = log2(D/W + 1), avoids negative difficulty for very close targets and is the ISO 9241-9 standard. Fits to real movement data are tight: typical R² values exceed 0.95. Measured throughput is 4 to 5 bits per second for a mouse and roughly 5 to 7 for direct finger input. Apple's Human Interface Guidelines set a minimum touch target of 44 × 44 points (about 7 × 7 mm), the practical floor for reliable finger acquisition. For rectangular targets, the width that counts is the smallest dimension, height or width (MacKenzie and Buxton, 1992). Movement has two phases (Woodworth, 1899): a fast ballistic fling, then a slow correction phase that small targets stretch out, which is why tiny targets feel disproportionately slow.

**Where it fits his apps.** Pixel Forge: the most-used tools (brush, eraser, undo) as the biggest toolbar targets, and color swatches large enough to hit without slowing down. LYNX SHARE: clip pads and transport controls sized generously, with the most-hit controls (play, record) at a screen edge or corner. Yahtzee: big dice and score buttons, with the roll button close to where the dice land. MIMIK: a large capture button near the preview, not a small icon in a far corner. Code Forge: review actions next to the diff they act on, so the cursor never crosses the window to approve a fix.

**What it gets wrong.** Fitts's law models one aimed movement, not a whole task: it says nothing about deciding which target to aim for (that is Hick's law territory), and moving faster still means more errors. It does not cover steering through a path: cascading menus, where the cursor travels a narrow corridor to a submenu, follow the steering law instead, where the penalty is linear, not logarithmic, so narrow corridors punish more than the pointing formula suggests. The edge trick is mouse-only: on touchscreens, edge targets are actually slower to hit, because a finger can overshoot past the edge (Avrahami, 2015). Padding a target's invisible click area helps only if the user knows it is there; otherwise they still slow down for the visible size. And bigger is not always better: crowded big targets cause overshoot into the neighbor, so spacing matters as much as size.

## See also

- [016 Pie menus](016-pie-menus.md)
- [025 Selection-following toolbar](025-selection-following-toolbar.md)
- [027 Drag and drop done right](027-drag-and-drop-done-right.md)
- [015 Accessibility presets](015-accessibility-presets.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)
- [042 Touch targets you can actually hit](042-touch-targets-you-can-actually-hit.md)

## Sources

- Fitts's Law and Its Applications in UX, Nielsen Norman Group, published 2022-07-31, updated 2024-01-24 — https://www.nngroup.com/articles/fitts-law/
- Motor Control and Fitts's Law, Textbook of Usability, 2026 — https://www.textbookofusability.com/chapter/motor-control-and-fitts-law.html
