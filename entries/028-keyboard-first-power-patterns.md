# 028 — Keyboard-first power patterns

> Entry 028 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*Every action has a key. The mouse is optional, never required.*

**What it is.** The Linear / Gmail / Superhuman school of desktop
design: every common action has a keyboard shortcut, navigation is
single keys (J/K to move through a list, Enter to open, E to archive),
and a `?` key opens a help overlay listing every shortcut, grouped by
context. Underneath, the discipline is a **central registry**: one map
from canonical key combination to action, one global key listener that
dispatches against it, and the help overlay, menu hints, and tooltips
all generated from that same registry, so the help can never drift out
of date with the bindings. Shortcuts are scoped: the same key can mean
different things on a board, in an editor, or in a modal, and an open
modal wins exclusively. And the input-field guard is sacred: a shortcut
must never fire while the user is typing in a text field.

**Why it feels good.** Once learned, the keyboard is pure flow: no
hunting, no aiming, no menus. A list triaged with one key per item (read
it once, press one key, it's gone) turns a chore into a rhythm. But the
pattern only works because it's *discoverable*: the `?` overlay teaches
the shortcuts in context, menu items show their keys, and the user
graduates from mouse to keyboard at their own pace instead of facing a
blank wall of bindings.

**The numbers.** The mechanism is the spec. Chords (multi-key sequences
like `g` then `i`) carry a **~1 second timeout**. Press `g`, wait a
minute, press `i`, and nothing fires, because the buffer cleared. Letter
bindings use the **physical key position**, not the character produced,
so muscle memory survives AZERTY and Dvorak layouts (the one exception
is `?` itself, which is genuinely a character and lives on different
physical keys per layout). **WCAG 2.1.4** is the accessibility floor:
single-key shortcuts must be disableable or remappable, because a single
letter can collide with a screen reader's own navigation keys. Never
steal Tab / Shift+Tab (focus traversal), the browser's address-bar and
tab keys, or screen-reader keys. And `preventDefault` only on a matched
shortcut, so unmatched keys pass straight through.

**Where it fits his apps.** **Code Forge**: J/K through the file list
and findings, single keys for build/run/test, `?` overlay generated from
the registry (this is a keyboard app's home turf; note the command
palette itself is a GUIFX pattern and out of scope here. This entry is
about the shortcut *system* underneath). **DUO**: J/K through
conversations, E to archive, R to reply, all without touching the mouse.
**Qwkhnd**: one key per task triage action. **Pixel Forge**: number keys
for tools, brackets for brush size, with the overlay teaching them.
**LYNX SHARE (DAW)**: transport keys (space, record, loop) that work
even when a panel has focus, because scopes resolve before the panel
does.

**Watch out.** Never scatter `keydown` listeners across components. One
global listener, one registry, or two handlers will fight over the same
key. Never hand-maintain the help dialog. Generate it from the registry
or it will lie within a month. Never fire shortcuts inside text fields
or rich-text editors (the `contenteditable` case is the one everyone
misses). Never override a single letter globally without a disable/remap
path. That's a WCAG failure and it breaks screen readers. And don't ship
shortcuts without the `?` overlay: undiscoverable shortcuts are features
nobody has.

## See also

- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [016 Pie menus](016-pie-menus.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)

## Sources

- Design a Keyboard Shortcut System, JSBits — https://www.jsbits.com/frontend-design/design-a-keyboard-shortcut-system
