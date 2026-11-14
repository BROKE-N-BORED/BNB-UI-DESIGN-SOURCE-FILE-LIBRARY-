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

## Reference rule repos

Three external repos are rule repos for UI design work, alongside this
library (Joshua, 2026-11-13). This repo stays the source of truth for
his rules; these three are the external references every UI design
task, build, and project pulls from. When the library writes up a
technique or a project needs a resource (a font, an icon set, a color
tool, a design system to study), check these three first and cite the
entry. Free and open-source first, matching the hard $0 rule.

- bradtraversy/design-resources-for-developers (67,398 stars,
  2026-11-13): curated list of design and UI resources. UI graphics,
  fonts, colors, icons, logos, favicons, icon fonts, stock photos,
  stock videos, stock music and sound effects, vectors and clip art,
  product and image mockups, HTML and CSS templates, CSS frameworks,
  CSS methodologies, CSS animations, JavaScript animation libraries,
  JavaScript chart libraries, UI components and kits,
  React/Vue/Angular/Svelte/React Native UI libraries, design systems
  and style guides, online design tools, downloadable design software,
  design inspiration, image compression, Chrome/Firefox extensions, AI
  graphic design tools.
  https://github.com/bradtraversy/design-resources-for-developers
- VoltAgent/awesome-design-md (127,420 stars, 2026-11-13): DESIGN.md
  files analyzing popular brand design systems, organized by category:
  AI and LLM platforms, developer tools and IDEs,
  backend/database/DevOps, productivity and SaaS, design and creative
  tools, fintech and crypto, e-commerce and retail, media and consumer
  tech, automotive, retro web. Each DESIGN.md explains what is inside
  and how to use it: drop one into a project and a coding agent builds
  from it.
  https://github.com/VoltAgent/awesome-design-md
- gztchan/awesome-design (17,775 stars, 2026-11-13): curated design
  resources from all over the world. Stock, color, icon and logo,
  typography, toolkit, prototyping, mockup, user testing, read and
  digest, styleguide and branding, tutorial, book, award, conference
  and festival, podcast, community.
  https://github.com/gztchan/awesome-design

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
  - Drop 3 (2026-11-13): 025–036, input, feedback, and forgiveness.
  - Drop 4 (2026-11-13): 037–048, seeing, learning, and responding.
  - Drop 5 (2026-11-13): 049–060, choices, motion, and craft.
  - Drop 6 (2026-11-14): 061–072, structure, comfort, and trust.
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
