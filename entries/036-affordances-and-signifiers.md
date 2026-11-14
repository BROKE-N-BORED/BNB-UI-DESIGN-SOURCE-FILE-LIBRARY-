# 036 — Affordances and signifiers

> Entry 036 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The thing tells you what it does before you ever read a label.*

**What it is.** An affordance is the relationship between an object's
properties and a person's capabilities that determines how the object
could be used. A flat plate on a door affords pushing, a handle affords
pulling, a raised button affords pressing, a slider affords dragging.
Ecological psychologist James J. Gibson coined the term in the 1960s for
the actionable possibilities an environment offers. What matters for
designers is the *perceived* affordance: what the user believes they can
do. Don Norman brought the concept into human–computer interaction in
*The Design of Everyday Things* (1988; revised and expanded 2013), and
later introduced a second term to clear up the confusion: the
**signifier**, the perceivable cue (a label, an underline, a shadow, a
chevron) that tells the user where the action is and how to perform it.
Affordance is the capability; signifier is what the user can actually
see. A glass door with no visible handle has the affordance of pushing
but no perceived affordance, and the user doesn't know where or how to
push.

**Why it matters.** Every entry in this library is, at root, an
affordance made visible. A button that doesn't look clickable is a
feature nobody has; a decorative element that looks clickable but isn't
is a false affordance that erodes trust. The categories give the library
a shared vocabulary: explicit affordances (a labelled button), hidden
affordances (a hover menu, use sparingly), pattern affordances
(underlined blue text means link), metaphorical affordances (a shopping
cart means buy), negative affordances (a greyed-out button says "not
yet"), and false affordances (underlined text with no link, remove or
restyle). Signifiers are often more important than affordances
themselves, because they communicate the designer's intention.

**The key facts.** Gibson coined "affordance" in the 1960s; his book
*The Ecological Approach to Visual Perception* is 1979. Norman's *The
Design of Everyday Things* is 1988, revised 2013; his real-vs-perceived
affordance distinction is from 1999. Nielsen's 10 usability heuristics
(1994) and Shneiderman's 8 golden rules (first published 1987) overlap
the same ground from different angles. Norman's principles explain *why*
designs succeed or fail, Nielsen's are for evaluating existing designs,
Shneiderman's for designing new ones.

**Where it fits his apps.** Everywhere, as the diagnostic lens: when a
feature goes unused in **DUO**, **MIMIK**, or **Qwkhnd**, the first
question is whether its affordance is visible. Does the card look
tappable, does the draggable thing look draggable, does the greyed-out
button explain what's missing? **Pixel Forge**: tool buttons that look
pressable, sliders with visible handles. **Code Forge**: the run button
that looks like the most important thing on the screen, because it is. A
design-system rule falls out of it directly: never suggest an action
that doesn't exist.

**What it gets wrong.** The term itself was overloaded for years.
Designers used "affordance" to mean the visible cue, which is why Norman
had to invent "signifier" to separate the two. Don't repeat that
confusion in the library: capability is the affordance, cue is the
signifier. And affordances are relational, not absolute. A door handle
affords opening to someone tall enough to reach it but not to a toddler,
so the same interface can have different affordances for different
users. Minimalist design that hides every cue in the name of cleanliness
is the classic failure mode: everything flat, nothing looks interactive,
users don't know where to act.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [015 Accessibility presets](015-accessibility-presets.md)

## Sources

- What Are Affordances in Design? 2026 Guide & UI Examples, Parallel HQ — https://www.parallelhq.com/blog/what-are-affordances-in-design
- Design Heuristics and Guidelines, Textbook of Usability — https://www.textbookofusability.com/chapter/design-heuristics-and-guidelines.html
