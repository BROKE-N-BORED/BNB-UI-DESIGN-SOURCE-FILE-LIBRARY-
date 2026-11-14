# 011 — Skeleton screens and honest loading

> Entry 011 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*never a dead screen*

**What it is.** Instead of a spinner on a blank screen, show the shape of the
content that is coming: grey blocks where the text and images will land.
When the content arrives, it fills the shape. The user sees structure
immediately and progress continuously.

**Why it feels good.** A spinner says "wait." A skeleton says "here is what is
coming, and it is on its way." It also stops layout jump: the content lands
where the skeleton said it would, instead of shoving everything around.

**Where it fits his apps.** Any list that loads from disk or a model: Forge's
history, GITDATA's search results, Fyrn's model list, the Data Pack Builder's
results table. Pair it with real numbers (files read, records found), not a
fake progress bar. This is U16 and U26 from the rules, as a named technique.

**Watch out.** Do not build a skeleton for perceived speed: in Viget's
2017 study (136 participants) the skeleton produced the *longest*
perceived wait — 2.82 seconds against 2.41 for a spinner and 2.29 for a
blank screen. Build it for layout stability instead: the placeholder
must match the real content's geometry exactly, or it causes the shift
it was meant to prevent. And keep it to waits of roughly 1 to 10
seconds — under a second it flashes, past ten the user needs a real
progress indicator.

## See also

- [010 AI-native patterns](010-ai-native-patterns.md)
- [008 Delight, done right](008-delight-done-right.md)
- [019 Optimistic UI](019-optimistic-ui.md)

## Sources

- Skeleton Screens 101, Nielsen Norman Group, 2023-06-04 — https://www.nngroup.com/articles/skeleton-screens/
- What Are Skeleton Screens? Why They Improve UX, wpdean, 2025-04-11 — https://wpdean.com/what-are-skeleton-screens/
- Skeleton Loading Screen: The CSS and the Evidence, The Plus Addons, 2026-09-03 — https://theplusaddons.com/blog/skeleton-loading-screen/
