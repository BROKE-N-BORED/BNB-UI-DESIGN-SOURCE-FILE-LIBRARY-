# Verdicts

The feedback loop. An entry earns its place when it gets used in a real
build — and what happens next belongs here, so the library hears back from
real apps instead of collecting wishes.

## How to record a verdict

One entry per use, newest first:

- **Date:** when the build shipped or the verdict was reached.
- **App:** which Broke n' Bored app used it.
- **Entry:** the entry number and name, linked.
- **What happened:** what was built with it, in plain words.
- **Verdict:** worked, or didn't — and why. What to do differently next time.

## Verdicts

### OLLAMA SYSTEM TEST v11-v15 — 2026-11-14

**App:** OLLAMA SYSTEM TEST, a native Qt/PySide6 desktop app on an 8 GB
no-GPU Linux Mint PC. **Build:** the UI redesign, versions 11 to 15
(redesign tasks R1-R25). **Library head at build time:** Drop 5, 60
entries. Sixteen entries used, nine read and deliberately not used.

#### Used

**[017 See it before you commit](entries/017-see-it-before-you-commit.md)
(R11, v13) — worked as written.** The run preview (what will run, how
many steps, an upper time estimate, the cost) replaced a bare cost
confirmation dialog, and the "Adjust" path is the part that earns its
place: the preview is the last chance to catch a wrong pick before a
90-minute run. Two things the entry does not say, both learned here: the
time estimate must be labelled an upper estimate ("at most about X"),
because a precise-looking estimate reads as a promise and the run usually
finishes sooner; and the preview and the worker must share one step
counter, or the preview's step count and the run's step count drift apart
(here both call one module function).

**[011 Skeleton screens and honest loading](entries/011-skeleton-screens-and-honest-loading.md)
(R12, R19, v13/v15) — worked as written, twice.** The run progress line
shows the real step count, the elapsed time, and an ETA from the real
rate so far ("22 of 22 steps done, took 26s"), and the pull progress
shows the real download speed and time left from the last 10 seconds of
samples. The entry's "never a fake progress bar" held up: the one place a
fake would have been tempting (a pull with no rate yet) reads "estimating
time left" instead, and nobody missed the bar. Watch: an ETA needs at
least two data points before it means anything. The first step of a run
has no rate yet, so the line says so rather than inventing one.

**[003 Calm technology](entries/003-calm-technology.md),
[021 Glanceable surfaces](entries/021-glanceable-surfaces.md),
[008 Delight, done right](entries/008-delight-done-right.md)
(R13, v13) — worked as a set.** A long run ends with a small status chip
(Ready / Running / Done) and one finish line naming the best model, its
score, and its speed. No popup, no sound, no modal. The chip is the
ambient channel the entries describe; the finish line is the one fact
worth surfacing. The delight is small on purpose: a tick mark and a
200 ms fade on the finish line, both skipped when Reduce motion is on.
What did not survive contact with the build: nothing. But the entries'
"escalate only when needed" needed a decision the entries do not make
for you, which is what counts as needing escalation here. A failed run
does not escalate (the chip says "Stopped" and the table shows the
failure); only Ollama dying mid-run gets its own chip state, because
that is the one failure the user must act on outside the app.

**[005 Bento grids](entries/005-bento-grids.md) (R14, v14) — worked, with
one adaptation.** Five tiles (hero latest score plus best score, average
speed, strongest, weakest) read at a glance exactly as the entry
promises, and the entry's "size is hierarchy" held: the hero tile spans
two columns and nothing else competes with it. The adaptation: the
entry's grid assumes the tiles are the whole surface, but here the tiles
sit beside a full profile text and above two charts, so the tile row had
to be short (five cells, not the entry's up-to-ten) or the page felt
top-heavy. The entry's 16 px gaps and 12 px corner radius were used as
written. One thing worth adding to the entry: when tiles, charts, and
text all describe the same run, they must all read one shared numbers
object, or they will disagree with each other eventually. Here one
function returns the numbers and all three views read it.

**[037 Data visualization for non-analysts](entries/037-data-visualization-for-non-analysts.md)
(R16, v14) — worked as written, and the entry's strictest rules earned
their keep.** One chart, one message, with the takeaway as the title
("Strongest: Math 80%. Weakest: Coding 40%."). The title is the feature,
not the chart. Bars for comparing amounts, lines for change over time,
axis fixed at 0, direct value labels, no legends, no pie. The entry's
"color is never the only carrier" mattered in practice: the grouped bars
on Compare carry a caption naming which bar is which model, because the
two bar colors alone would not survive a screenshot or a color-blind
reader. Watch: the entry assumes a charting library; painted by hand in
Qt, the fiddly part is the grid labels (nice round steps, about four
lines) and the date labels (first/middle/last, all when there are five
or fewer points). Both are small functions now, but they were the only
real work in the charts.

**[020 Setup checklist](entries/020-setup-checklist.md) (R7, v12) —
worked as written, including the parts that feel like over-caution until
you build them.** Three steps on the home screen, the first two honestly
ticked when they are true ("Ollama is running", "At least one model is
pulled"), never pre-ticked when they are not, dismissible, gone forever
when done. The honest ticking is load-bearing: the checklist checks the
real state (Ollama reachable, models listed), so a tick means something.
The entry's "first step already ticked" only works because the first
step is genuinely the easiest true thing; a checklist whose first step
is a chore teaches the user to dismiss the whole panel. One addition
worth recording: the checklist is also where the Bigger text preset
lives in v15 (R21), one tap, because the first boot is the one moment
the user most needs it, and it goes away with the checklist, which is
the right lifetime for a first-boot offer.

**[015 Accessibility presets](entries/015-accessibility-presets.md)
(R21, v15) — worked, and the entry's "each setting still adjustable
after" was the part that made it shippable.** Bigger text is one tap
(startup size plus three points), but the size spin stays in Settings
and the preset is just a shortcut to a value, not a mode, so a user who
wants plus two, or plus five, is never fighting the preset. Correction
carried back into the entry: a settings dialog that grows a section can
overflow its fixed size. Ours did at 12 pt text. Explanation labels
overlapped each other and the Save button. The fix is a scroll area with
the buttons below it, always visible.

**[023 Focus-first navigation](entries/023-focus-first-navigation.md)
(R22, v15) — worked, with one platform correction carried back into the
entry.** The focus ring is a 2 px solid border, visible in both themes;
Tab moves in visual order per tab; focus is remembered per tab and
restored when you come back. The correction: the entry's ring guidance
assumes `outline` works, and in this PySide6 build `outline` renders
nothing at all (probed: 0 pixels). The ring must be a `border` on
`:focus`. That is a Qt-specific fact, but the entry's "focus must be
unmistakable" is exactly what caught it. The ring was specified, probed,
and found invisible, which is the entry working as a checklist. Second
note, same entry: focus memory must be tested with the window's own
focus widget, not the application's, because under a test harness with
no window manager the application-level focus reads empty even when the
window-local focus is correct. On a real desktop with a window manager,
both agree.

**[018 Scrub through time](entries/018-scrub-through-time.md) (R20, v15)
— worked, with the entry's thumbnail idea dropped.** The slider walks a
model's runs newest to oldest with a readout naming the date, template,
score, and speed. Ten runs browsable in the time one open takes, as the
task required. The entry wants hover-scrub thumbnails; a run has no
thumbnail, and the readout line is the honest equivalent. It is the same
information a thumbnail would carry (which run is this, how did it do),
in text. The entry's "double-click loads at the hovered frame" became
"click opens the run": scrubbing moves the highlight and the readout
only, never the detail view, so browsing stays cheap and opening stays
deliberate. Hovering a run previews the same readout line as a tooltip.
The adaptation to record: when the item has no image, the readout line
IS the thumbnail.

**[022 Per-context profiles](entries/022-per-context-profiles.md) (R18,
v14) — worked, quietly.** Each model remembers its usual templates: tick
a model and its usual set ticks with it, with a label saying so ("Usual
templates for fake-smart:2b."). The entry's "settings follow the job
automatically and silently, with a visible label of which profile is
active" is exactly the design. The label is what keeps the silence
honest. What the entry does not spell out: a saved set must only apply
to templates that are currently enabled (a greyed-out template must not
get ticked by a stale set), and a hand-changed tick must clear the
label, or the label lies about what is picked. Both are in the build.
The sets save only when a run is actually accepted. A cancelled preview
saves nothing, because a preview the user backed out of is not a choice.

**[004 Just-in-time GUI](entries/004-just-in-time-gui.md) (R1, R17, R18,
v12/v14) — worked as the quiet rule behind three rebuilds.** The
Benchmark tab split into Run setup / Run / Models shows only the
controls for the current job; the Providers tab rebuilt into Connection
and Models sections shows each field with its explanation underneath,
and the fetched-model pick-list appears only after a successful
connection test; Settings holds the four things that are set once and
rarely touched. The entry's value here was as a veto: every time a
control threatened to live on a tab where it is never used (the pull box
on the Run tab, the budget spin on the Models tab), the entry said no.
No adaptation needed. But the entry reads as a layout rule and it is
really a scope rule: what belongs on this screen is decided by the job,
not by the feature list.

**[012 Progressive disclosure](entries/012-progressive-disclosure.md)
(R1, R17, v12/v14) — worked as the other half of 004.** The minimum now,
the rest one tap away: the run preview hides the cost breakdown until
there is a provider model to price; the provider form hides the fetched
model list until the connection works; the template list shows names and
task counts, with the full task list one Preview click away. The entry's
"one tap away" held as a hard limit. Nothing in the redesign is more
than one click from where it is needed. No adaptation, no failure.

**[001 Micro-interactions](entries/001-micro-interactions.md),
[014 Teach by playing](entries/014-teach-by-playing.md) (R23, v15) —
worked, in the small.** Every tick says what is picked now ("1 model, 2
templates picked.") in the status line. The tick feedback is a sentence,
not an animation, because the thing the user needs to know is the count,
not that something moved. The finish moment has the tick and the 200 ms
fade (see 008). Teach by playing is the first-run hint ("New here? Ask
one model one question first: Models tab, Try one model.") plus the
checklist: the first run teaches the app by doing it, with no tutorial
text. What did not work as the entries describe it: 001's button-press
scale and card-hover lift were not built. Qt widgets do not have a cheap
transform animation path the way the web does, and a hand-rolled
geometry animation on every button would cost frames on this PC for no
information. The entries' timing numbers (100-150 ms feedback, under
300 ms for functional animation) were kept as the budget for the one
animation that exists (the 200 ms finish fade). The honest verdict: on a
Qt desktop app, the entries' feedback timing transfers, but their
transform vocabulary mostly does not. The feedback here is text and
state, not motion.

#### Read and deliberately not used

These were read in full during the audit and rejected for OST with
reasons, not overlooked. They may fit other apps; the rejection is
OST-specific.

- [002 Spring physics motion](entries/002-spring-physics-motion.md),
  [006 Neo-skeuomorphism (Soft UI)](entries/006-neo-skeuomorphism.md),
  [007 Liquid Glass and glassmorphism 2.0](entries/007-liquid-glass.md),
  [009 Shape morphing and continuity](entries/009-shape-morphing-and-continuity.md):
  decoration for a work tool. OST is a benchmark runner; its personality
  lives in one finish line, not in its surfaces. (The creativity
  correction stands. This is about fit for this app, not a rule against
  decoration.)
- [013 Diegetic UI](entries/013-diegetic-ui.md),
  [016 Pie menus](entries/016-pie-menus.md),
  [024 Clip launcher](entries/024-clip-launcher.md): wrong app shape.
  OST has no world to be diegetic in, no radial command set, and no clip
  grid.
- [010 AI-native patterns](entries/010-ai-native-patterns.md): OST has
  no chat UI. The try-it box (R24) is one question and one answer, not a
  conversation.
- [019 Optimistic UI](entries/019-optimistic-ui.md): rejected on
  principle for this app. A run must never look done before it is. A
  benchmark that reports early is a benchmark that lies. Optimism belongs
  where the outcome is near-certain and the cost of being wrong is a
  redraw; here the cost is a false score.

#### Cross-cutting notes

- Every entry that touches a list should say whether the list is
  checkable. This PySide6 build sets ItemIsUserCheckable on a bare list
  item by default, so a read-only list sprouts a checkbox the first time
  the user presses Space on it. OST fixed its installed-models list; the
  history, profile, and provider lists still carry the quirk (out of
  scope for the redesign, no task exists). A library note would have
  caught all of them at audit time.
- Every entry that touches a modal dialog should say how the dialog is
  driven in a test. In this sandbox a QTimer does not fire while a modal
  dialog's exec() runs, so a timer-driven test harness hangs at the first
  modal; a thread-driven harness (queued signals are delivered inside the
  modal loop) is what works. That is a testing note, not a design note,
  but three versions' GUI drives hit it.
- The entries' numbers held up wherever they were used as written (16 px
  gaps, 12 px radius, 2 px focus ring, 200 ms fade, 3-point text bump).
  The numbers that needed adapting were all about density (five tiles,
  not ten) or platform (`border`, not `outline`). Nothing in the library
  was wrong; the adaptations were all about this app's shape and this
  toolkit's quirks.
