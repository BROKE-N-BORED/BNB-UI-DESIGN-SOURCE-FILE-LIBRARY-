# 048 — Sound as UI feedback

> Entry 048 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*A short sound says "that worked" faster than any label can.*

**What it is.** An earcon links an action, or a state change, to a short audio cue, and its sound reinforces both the meaning of the interaction and the product's personality. Material Design sorts UI sound into layers. Primary UX sounds are the frequent ones, simple and understated: menu navigation, confirming a direct action, data input. Secondary UX sounds are less frequent and mark state changes or infrequent actions. Hero sounds are rare and prominent: they celebrate a significant action, welcome the user, or confirm a key moment of the product's purpose, and because of their prominence they are applied in consistent ways. Notifications sit between the two: shorter than hero sounds and crafted to survive being played many times. Ambient sound is a decorative layer that expresses emotion and personality. And silence is part of the design: Material says building silence into a UI is just as important as knowing when to apply sound, and sound is not usually suitable for UIs that require privacy, users who have requested no interruptions, or actions performed frequently. On Linux there is a native path for all of this: the freedesktop Sound Theme Specification lets apps trigger sounds by event name (dialog-error is the spec's own example) while the user's chosen sound theme supplies the actual audio.

**Why it feels good.** Sound reaches the user when their eyes are elsewhere. A confirmation tick lets them keep working without looking back to check, and a distinct success sound becomes part of an app's identity, the same way a color or a shape does. Material lists what sound design can do: associate a UI element with a specific sound, express emotion or personality, convey hierarchical structure, and provide sensory feedback. A well-chosen sound also marks a boundary: the work is done, the moment is over, you can move on.

**The numbers.** Material Design gives no durations, so this entry states the mechanism instead: frequent sounds stay short and simple enough to repeat without annoyance, notification sounds stay shorter than hero sounds, and hero sounds stay rare. The freedesktop spec gives the concrete formats: WAV/PCM 8 to 48 kHz, 8 or 16 bit, and OGG/Vorbis I, with WAV at 48 kHz stereo as the recommended uncompressed format and OGG/Vorbis as the recommended compressed one, and samples normalized to a suitable average replay level. The spec sorts sounds into four contexts: Alert (something with a major impact, such as dialog-error), Notification (the system or the current use changed state), Support (feedback on your actions, such as window opening and closing), and Game. Lookup falls back through a theme's parents to the freedesktop theme, so an app that names its sounds by event always gets something playable.

**Where it fits his apps.** Yahtzee: a dice roll rattle, a turn chime, a win flourish; games are a named context in the freedesktop spec, and sound is part of how a game feels. MIMIK: a capture confirmation click, the classic earcon, telling the user the shot landed without them looking. Code Forge: a soft completion chime when a long review finishes, so he can look away and come back when it is done. Fyrn: a finished chime when a model pull completes. LYNX SHARE: a render or export done sound, with care, since a DAW already makes sound: UI sounds there stay short, quiet, and out of the mix's way.

**Watch out.** Always provide a mute, with a visible toggle in settings, and never the only feedback: pair every sound with a visual change, since the user may have sound off or be somewhere quiet. Use decorative sound sparingly, limited to moments that reinforce the app's themes and unique voice, and limit its frequency to reduce fatigue (both straight from Material). Never put a sound on a frequently performed action; a sound that was charming the first time is the one that drives people away by the hundredth. Never stack sounds: one sound per moment, and let the more important one win. Keep volumes low and normalized, and test with the system muted: the app must still communicate everything visually. On his PC sounds are cheap (short WAV or OGG files, no GPU needed), which makes restraint a design choice, not a performance limit.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [008 Delight, done right](008-delight-done-right.md)
- [015 Accessibility presets](015-accessibility-presets.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)

## Sources

- Applying sound to UI, Material Design 2, Google (no date on page) — https://m2.material.io/design/sound/applying-sound-to-ui.html
- About sound, Material Design 2, Google (no date on page) — https://m2.material.io/design/sound/about-sound.html
- Sound Theme Specification, freedesktop.org, Version 0.2, June 4, 2008 — https://specifications.freedesktop.org/sound-theme/latest-single/
