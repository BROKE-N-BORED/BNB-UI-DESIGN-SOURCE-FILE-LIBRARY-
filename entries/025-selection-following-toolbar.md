# 025 — Selection-following toolbar

> Entry 025 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The tools come to the text you picked, then leave when you let go.*

**What it is.** A small floating row of controls that appears beside a
text selection (bold, italic, link, heading) without occupying a
permanent toolbar. Medium made the pattern familiar for web publishing;
editors built with Tiptap call it a bubble menu. The defining trait is
that the toolbar is *anchored to the selection itself*: it positions
against the selection's bounding box and follows it as the selection
moves, scrolls, or resizes.

**Why it feels good.** Zero travel: the action sits next to the thing it
acts on, so the eye never leaves the text. There is no mode switch and
no ribbon to scan; the toolbar exists only while a selection exists, so
the page stays clean the rest of the time.

**The numbers.** Tiptap's BubbleMenu debounces position updates so the
menu does not jump on every selection change: a default update delay of
250 ms and a resize delay of 100 ms. Positioning runs through Floating
UI middleware: offset (gap from the selection), flip (jumps to the other
side when there is no room), and shift (slides sideways to stay inside
the viewport). The menu shows only for a non-empty selection and
repositions on selectionchange, scroll, and resize. The gotcha that
sinks naive versions: clicking a toolbar button can steal focus and
collapse the very selection the command needs, so the click must not
steal focus and the saved range must be restored before the command
runs. Close on Escape; under prefers-reduced-motion, show and hide
instantly instead of animating position.

**Where it fits his apps.** **DUO**: format a selected span in the
message composer without a permanent formatting bar. **Data Pack
Builder**: format pack descriptions and notes where a full ribbon would
be noise. **STELLA**: quick formatting on any text surface. **GITDATA**:
edit field notes and dataset descriptions in place.

**Watch out.** Never cover the selection itself. Offset above or below
and flip when the edge is near. Keep only actions that apply to the
current selection, and reflect active formats with pressed states. Every
action needs a keyboard path. Motion is a small fade or slide on
transform and opacity only. This is a cheap overlay, not a reason to
blur the page.

## See also

- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [001 Micro-interactions](001-micro-interactions.md)
- [015 Accessibility presets](015-accessibility-presets.md)

## Sources

- BubbleMenu extension, Tiptap Editor Docs — https://tiptap.dev/docs/editor/extensions/functionality/bubble-menu
- Contextual formatting toolbar, Jargon Buster — https://jargon-buster.sivaram.dev/ui-components/contextual-formatting-toolbar/
