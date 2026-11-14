# 019 — Optimistic UI

> Entry 019 — added 2026-11-13 (Drop 2: Games, editors, and gadgets).

*show it done, then confirm*

**What it is.** When the user does something, the UI shows it done
immediately and checks with the server afterwards. No spinner, no waiting
for confirmation. The write goes to a local store first, the screen
updates from that store, and the sync happens in the background, with
retries and conflict resolution handled quietly. If the server says no,
the UI rolls back and says so. Chat apps, social feeds, and like buttons
all work this way now; the pattern is called optimistic because it
assumes success and deals with failure as the exception.

**Why it feels good.** Waiting is the worst part of any app. A spinner
says "your action might have worked, hold on." An optimistic update says
"done," and is right almost every time. The app feels instant because,
from the user's side, it is instant. The network delay still exists; it
just stops being the user's problem.

**The numbers.** No millisecond figure in the source. What it gives
instead is the rule: use optimistic updates where the success rate is
high and the action is small. Do NOT use them for large, complex
transactions, for anything needing heavy server validation, or for any
workflow where showing success early could mislead the user about what
actually happened. A hybrid is fine: optimistic for the small stuff,
confirmed for the serious stuff.

**Where it fits his apps.** DUO (a message appears sent the instant you
hit send, the sync confirms in the background), GITDATA (a save shows as
saved, the write confirms after), Code Forge (a queued job appears in
the queue immediately), Qwkhnd (a lookup shows the cached answer while
it checks for a newer one).

**Watch out.** If the server can say no, the rollback must be visible
and honest: the item quietly un-does itself with a short note, never a
silent lie. Never be optimistic about destructive actions or money.
And if the same data can change in two places at once, you need a
conflict rule (last write wins is fine for likes; it is not fine for
edits).

## See also

- [017 See it before you commit](017-see-it-before-you-commit.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [010 AI-native patterns](010-ai-native-patterns.md)

## Sources

- Building an Optimistic UI with RxDB, RxDB, updated 2026-07-31 — https://rxdb.info/articles/optimistic-ui.html
- Optimistic mutation results, Apollo Client documentation (living docs, undated) — https://github.com/apollographql/apollo-client/blob/main/docs/source/performance/optimistic-ui.mdx
