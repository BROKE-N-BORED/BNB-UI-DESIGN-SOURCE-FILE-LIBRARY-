# Changelog

Dated history of the library: what landed, what changed, what got struck.
Newest first.

## 2026-11-13 — Drop 5: choices, motion, and craft (entries 049–060)

Twelve new entries: Hick's law, the aesthetic-usability effect, design
tokens, text that scales, starter content and templates, notification
batching, blur-up placeholders, staggered entrances, shared-element
transitions, FLIP layout animations, elastic overscroll, and overview
first, details on demand. Four are concept entries (Hick's law, the
aesthetic-usability effect, overview first, design tokens), the most of
any drop. Five came from the queue: Hick's law, the aesthetic-usability
effect, overview first, text that scales, and starter content and
templates. Motion and feel, the thinnest theme at three entries, gains
four (staggered entrances, shared-element transitions, FLIP layout
animations, elastic overscroll) and is thin no more. The thinnest apps
gain the most: STELLA from twelve entries to twenty-two, Fyrn from
twelve to twenty-two, Reblend from thirteen to twenty-three, Yahtzee
from thirteen to twenty-four.

The thin-source strengthening is finished: all ten single-source
entries (004, 008, 013, 018, 019, 020, 022, 023, 024, 028) gained a
second source each, from pages actually opened, with bodies untouched.
No entry in the library rests on a single source anymore. Two research
notes were filed for Drop 6 (feedback loops, progressive
enhancement), each one source short of a draft.

## 2026-11-13 — Drop 4: seeing, learning, and responding (entries 037–048)

Twelve new entries: data visualization for non-analysts, comparison and
diff views, triggered coach marks, tooltips that teach, reduced motion
done right, touch targets you can actually hit, command palette, inline
validation, Fitts's law, response-time limits, live presence and named
cursors, and sound as UI feedback. Fitts's law is the library's second
concept entry, after 036. Five came from the queue: data visualization
(the strongest holdover, from the WWDC22 chart talk and Nielsen Norman
Group), comparison and diff views, triggered coach marks (held in Drop
3 for weak sourcing, now resting on two NN/g articles, Apple's tips
guidance, and a peer-reviewed study), live presence (held for a single
source, now with a second in the Liveblocks docs), and sound as UI
feedback (held for a single secondary doc, now resting on Material
Design's sound guidance and the freedesktop Sound Theme Specification).
The three thin themes are filled out: onboarding and learning,
accessibility and comfort, and browsing and preview each go from two
entries to four. The two thinnest apps gain the most: Fyrn from six
entries to twelve, ACR from seven to fourteen.

The HIG re-check owed from Drop 3 is done as far as the browser allows:
developer.apple.com still would not load, but the HIG Doctor mirror of
Apple's current drag-and-drop page confirms every checkable claim in
entry 027 (the 3-point drag image, Option read at drop time, spring
loading, the multi-item badge, selection kept after the drop), and it
is now 027's second source. Entry 026's numbers stay flagged as
reconstructions, which is what they are. One correction from the
research: the WWDC22 chart talk is session 110340, not 10124 as the
queue had it.

## 2026-11-13 — Drop 3: input, feedback, and forgiveness (entries 025–036)

Twelve new entries: selection-following toolbar, swipe actions on list
rows, drag and drop done right, keyboard-first power patterns,
search-as-you-type done well, toasts and snackbars that respect
attention, empty states and error states done well, self-hiding chrome,
forgiving UI, conversational repair, tiered permission gates, and the
library's first concept entry, affordances and signifiers. Six came from
the Drop 2 queue (the floating toolbar, self-hiding HUD, swipe actions,
undo-everywhere, voice-first UI, and agentic interfaces — each narrowed
to one sharp technique with real numbers); six are fresh finds from
shipping software. Every source was opened and every figure checked
against the page it came from.

The five Drop 1 source gaps are filled: 007 Liquid Glass, 009 Shape
morphing, 010 AI-native patterns, 011 Skeleton screens, and 012
Progressive disclosure all have Sources sections now, from the two
unattributed roundups plus Nielsen Norman Group, Material Design 3, and
the M3 motion reference on GitHub. No entry in the library is sourceless
anymore.

## 2026-11-13 — Restructure: the encyclopedia

The two batch files were split into 24 entries under `entries/`, one file
per technique, numbered permanently (001–024). Added `INDEX.md`
(alphabetical, by topic, by app), `CHANGELOG.md`, `verdicts.md`,
`templates/entry.md`, and `queue.md`. Added the MIT `LICENSE`. The old
batch files were retired; their content lives on in the entries, checked
against the originals so nothing was dropped. The filter now lives in one
place only: the README.

Five Drop 1 entries have no attributable source in the batch file's
Sources list, so their Sources sections are empty for now: 007 Liquid
Glass, 009 Shape morphing and continuity, 010 AI-native patterns,
011 Skeleton screens and honest loading, 012 Progressive disclosure.
They are flagged in `queue.md` for source research.

## 2026-11-13 — Drop 2: games, editors, and gadgets (entries 013–024)

Twelve techniques hunted outside the usual app-design roundups: diegetic
UI, teach by playing, accessibility presets, pie menus, see it before you
commit, scrub through time, optimistic UI, setup checklist, glanceable
surfaces, per-context profiles, focus-first navigation, clip launcher.
Every source was spot-checked against the live page before the drop
landed. Two fixes came out of verification: "launching" corrected to
"launched" for the May 22 and July 9, 2026 dates (both past by the time
the drop landed), and the Hover Scrub wording tightened to what the Adobe
source actually says (Shift + H turns it off; the source does not state
it is on by default).

## 2026-11-13 — Q4 creativity correction

The "no decoration for its own sake" line was struck everywhere. It was
Arlo's own note, not Joshua's rule — there is no rule against decoration.
Question 4 of the filter is now "Does it make the app feel like itself?"
Creativity is wanted; decoration that gives an app its identity is fine.
(Joshua, 2026-11-13: "some shit should be creative... everything you make
is boring and looks exactly the same.")

## 2026-11-13 — The three uploads, checked first

Three files sent the same day were diffed against the library before
anything went in: the Modern UI file was already file 001
(byte-identical), the standalone rules were already inside the master
doc, and the combined file with the STELLA brief was the pre-removal
snapshot — the STELLA part stays out, per Joshua's order 2026-11-13.
Nothing was duplicated.

## 2026-11-13 — Foundation (commit ebeaa26f)

`design-rules.md` landed at the root as the master rules file: the
combined 578-line doc (philosophy, U1–U39 plus D1–D3, techniques drawer),
with its header pointing at this repo as the source of truth. The README
was rewritten around it, and file 001 was reconciled to the canonical Q4.

## 2026-11-13 — Seed (commit 85d5f5bf)

The library opened with the README charter and file 001: twelve modern UI
design techniques (micro-interactions, spring physics, calm technology,
just-in-time GUI, bento grids, neo-skeuomorphism, liquid glass, delight,
shape morphing, AI-native patterns, honest loading, progressive
disclosure).
