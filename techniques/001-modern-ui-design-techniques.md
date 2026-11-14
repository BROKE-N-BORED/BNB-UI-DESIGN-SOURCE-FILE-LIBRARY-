# Modern UI Design Techniques — Source File

> Library file 001 — added 2026-11-13. Seed file of the BNB UI Design Source File Library.

Researched and gathered 2026-11-13 by Arlo, at Joshua's request: modern UI design
techniques that are NOT typical, run-of-the-mill patterns, but that work, and are
simple and satisfying to use.

Companion to `design-rules.md`. The rules say what must be true. This file is the
techniques drawer: things to pull from when a build needs a better way to feel.
Nothing here overrides the rules. Every technique below was picked because it
passes the philosophy test in Part 1 of the rules: complex underneath, simple on
top, like a toy a child could use.

## How to use this file

- Do NOT use all of these in one app. Pick two or three per app, the ones that
  fit what the app actually does. (The wavespace roundup says the same: you need
  the two or three that suit your users, not all eight.)
- Every technique here must still pass the toy test: if a child couldn't pick it
  up and use it, it doesn't go in, no matter how clever it is.
- Motion has a budget. Functional animation stays under 300 ms. Anything longer
  feels slow, not delightful. Respect reduced-motion settings.
- Qt note: his apps are Qt. Qt has no spring physics built in, but
  `QPropertyAnimation` with `QEasingCurve::OutBack` (overshoot) and `OutElastic`
  (bounce) covers most of what this file asks for. Springs need a small custom
  animator for true velocity-aware motion; OutBack is the cheap version that
  already feels good.

---

## 1. Micro-interactions — the small moments that make it feel alive

**What it is.** The tiny response to a tiny action: a button that dips when
pressed, a checkmark that draws itself when a task finishes, a field that shakes
gently when the input is wrong, a toggle that slides home. Each one follows four
parts: Trigger (what the user did), Rules (what happens), Feedback (what the
user sees), Loops and Modes (what changes afterwards).

**Why it feels good.** A button that doesn't respond feels broken. A form that
saves without confirmation feels uncertain. Users don't consciously notice good
micro-interactions; they notice their absence. Research cited across the 2026
roundups puts satisfaction up 15 to 25 percent from micro-interactions alone,
with no change to core functionality.

**The numbers.**
- Micro feedback (press, ripple, hover): 100 to 150 ms.
- Small UI actions: 150 to 250 ms.
- Context changes (a panel opening, a view switching): 250 to 400 ms.
- Ease-out for things entering, ease-in for things leaving, ease-in-out for
  loops. Animate transform and opacity, never layout properties, or the frame
  rate dies.

**The premium patterns, measured.**
- Button press: scale to 0.97 (3 percent smaller) over 150 ms. Smaller than
  2 percent is invisible; bigger than 5 percent looks cartoonish.
- Card hover: lift 4 px, over 200 ms, ease-out. Enough to feel tangible,
  not enough to look like a toy popping off the screen.
- Focus ring: a soft glow at about 10 percent opacity, colored border plus
  ring. Visible enough to show focus, quiet enough not to shout.

**Where it fits his apps.** Everywhere, but especially Forge (chat send,
approval buttons, tool-call status), DUO (relay send, model switch), STELLA
(training start, the moment a run finishes). The finish moment matters most:
a small celebration when a long job completes turns waiting into payoff.

**Watch out.** Every animation needs a purpose. If you can't say why it helps,
remove it. Never animate to cover up slowness; fix the slowness.

## 2. Spring physics motion — things that feel like they have weight

**What it is.** Motion driven by a simulated spring instead of a fixed timer.
A spring has stiffness (how fast it moves) and damping (how fast the bounce
settles). When you flick a card, it overshoots slightly and settles, the way
a real object would. The key property: a spring is velocity-aware. A fast
fling settles fast; a calm tap settles slow. The animation energy matches the
gesture energy automatically.

**Why it feels good.** Our brains have a lifetime of handling physical objects.
A ball bounces smaller and smaller until it stops. A rubber band snaps and
overshoots. Spring motion matches that expectation, so it reads as real.
Fixed easing curves feel mechanical by comparison, and CSS-style easing can't
overshoot at all, which is exactly the part that feels tactile.

**The numbers.**
- A snappy toggle: stiffness around 500, damping around 30. Quick movement,
  slight overshoot, fast settle.
- Springs are for motion the USER causes: taps, drags, swipes, pull-to-refresh.
  For things that happen on their own (a loading fade), plain easing is better.
- Feed the release velocity into the spring. A spring that restarts from zero
  when you let go of a drag feels disconnected from your hand.
- Transitions must be interruptible: if the user grabs something mid-flight,
  it retargets smoothly instead of finishing the old animation first.

**The earned rule (from Material 3 Expressive).** Expressive spring motion is
earned, not defaulted to. Springs belong on content and interactive surfaces
that reward attention: sheets sliding up, a button expanding into a menu,
hero reveals. Standard motion belongs on chrome and utility controls. Two
schemes coexist; don't spring everything.

**Where it fits his apps.** Reblend (dragging objects, panels), Pixel Forge
(strip reordering, canvas tools), Yahtzee (dice, cards), Forge's deck and
palette. Anywhere the user grabs something and lets go.

**In Qt.** `QEasingCurve::OutBack` gives the overshoot; `OutElastic` gives the
bounce. For true velocity-aware springs, write a small spring animator that
integrates stiffness and damping per frame.

## 3. Calm technology — the interface that knows when to shut up

**What it is.** From Xerox PARC, 1995 (Mark Weiser and John Seely Brown):
"The most profound technologies are those that disappear." Calm technology
informs without demanding focus. It works across three zones of attention:
center (focal, conscious), periphery (aware without looking), background
(fully automatic, zero attention unless something needs you).

**Why it feels good.** Most software has one volume setting: loud. Calm design
has the full spectrum: a whisper, a nudge, a glow in the corner, and only a
firm tap on the shoulder when it truly matters. The classic example is the
Dangling String at PARC: an eight-foot string that swayed gently with network
traffic and whirled when it spiked. You could read the whole network at a
glance, from across the room, without looking at a screen.

**The principles (Amber Case's eight, condensed).**
- Require the minimum attention necessary to deliver the value.
- Communicate through ambient channels first: peripheral vision, soft light,
  gentle sound, haptic rhythm. Escalate to focal attention only when needed.
- Default to silent. Earn the right to interrupt.
- Bring things forward gracefully when they become relevant; let them recede
  quietly when they don't.
- Use the minimum technology necessary. Don't over-engineer.
- The goal is not invisibility, it's pass-through: a good tool disappears
  through use, like a bicycle or a pen. You never have to relearn it.

**Where it fits his apps.** This is the closest thing in the research to his
own philosophy, and it should shape all of them. Forge's status: an ember dot
and a quiet status line, not a modal. STELLA's training: live graphs you can
glance at, not a form you must watch. Long jobs: a status chip that changes
state, not a popup. The app should be a good roommate, not a demanding
houseguest.

**Watch out.** The discoverability paradox: the better an interface disappears,
the harder it is to discover what it can do. Calm apps still need a way to
surface their capabilities when the user goes looking. Too subtle, and people
miss important information entirely.

## 4. Just-in-time GUI — invisible until the moment it matters

**What it is.** The interface is invisible by default and surfaces only when
context demands it, then disappears when its purpose is served. Coined by
Andrew Sims (Signal Path). Related to calm technology, but stricter: zero
inventory. No unused features sitting in the interface; show what's needed,
discard the rest.

**Why it feels good.** The screen never shows you something you don't need
right now. Every control you see is relevant to this exact moment. That is
the toy bar, enforced by the system instead of by willpower.

**The calm test.** Before adding any visible UI, ask: can this be done without
a screen at all? Can it be a quiet indicator instead of a control? Can it
appear only when the user is in the situation where it matters?

**Where it fits his apps.** Forge's approval flow (the approval appears when a
tool needs it, not before). STELLA's settings (they don't exist on screen at
all until the backend can't decide something itself). ACR's controls (the
learning rate lives in its own window, behind the menu, not on the main
screen). This is U35 and U36 from the rules, as a named technique.

**Watch out.** Context has to be accurate. A just-in-time UI that guesses the
context wrong hides the thing the user needs. When in doubt, the menu bar is
the fallback: everything is still reachable, just not on screen.

## 5. Bento grids — size is the hierarchy

**What it is.** Named after the Japanese lunch box. Instead of one long column,
the screen breaks into neat blocks of different sizes. A big block for the
main point, smaller blocks around it for supporting details. Every tile is
self-contained and has exactly one job. The asymmetry is the point: bigger
tile, more important content. The layout itself tells you where to look
first, no labels needed.

**Why it feels good.** Each tile is one idea, so your brain never has to hold
the whole page at once. You scan in seconds instead of reading linearly.
Users form a first impression of a dashboard's usefulness in under six
seconds, and spatial weight pre-answers "what matters here" before a word is
read. On a phone, the tiles restack into a single column ordered by priority,
not by their original position, so the hierarchy survives any screen.

**The numbers.**
- Grid: 3 to 5 columns. One hero tile per layout (4 to 6 columns wide,
  2 rows tall).
- Gaps: uniform, 16 to 24 px on desktop, 8 to 16 px on smaller screens.
- Corners: rounded, 12 to 24 px radius. Square corners read as a table.
- 5 to 10 cells per layout. More than that and it stops being scannable.

**Where it fits his apps.** STELLA's main screen (one big tile: pick a model,
pick a job, press go; small tiles: RAM, speed, progress). Forge's deck.
GITDATA's results. Any dashboard or home screen that has to show ten things
at once without shouting.

**Watch out.** Bento fails when every box is the same size, or when the
hierarchy is unclear. Symmetric grids look like spreadsheets. If the sizes
don't mean something, it's just a wall of boxes.

## 6. Neo-skeuomorphism (Soft UI) — controls you want to press

**What it is.** The 2024 to 2026 revival of skeuomorphism, but grown up: not
stitched leather and wood grain, but soft inner and outer shadows, believable
light, and controls that look physically pressable. A button is mostly flat,
but a gentle shadow and a soft animation give it weight. A slider moves like
a real knob. Two soft shadows, one light from above, one dark below, do most
of the work. One consistent light source across the whole interface.

**Why it feels good.** After a decade of flat design, people crave digital
texture. A control that looks pressable tells you how to use it without a
manual: that is affordance, the oldest idea in design. When the app maps to a
physical object, a musician who knows the original instrument has zero
learning curve.

**Where it fits his apps.** Music and audio first: LYNX SHARE (the DAW),
Reblend's animation controls, any synth or mixer surface. Knobs, dials, VU
meters, faders. Also any control where the physical metaphor is the point:
a volume dial that rotates with inertia, a toggle that feels like a switch.

**Watch out.** Rotational-drag knobs are hard on touchscreens and brutal for
users with tremor or limited dexterity. If you ship a knob, also ship a plain
numeric input or slider bound to the same value. And keep a real 1 px border
on buttons: high-contrast modes strip shadows and gradients, and without a
border the button stops reading as a button.

## 7. Liquid Glass and glassmorphism 2.0 — depth as a navigation cue

**What it is.** Frosted, translucent panels that bend light, with refraction
and specular highlights. Apple's Liquid Glass (iOS 26, 2025) is the anchor
example: the material moves like a light liquid and responds to touch.
The 2026 version is smarter than the first glassmorphism wave: frosted panels
with purpose, not decoration.

**Why it feels good.** Depth becomes a functional signal. A floating panel is
obviously above the content beneath it; a glass sheet that slides over the
screen obviously belongs to a different layer. The eye reads the hierarchy
from the material, not from labels. It also feels alive: light moves through
it as you interact.

**Where it fits his apps.** Forge already lives here: Future 3 Dark Glass
Minimal. The technique to borrow is restraint: glass for floating layers
(palette, deck, popups), solid for the working surface. Glass everywhere
turns to fog.

**Watch out.** Clear panels hurt readability, and that is a real problem for
low vision. Keep text on solid-enough backgrounds, and never put small text
over a busy background through glass.

## 8. Delight, done right — personality in the small places

**What it is.** Delight is not cute illustrations everywhere. It is moments
where the interface exceeds expectations in small, surprising ways: an empty
state that makes you smile instead of feel frustrated, an error message that
feels helpful instead of scolding, a loading state that entertains instead of
annoying, a small celebration when a task finishes.

**Why it feels good.** The boring moments are where most apps give up. A good
empty state teaches you what to do next. A good error message tells you how
to fix it. A small celebration when a long job completes turns waiting into
payoff. These are the moments users remember and describe to other people.

**The rules.**
- Functional animations under 300 ms. Longer feels slow, not delightful.
- Personality in the small places, not the big ones. The empty state, the
  error, the completion moment. Not the main workflow.
- A checkmark that draws itself, a toggle that settles with a bounce, a
  button that dips on press: all delight, all under 200 ms.

**Where it fits his apps.** STELLA's empty project list (what to do first, in
plain words). Forge's error states (what went wrong, what to do). The moment
a STELLA training run finishes, a Data Pack Builder pack is written, a Fyrn
model finishes pulling. Those are the moments to celebrate, quietly.

## 9. Shape morphing and continuity — things that change shape, not screens

**What it is.** A button expands into a full-screen menu. A card grows into a
detail view. A small control morphs into the thing it controls. The element
keeps its identity through the transition, so the user never loses their
place. The focal point stays put; the shape changes around it.

**Why it feels good.** Screen switches are jarring: everything disappears and
something new appears, and the brain has to re-orient. A morph says "this
thing you were looking at IS the next screen." It reduces the mental effort
of figuring out where one screen ends and another begins, because there was
no switch, only a change of shape.

**Where it fits his apps.** Forge's mode windows (a rail icon expands into its
window). DUO's model picker. STELLA's job picker (pick a job, the picker
becomes the job). Anywhere a small control opens a big surface.

**Watch out.** Morphs need to be fast (under 400 ms) and interruptible. A slow
morph that can't be cancelled is worse than a plain screen switch.

## 10. AI-native patterns — the interface for talking to a model

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

## 11. Skeleton screens and honest loading — never a dead screen

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

## 12. Progressive disclosure — the minimum now, the rest when asked

**What it is.** Show only what the user needs for this step. The rest is one
tap away, in a collapsible section, a second window, or a menu. Related to
just-in-time GUI, but simpler: it is about forms and settings, not about the
whole interface disappearing.

**Why it feels good.** A screen with three choices is a toy. A screen with
thirty choices is a cockpit. The work is the same underneath; the difference
is how much the user has to hold in their head at once.

**Where it fits his apps.** Everywhere, and it is already U21 in the rules
(ask for the minimum up front). STELLA's new profile form (pick a model only).
Fyrn's settings (the models folder, nothing else, until you need more). The
Data Pack Builder (one plain-words request, presets as chips).

---

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
4. **Does it earn its place?** Every animation, every shadow, every morph
   should help the user understand, feel, or enjoy something. Delight and
   personality count as earning a place. What fails is a technique that adds
   noise without helping or pleasing anyone. (Corrected 2026-11-13: the old
   wording here, 'No decoration for its own sake,' was Arlo's own note, not
   one of Joshua's rules. Creativity is wanted.)

## Quick map: techniques by project

- **Code Forge:** micro-interactions, calm technology, AI-native patterns,
  shape morphing (rail to window), skeleton screens for history.
- **STELLA:** bento grid (main screen), calm technology (glanceable training
  graphs), just-in-time GUI (settings that don't exist until needed), delight
  (the finish moment).
- **DUO:** micro-interactions, spring physics (relay send, model switch),
  skeleton screens for the model list.
- **Fyrn:** calm technology (quiet RAM and speed indicators), honest loading
  (pull progress with real numbers), bento grid (model list with fit).
- **Data Pack Builder:** bento grid (results), trust cues (source next to
  every pack), honest loading (live counts while it reads).
- **ACR:** calm technology (the trace log as an ambient display), delight
  (the resonance moment), just-in-time GUI (controls in their own window).
- **Pixel Forge:** spring physics (drag and reorder), shape morphing
  (tool to canvas), micro-interactions (brush and layer feedback).
- **Reblend:** neo-skeuomorphism (dials, sliders, tactile controls), spring
  physics (dragging objects), shape morphing (panel to workspace).
- **MIMIK:** calm technology (quiet status), micro-interactions (capture
  feedback).
- **Yahtzee:** spring physics (dice, cards), delight (win moments),
  neo-skeuomorphism (the dice themselves).
- **LYNX SHARE (DAW):** neo-skeuomorphism first (knobs, faders, VU meters),
  spring physics (fader movement), calm technology (the mix runs, the UI
  stays quiet).
- **GITDATA:** bento grid (results), skeleton screens (search loading),
  micro-interactions (save, filter).
- **Qwkhnd:** progressive disclosure (one request, then the dictionary),
  honest loading (rebuild progress).

---

## Sources

- Microinteractions in 2026 — https://www.maviklabs.com/blog/microinteractions-2026/
- 14 Best Micro-interaction Examples (2026) — https://www.designstudiouiux.com/blog/micro-interactions-examples/
- UI Micro-Interactions: Premium UX Patterns 2026 — https://rune.codes/hub/tech-trends/ui-micro-interactions-the-details-that-make-apps-feel-premium
- Designing for Delight — https://medium.com/@bammiecreations/designing-for-delight-when-and-how-to-add-personality-to-your-interfaces-39af63c3ade5
- 8 UI Design Trends in 2026 — https://www.wavespace.agency/blog/ui-design-trends
- Five UI Patterns That Look Poised to Define 2026 — https://dev.to/sissie_hensley_568968e0fb/five-ui-patterns-that-look-poised-to-define-2026-59k3
- What is Calm Computing? — https://ixdf.org/literature/topics/calm-computing
- The Ambient Revolution: Why Calm Technology Matters More in the Age of AI — https://edges.ideo.com/posts/the-ambient-revolution-why-calm-technology-matters-more-in-the-age-of-ai
- Calm Technology: Designing Digital Products That Enhance Rather Than Overwhelm — https://eidosdesign.substack.com/p/calm-technology-design
- Ambient Computing and Calm Technology (skill) — https://github.com/xgodev/ux-ui-mastery/blob/HEAD/skills/ambient-calm-zero-ui/SKILL.md
- Just-in-Time GUI Expert (skill) — https://github.com/diegosouzapw/awesome-omni-skill/blob/HEAD/skills/design/jit-gui-expert/SKILL.md
- Understanding Spring Animations in SwiftUI — https://www.createwithswift.com/understanding-spring-animations-in-swiftui/
- Material 3 Expressive (skill) — https://github.com/ichintansoni/skills-master/blob/HEAD/skills/android/design/technologies/m3-expressive/SKILL.md
- Material Design Expressive: The Future of UI/UX in 2026 — https://zignuts.com/blog/google-material-design-expressive
- Bento Grid Dashboard Design: Complete Guide 2026 — https://www.orbix.studio/blogs/bento-grid-dashboard-design-aesthetics
- Bento Grid Web Design — https://webpo.space/blog/bento-grid-web-design
- Why Skeuomorphism Is Making a Comeback in 2025 — https://pixite.com.au/the-resurgence-of-skeuomorphism/
- Skeuomorphism: Definition, CSS Recipe, 2026 Revival — https://superdesign.dev/styles/skeuomorphism
- Neo-Skeuomorphism (Cusps Trend Guide) — https://www.cusps.net/guide/skeu
- Skeuomorphism 2026: The Return of Digital Leather and Wood — https://techsnostalgia.com/skeuomorphism-vs-flat-design-2026-comeback/
