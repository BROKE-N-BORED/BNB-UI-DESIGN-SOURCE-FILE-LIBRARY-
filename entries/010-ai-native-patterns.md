# 010 — AI-native patterns

> Entry 010 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*the interface for talking to a model*

**What it is.** The patterns built for products where the model is the point:
streaming text that appears as the model works, a prompt-first layout where
the text box sits at the center instead of a menu, and trust cues (citations,
confidence signals) that tell you where an answer came from. Also
provenance: showing what is generated and what is real, in the interface
itself.

**Why it feels good.** Streaming text is honest: you watch the work happen
instead of staring at a spinner. A prompt-first layout says the job is
"ask for what you want," not "find the right button." Trust cues answer the
question every user has about AI output: where did this come from, and should
I believe it?

**Where it fits his apps.** Forge (streaming replies, the model working
visibly, tool calls shown as they happen). STELLA's chat (plain words in,
training set up, with the plan shown before it runs). ACR's trace log (every
weight change shown, nothing hidden). The Data Pack Builder's promise (every
sentence traces back to the source) is a trust cue, and it should look like
one in the UI: show the source next to the pack, not buried in a file.

## See also

- [019 Optimistic UI](019-optimistic-ui.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)

## Sources

- 8 UI Design Trends in 2026, Wavespace, updated 2026-09-10 — https://www.wavespace.agency/blog/ui-design-trends
- Five UI Patterns That Look Poised to Define 2026, DEV, 2026-05-05 — https://dev.to/sissie_hensley_568968e0fb/five-ui-patterns-that-look-poised-to-define-2026-59k3
