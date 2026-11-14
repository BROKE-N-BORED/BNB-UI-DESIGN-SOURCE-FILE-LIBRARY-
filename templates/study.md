# Study template

The exact shape every new study follows. A study is a deep dive on one
shipping product (or one video of one): everything it does, the designs
and workflows worth stealing, and what it does not give us. Studies live
under `studies/` and are listed in `INDEX.md` under Studies, not in the
alphabetical entry list. Copy this file, name it after the subject
(`studies/<slug>.md`), and fill it in. Then add it to `INDEX.md`
(Studies section), note it in `CHANGELOG.md`, and mention it in the
README's Studies section if it is the first of its kind.

```md
# <Subject>: <short hook>

> Study, added <YYYY-MM-DD>. <one line on what the study covers>

*<tagline, one line>*

## What it is

...

## The interface

... (the anatomy: what is on screen, what each part does)

## How it works

... (the workflows, step by step)

## What it teaches the library

... (the patterns worth stealing, each linked to the entry it relates
to, or named as a candidate for a future entry)

## What it does not give us

... (honest scope: what is paid, platform-locked, unproven on his PC,
or too big for a first version)

## Open questions

... (what the sources do not settle; noted, not asserted)

## See also

- [<NNN Name>](../entries/NNN-slug.md)
- ...

## Sources

- <Title>, <publication>, <date> — <URL>
- ...
```

## Standing rules

- Sourced and dated. Every study carries the sources its facts came
  from, and the date it was added. Video facts come from frames actually
  read, not from a summary of the video.
- The numbers rule: every figure must be cited from a source actually
  opened. Where a source gives no number, state the mechanism instead,
  never invent.
- Secondary sources are labeled as such in the Sources list.
- What the study does not show is listed, not hidden. If the video
  never presses a button, say so.
- The filter lives only in the README. Never copy it into a study.
- A companion walkthrough (frame by frame, one video) is optional. When
  one exists, the study links to it and does not repeat its contents.
