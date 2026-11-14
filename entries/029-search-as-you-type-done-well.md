# 029 — Search-as-you-type done well

> Entry 029 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*Results that keep up with your fingers — and never show you yesterday's query.*

**What it is.** The search box that answers while you type, the way
Google, Algolia, and Spotify do. The naive version fires one request per
keystroke, 22 requests for a 22-character query, and shows stale results
when an old request arrives after a newer one. The good version is a
small stack of patterns working together: a short debounce so the
request waits for a pause in typing; cancellation of the previous
in-flight request so stale results can never overwrite fresh ones; a
minimum of 2–3 characters before searching at all; and local filtering
first: filter a cached or prefetched set instantly on the device, then
refine with the real results when they arrive, so the user always sees
*something* immediately.

**Why it feels good.** Typing is the fastest input a user has, and
search that lags behind it feels broken even when it's technically
working. The local-first trick is the heart of it: the brain registers
the UI as responsive the instant something appears, and the real results
arriving a beat later feel like a refinement, not a wait. Keeping the
previous results visible while new ones load (instead of flashing a
blank state) makes the whole thing feel continuous rather than flickery.

**The numbers.** Algolia's performance docs (updated 2026-09-16) put the
debounce delay at **200 ms preferred**, matched to typing speed
(typically **30 words per minute on mobile, 40 WPM on desktop**), and
warn that **delays over 300 ms start degrading the user experience**;
too short a delay and users see flashes of content. The
minimum-character threshold is **2–3 characters**: single-character
queries are almost always noise. Debounce alone is not enough: without
cancelling the stale request, a slow "re" response can arrive after the
"react" response and show the wrong results (a race condition debounce
does nothing to prevent). And when the network is slow, Algolia's own
advice is to turn search-as-you-type off entirely and restore it when
conditions improve. A degraded mode, not a broken one.

**Where it fits his apps.** **GITDATA** is the obvious home: search
across datasets and tables with local filtering over cached metadata
first. **Code Forge**: search across files and findings, with the 200 ms
debounce keeping a spinning hard drive from being hammered on every
keystroke. **Qwkhnd**: instant filtering of the task list as you type,
local-only so it's free. **DUO**: searching conversations and contacts,
with recent searches cached so a repeat query answers instantly. **Pixel
Forge**: filtering presets and assets by name. On his hardware the
local-first layer matters most: filtering an in-memory list costs
nothing, while a disk or network round trip per keystroke is exactly
what makes search feel slow.

**Watch out.** Never fire a request per keystroke without a debounce.
It's the most common search bug there is. Never show a blank loading
state while the new results are in flight; keep the previous results up.
Don't use search-as-you-type for complex multi-filter queries (flights,
faceted catalogues). There, let the user compose the full query and
press Search; a button is better design than a flickering list. And
don't set the debounce from guesswork: 200 ms is the measured
preference, 300 ms is where it starts to feel sluggish.

## See also

- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)

## Sources

- Improve performance, Algolia Docs, updated 2026-09-16 — https://www.algolia.com/doc/guides/building-search-ui/going-further/improve-performance/react
- Beyond Debounce: The Complete Guide to Fast, Smooth Search UX, DEV Community, 2026-05-24 — https://dev.to/ahr_dev/beyond-debounce-the-complete-guide-to-fast-smooth-search-ux-442d
