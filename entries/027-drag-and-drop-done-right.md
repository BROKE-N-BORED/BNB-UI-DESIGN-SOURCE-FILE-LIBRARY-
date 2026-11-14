# 027 — Drag and drop done right

> Entry 027 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*Pick it up, carry it, put it down — and always know where it will land.*

**What it is.** Direct manipulation at its best: the user grabs a thing,
moves it, and drops it somewhere, and the interface narrates every step.
Apple's HIG lays out the full lifecycle. The drag image, a translucent
copy of what's moving, appears after about three points of movement, so
a mere click never starts a drag; translucency distinguishes it from the
original and lets the user see destinations underneath. While dragging,
exactly one destination lights up at a time: an insertion point or a
highlight, shown only while the content hovers over it. An invalid
target shows nothing, or an explicit "not allowed" mark. Drop it
somewhere wrong and the item returns to its source, or scales up and
fades out as if evaporating. Multiple items flock together visually so
the user can confirm nothing was missed, then ungroup on drop.

**Why it feels good.** Dragging is the most physical thing a mouse can
do, and done right it needs no explanation. A child picks things up and
puts them down. The feedback loop is continuous: lift, carry, preview
the landing, land. The rules underneath are invisible but consistent:
same container means move, different container means copy. So the user
builds a correct mental model after one or two drags and never has to
think about it again.

**The numbers.** The HIG's numbers are small and exact: the drag image
appears after **about 3 points** of movement. The rest is mechanism, and
the mechanism is the entry: **same container → move; different container
→ copy; between apps → always copy** (and read the modifier key at drop
time, not drag start: holding Option forces a copy, releasing it before
dropping makes it a move). **Spring loading**: hovering dragged content
over a folder, tab, or segmented control opens it, so the user can drill
into a deep destination without dropping. **Flocking** groups multi-item
drags; a numeric badge counts them. After the drop, the dropped content
stays selected in its new home. And the standing rule: drag and drop is
an enhancement, never the only path: every draggable action must also
exist as a menu command, button, or copy/paste, because dragging is
impossible for some users.

**Where it fits his apps.** **Pixel Forge**: drag images onto the canvas,
reorder layers and sheet frames, drag out to export; spring-loaded
folders for deep layer groups. **LYNX SHARE (DAW)**: drag clips between
tracks, with the insertion point showing exactly where the clip lands on
the timeline. **Reblend**: drag materials onto objects, with the object
highlighting as the single live target. **Qwkhnd**: drag tasks between
columns, same-container move, with the task staying selected after the
drop. **Data Pack Builder**: drag entries between packs, cross-pack
meaning copy unless the user holds the modifier.

**Watch out.** Never make dragging the only way to do something. Always
ship the menu/button alternative. Never light up every possible target
at once; one destination at a time, only while hovered. Prefer undoable
drops; where a drop can't be undone, ask first (the Finder confirms
dropping into a write-only folder because the file couldn't be retrieved
afterward). Don't let the drag image change constantly or radically
mid-drag. It must stay recognisable as the thing being carried. And keep
the motion cheap: the drag image is a translate + opacity, which is
exactly what the 8GB no-GPU machine handles well.

## See also

- [002 Spring physics motion](002-spring-physics-motion.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)

## Sources

- Notifications, Sharing, Drag & Drop, Files & Printing, apple-hig-skills, GitHub — https://github.com/yue1123/apple-hig-skills/blob/HEAD/apple-hig/references/patterns/notifications-sharing-files.md
- Drag and drop, HIG Doctor (structured index of Apple's canonical HIG drag-and-drop page, snapshot 2025-02-02; corroborates the 3-point drag image, Option at drop time, spring loading, badge, and selection rules) — https://apple.raintree.technology/topics/drag-and-drop
