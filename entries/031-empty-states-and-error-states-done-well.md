# 031 — Empty states and error states done well

> Entry 031 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The blank screen and the broken moment are where trust is won or lost.*

**What it is.** Two sides of the same coin: what the app shows when
there is nothing to show, and what it says when something goes wrong. A
good empty state never leaves a dead end. It explains what will appear
here, in one brief sentence, and offers one clear next action (Slack's
new channel suggests you "say hi to yourself"; Dropbox's empty folder
shows a big drop zone and an "Upload your first file" button; Pinterest
asks your interests at signup and pre-fills boards so the first screen
is already yours). A good error message follows Nielsen Norman Group's
three-part rule: highly visible, constructive communication, respect for
user effort: what went wrong in plain language, how to fix it, and your
work kept intact. Never "Something went wrong" with no path forward.

**Why it feels good.** Empty and broken moments are when users feel most
alone with a product: first launch, zero search results, a failed save.
A state that guides instead of shrugging turns anxiety into a first
step; an error that names the fix turns frustration into momentum. The
alternative is the user staring at "This folder is empty" or a bare
error code, guessing, and quietly leaving.

**The numbers.** NN/g's error-message rubric scores 12 guidelines across
3 dimensions (visibility, communication, efficiency) on a 1–4 scale, A
(4.0–3.3) to D (1.5 or less). Its "Excellent" bar: the message sits next
to the error's source; at least **3 redundant indicators** (icon +
border + text, never colour alone, since roughly **350 million people**
worldwide have a colour-vision deficiency); copy written at a
**7–8th-grade reading level** (Flesch-Kincaid) or lower; nonessential
animation kept to **100–500 ms**; the user's original input preserved so
they edit instead of retyping; and errors never shown prematurely.
Flagging a field before the user has finished is what NN/g calls a
hostile pattern. For empty states the mechanism is the checklist: one
sentence of explanation, one primary action, never show an empty state
while data is still loading (it flickers in and out and reads as a false
signal).

**Where it fits his apps.** **Qwkhnd**: an empty task list that says
what a first task looks like and offers one "+ Add task" button; a
failed sync that names the fix and offers Retry.
**MIMIK**: an empty capture library with a "Record your first clip"
action instead of a blank grid. **DUO**: a new conversation that
suggests a first message, and a send failure that keeps the draft.
**Data Pack Builder**: an empty pack with a template to start from.
**GITDATA**: zero search results that suggest broadening the query
instead of a blank table.

**Watch out.** Don't joke in error messages. Humour goes stale the third
time someone hits the same failure, and NN/g explicitly advises against
it. Don't use the word "invalid", "illegal", or "incorrect". Blame the
system, never the user. Don't clear the user's input when an error fires
(Craigslist scored 2.08/4 on NN/g's rubric, with its lowest marks on
input preservation — the form cleared the input, forcing a full restart).
Don't show a red error treatment for a mere warning. Reserve error
styling exclusively for errors or users learn to ignore it. And don't
design the empty state as an afterthought: the first-launch screen *is*
the onboarding.

## See also

- [008 Delight, done right](008-delight-done-right.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [020 Setup checklist](020-setup-checklist.md)

## Sources

- Error-Message Guidelines, Nielsen Norman Group, 2023-05-15 — https://www.nngroup.com/articles/error-message-guidelines/
- An Error Messages Scoring Rubric, Nielsen Norman Group, 2023-06-18 — https://www.nngroup.com/articles/error-messages-scoring-rubric/?lm=ui-copy&pt=article
- Empty states in UX done right: 4 inspiring examples, LogRocket Blog — https://blog.logrocket.com/ux-design/empty-states-ux-examples/
- Material Design 3 feedback patterns, m3-feedback skill doc, snapshot 2026-06-06 — https://github.com/ichintansoni/skills-master/blob/HEAD/skills/android/design/patterns/m3-feedback/SKILL.md
