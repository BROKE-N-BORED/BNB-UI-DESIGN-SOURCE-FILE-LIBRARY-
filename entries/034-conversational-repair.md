# 034 — Conversational repair

> Entry 034 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*When the voice gets it wrong, it says what it heard and asks for just the missing piece.*

**What it is.** The one voice technique sharp enough to stand alone:
repair. Mishearing is the norm in voice interfaces, not the edge case,
so the recovery turn *is* the design. When understanding fails, the
system echoes what it did hear and asks for only the piece that failed,
then escalates with more guidance each time, instead of repeating "I
didn't understand."

**Why it feels good.** Repeating "Sorry, I didn't get that" punishes the
user for the system's failure. A repair that shows its work ("I heard
you asking about flour measurements. Did you want grams to cups?") keeps
the conversation moving and tells the user exactly where the gap is.

**The numbers.** Match confirmation to risk: implicit confirmation for
low-stakes actions ("Set a timer for 5 minutes" → "Starting 5-minute
timer"), explicit confirmation for anything irreversible. Keep responses
to one breath. Amazon's one-breath test says if you can say a response
at a conversational pace in one breath, the length is right, and a
comfortable breath is 6–8 seconds of speech. Working memory holds 3–4
pieces of information, so never read a long option list aloud. Latency
targets: wake-word detection under 500 ms, a simple command answered in
under 1 second, a query in under 2 seconds, a complex action in under 3
seconds with progressive feedback while it runs. Always allow barge-in:
the user can interrupt mid-prompt. Reprompts escalate with guidance ("I
didn't catch that. You can say 'checking,' 'savings,' or 'credit
card.'"), and a stuck conversation offers an exit ramp to the app or a
human. Discoverability comes from signifiers: explicit verbal prompts,
implicit cues like appending "Sound good?", and nonverbal earcons such
as a short tone.

**Where it fits his apps.** **STELLA** is the primary home: repair
turns, one-breath replies, barge-in, and explicit confirmation before
any irreversible spoken action. **DUO**: voice input in chat: show what
was heard as a transcript so the user can correct it in text instead of
re-speaking. **LYNX SHARE (DAW)**: hands-busy DAW control while playing
("record take 3"), where a misheard command must be repaired without
stopping the session.

**Watch out.** Never design voice-only for comparisons or long lists.
Pair voice with a screen, and let the screen carry the comparison. Do
not force one rigid phrasing path; map synonyms to the same intent and
expect accents and natural variation. Be transparent about when the
system is listening and what is recorded. Design the error branches
first. Most voice quality lives in the non-happy paths.

## See also

- [012 Progressive disclosure](012-progressive-disclosure.md)
- [015 Accessibility presets](015-accessibility-presets.md)
- [010 AI-native patterns](010-ai-native-patterns.md)
- [003 Calm technology](003-calm-technology.md)

## Sources

- Voice User Interface Design: Principles & LLM, Resourcifi — https://www.resourcifi.com/insights/voice-ui-design/
- Voice UI Design Principles, TechPlato — https://www.techplato.agency/blog/39-voice-ui-design-principles
