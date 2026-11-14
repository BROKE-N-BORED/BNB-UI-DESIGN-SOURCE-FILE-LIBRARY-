# 035 — Tiered permission gates

> Entry 035 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The agent asks exactly as much as the risk deserves — never more, never less.*

**What it is.** Three tiers for agent actions, each visually distinct by
color *and* icon: reads need no prompt, writes ask once per session per
scope, destructive actions ask every time with no always-allow. The gate
is the human-in-the-loop layer: the checkpoint phase of a delegated
task, separate from the chat surface and the plan.

**Why it feels good.** Asking permission for everything trains users to
click Allow without reading; asking for nothing is how a branch nobody
wanted deleted gets deleted. Tiering keeps the interrupt rare enough
that it still gets read. And when the red gate appears, its different
shape breaks the muscle memory that always-allow builds.

**The numbers.** Setproduct's pattern library (behavior observed in
Cursor, Claude Code, Devin, Manus, ChatGPT Agent): read is grey with no
prompt; write is blue, ask once per session per scope, with "always
allow" available; destructive is red, ask every time, no always-allow.
The tier badge appears on the tool call card and in the dialog, and the
destructive dialog gets a different layout, not just a red color swap.
Batch approval: when more than three same-tier approvals would fire
within a minute, group them into one scrollable checklist (all checked
by default, one Approve button) with per-item consequences shown ("Edit
auth.ts +40, −12"); destructive items always surface alone. Stop pauses
rather than kills for tasks running longer than about 30 seconds. Label
the button Pause, because users hesitate to press Stop expecting to lose
work. Datarekha's worked approval policy approves an action if it is
irreversible, or external, or above a cost limit (their example limit is
$25). Never on model confidence. The approval boundary goes around a
meaningful bundle ("Send this email to Acme Analytics"), not a tool
call. Plan approval is not step approval: approve the bounded plan once,
and re-ask only if the plan changes materially. Batches cover only items
with the same action, permission, and risk, with counts and exceptions
shown ("Approve 18 read-only label changes? 16 match the rule. 2
conflict with existing labels.").

**Where it fits his apps.** **STELLA**: an agent acting on his behalf.
Reads free, sends and deletes gated. **DUO**: an agent drafting and
sending messages: sending is external, so it always gates. **ACR**: an
agent building data packs: writes gated once per session, publishing
gated every time. **GITDATA**: agent edits to datasets: deletes in the
destructive tier. **Data Pack Builder**: agent-generated packs: preview
the write before it lands.

**Watch out.** An approval rate near 100% means the prompts are too
frequent or too vague. Batch or re-tier, and measure correction and
review time, not approvals alone. Never combine an irreversible purchase
with routine updates behind one Approve all. Never report success when a
tool call timed out without confirmation. "Outcome unknown" beats a
fictional success. Do not use model confidence as the approval trigger;
use reversibility and consequence. A confidence percentage ("87%") is
not evidence. Show the assumption instead, so the user can verify it.

## See also

- [010 AI-native patterns](010-ai-native-patterns.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)
- [019 Optimistic UI](019-optimistic-ui.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)

## Sources

- 16 AI agent UI design patterns for plans, approvals and undo, Setproduct Blog — https://www.setproduct.com/blog/ai-agent-ui-design-patterns
- Designing human-agent interaction, datarekha — https://datarekha.com/agentic-ai/agentic-ux/
