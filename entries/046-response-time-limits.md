# 046 — Response-time limits

> Entry 046 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Three numbers decide whether an app feels instant, patient, or broken.*

**What it is.** Human perception sets three hard limits on how long a system may take to answer, and they have not changed since researchers first measured them in the 1960s. At 0.1 seconds a response feels instantaneous, and the user feels they are moving things directly. At 1 second the flow of thought stays unbroken, though the delay is noticed. At 10 seconds attention gives out, and the user turns to something else. Jakob Nielsen published them in 1993, drawing on Miller (1968) and Card et al. (1991), and restated them unchanged in a 2014 update. Sitting inside those limits is the Doherty threshold: when a computer answers in under about 400 milliseconds, neither person nor machine waits on the other, and people stay in flow and work faster.

**Why it feels good.** Waiting is the most common friction in any app, and these limits explain why small delays matter out of proportion to their length. A response inside 0.1 seconds feels like an extension of the hand. A response inside a second keeps the next step in short-term memory, so the user never has to reconstruct what they were doing. Doherty and Thadani found the mechanism in 1982: people hold their next few steps in short-term memory, and a long wait breaks that train of thought, so every slow response costs more than its own length.

**The numbers.** Nielsen's three limits: 0.1 second for direct manipulation (no special feedback needed except showing the result); 1 second for uninterrupted flow (delays of 0.2 to 1.0 seconds are noticed but tolerable, and past 1 second the UI should show the computer is working, for example by changing the cursor); 10 seconds for attention (anything slower needs a percent-done indicator and a clearly signposted way to interrupt). For operations between 2 and 10 seconds, a percent-done indicator is overkill; Nielsen recommends a busy cursor plus a small rapidly changing number. Doherty and Thadani (IBM, 1982): as response time fell from 3 seconds to 0.3 seconds, programmers' throughput roughly doubled, from 180 to 371 transactions an hour, and cutting 2.7 seconds of computer time saved about 10 seconds per task because the programmers themselves got faster. One honest caveat: the 1982 paper never names 400 milliseconds. It argued for sub-second response, with its fastest data point at 0.3 seconds, and the 400 ms figure comes from later summaries. Google's 2009 experiment points the same way: slowing search results by 100 to 400 milliseconds made users search 0.2% to 0.6% less, and the effect lingered for weeks after the delay was removed.

**Where it fits his apps.** Pixel Forge: brush strokes, canvas panning, and layer toggles must answer inside 0.1 seconds or the tool feels disconnected from the hand; a filter that takes longer gets a progress readout, not a frozen canvas. Code Forge: a review run takes seconds to minutes, so acknowledge the click at once and show real progress with a cancel button. STELLA and DUO: local model calls take seconds, so stream tokens as they arrive and the wait becomes visible work instead of a blank stare. Fyrn: a model pull runs for minutes, so percent-done plus time left plus cancel is the whole design. ACR: analysis over a file or folder takes seconds, so show which file is being processed and how many remain.

**Watch out.** Do not hide slowness behind animation: a long transition is still a wait, so keep movement short. Do not show a spinner for a 200 millisecond wait; it flashes like a glitch, so wait about half a second before showing one. Do not show a progress bar that sits at 99% for a minute; people notice when the bar has nothing to do with the work. Acknowledge every tap within 0.1 seconds even if the real work takes longer, or users tap again and do the action twice. And remember the limits are about response, not total task time: a fast-answering app can still do long work, it just has to stay honest about it.

## See also

- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [019 Optimistic UI](019-optimistic-ui.md)
- [002 Spring physics motion](002-spring-physics-motion.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)

## Sources

- Response Times: The 3 Important Limits, Jakob Nielsen, Nielsen Norman Group, 1993 (updated January 31, 2024) — https://www.nngroup.com/articles/response-times-3-important-limits/
- Doherty Threshold in UX: Definition and Examples, Shirish Shikhrakar, ux360.design, October 14, 2026 — https://ux360.design/doherty-threshold/
