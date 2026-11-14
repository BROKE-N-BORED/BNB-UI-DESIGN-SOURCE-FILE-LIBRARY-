# BNB UI Design Source File Library

An encyclopedia of UI design — the library every Broke n' Bored app pulls its
feel from.

This library studies real software that is shipping right now: games, apps,
websites, phones, tablets, gadgets, anything with an interface worth learning
from. What actually works gets written up as an entry: one technique or
concept per file, each sourced and dated, each self-contained. Start at
[INDEX.md](INDEX.md) and find the entry by name, by topic, or by the app you
are building.

## Master rules file

`design-rules.md` at the root is the canonical combined doc: Part 1 is the
design philosophy, Part 2 is the immutable rules (U1-U39 plus delivery rules
D1-D3), Part 3 is the techniques drawer. From 2026-11-13, all UI design rules
and material get pulled from this repo, at Joshua's order. The copy in the
workspace is a working copy; this repo is the source of truth.

## How to use this library

- Start at [INDEX.md](INDEX.md): alphabetical, by topic, or by app.
- Each entry under `entries/` is self-contained: what the technique is, why
  it feels good, the exact numbers (timings, sizes, easing), which apps it
  fits, what to watch out for, and its sources.
- Pull what fits the app you are building. Two or three techniques per app
  is usually the right amount: the ones that fit what the app actually does.
- Entries are numbered permanently. A number is never reused, so a link to
  an entry never breaks.
- Before pulling an entry into a build, run it through the filter below.

## The bar

Every entry has to pass these before it goes in:

1. **The toy test (U34).** A child could pick it up and use it. If the
   technique needs explaining, it doesn't go in.
2. **It runs on the PC.** 8 GB RAM, no GPU, spinning hard drive. Motion must
   be cheap: transform and opacity only, no layout thrash, no heavy blur on
   every frame.
3. **It fits the design rules.** design-rules.md is the source of truth.
   Nothing here overrides it.
4. **It makes the app feel like itself.** Creativity is wanted, and every
   app should have a look of its own instead of the same flat thing.
   Decoration that gives an app its identity is fine. What fails is motion
   or styling that fights readability or costs frames.

## The filter: which techniques to actually use

Before pulling a technique into a build, run it through these four questions.
If it fails any of them, leave it out.

1. **Does it make it simpler?** If the technique adds visual interest but the
   user still has to think harder, it fails. Simpler wins over prettier.
2. **Does it survive the toy test?** A child should be able to pick it up and
   use it. If the technique needs explaining, it doesn't go in.
3. **Does it run on his PC?** 8 GB RAM, no GPU, spinning hard drive. Motion
   must be cheap: transform and opacity only, no layout thrash, no heavy
   blur on every frame. Glass effects and shadows cost real frames on weak
   hardware; use them on small surfaces, not full screens.
4. **Does it make the app feel like itself?** Creativity is wanted — every
   app should have its own look, not the same flat thing. Decoration that
   gives the app its identity is fine. What fails is motion or styling that
   fights readability or costs frames on his PC. (Joshua, 2026-11-13: "some
   shit should be creative... everything you make is boring and looks
   exactly the same.")

This is the one canonical copy of the filter. It lives here and nowhere
else; entries and other files point at it instead of repeating it.

## Contents

- `design-rules.md` — the master rules file. Philosophy, immutable rules,
  techniques drawer.
- `INDEX.md` — the lookup page: alphabetical, by topic, by app.
- `entries/` — the entries, one file per technique:
  - Drop 1 (2026-11-13): 001–012, modern UI design techniques.
  - Drop 2 (2026-11-13): 013–024, games, editors, and gadgets.
- `CHANGELOG.md` — dated history of the library: drops, corrections,
  restructures.
- `verdicts.md` — what happened when entries got used in real builds.
- `templates/entry.md` — the shape every new entry follows.
- `queue.md` — entries to research next.

## Scope

Entries cover techniques today. The same structure fits concepts,
principles, people, and history entries later: one entry per subject,
sourced and dated, numbered permanently, linked from the index.

## Maintenance

Maintained by Arlo from the Maintain BNB UI design library thread. New
entries are researched from live software and current sources, then pushed
here. History lives in [CHANGELOG.md](CHANGELOG.md).
