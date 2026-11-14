# 038 — Comparison and diff views

> Entry 038 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Show what changed, side by side, so the eye does the work instead of the memory.*

**What it is.** Three shapes of the same idea, all for content that is not code. Side-by-side puts two versions next to each other so the eye can flick between them. A before/after slider overlays both versions in one frame with a draggable divider that reveals one over the other. A highlight-changes view shows one version with the differences marked in place. Google Docs does the third: open version history, pick a version, and the changes are shown against the current document, with a blue dot on the Last edit control when someone changed the file since you last looked. Figma does the timeline version: a sidebar of checkpoints you can preview, restore, duplicate, or link to. GitHub's pull request diff is the familiar reference for the pattern itself, with unified, split, rich, and source views of the same changes.

**Why it feels good.** Comparison is a perceptual task, not a navigation task. As one writeup of before/after sliders puts it, users do not want to flip between two tabs or open two windows; they want to drag one handle and watch a single image transform under their cursor. Anything that breaks that direct manipulation, even a slightly laggy handle or a slider that jumps on release, destroys the feeling of control that makes the pattern persuasive. The same logic runs through the document tools: Google Sheets hides unmodified rows by default in version history so the changes stand out, and Figma's restore saves your current state as a checkpoint first, so looking back never risks what you have now.

**The numbers.** Figma records a new checkpoint every 30 minutes, and users on the Starter plan or in Drafts can only reach 30 days of version history. Figma clips version titles longer than 25 characters and shows descriptions in full only when they are under 140 characters, which is a good ceiling for any version label of your own. Restoring a version in Figma adds two checkpoints (one saving the current state, one for the restored state), so restore is non-destructive by construction. For sliders, the practitioner guidance is to open near 90% on the before side rather than dead center at 50%, which shows half of each image and proves nothing; the user performs the reveal by dragging, and people trust conclusions they feel they reached on their own. GitHub offers four diff views for the same changes (unified, split, rich, source) and lets reviewers hide whitespace differences and filter files, which is the same principle as hiding unmodified rows: show only what changed.

**Where it fits his apps.** Pixel Forge: a before/after slider for filters and pixelize passes is the natural home for this, letting him drag across the image and judge the effect instead of toggling. Reblend: before/after on a material or lighting tweak. Data Pack Builder: compare two versions of a dataset pack, with added and removed examples highlighted, before committing to a rebuild. DUO: two models answering side by side is already a comparison view; this entry is the discipline for it (same prompt, same framing, differences visible without scrolling). ACR: compare two analysis runs of the same file, so a changed score is visible next to the run that produced it.

**Watch out.** An unlabeled slider forces the user to guess which side is which, and guessing introduces doubt about exactly the claim you are trying to prove, so keep small persistent Before and After labels anchored to their sides. Keep both versions the same dimensions: rescaling one side silently is the fastest way to look deceptive. Preload both images before showing the slider, or the first drag will stutter and undermine the effect. A slider only works when the change is legible; if the before/after has to explain itself with paragraphs of copy, the transformation is doing too many things at once. And never make restore destructive: save the current state first, the way Figma does, or nobody will dare use it.

## See also

- [017 See it before you commit](017-see-it-before-you-commit.md)
- [018 Scrub through time](018-scrub-through-time.md)
- [033 Forgiving UI](033-forgiving-ui.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [021 Glanceable surfaces](021-glanceable-surfaces.md)
- [037 Data visualization for non-analysts](037-data-visualization-for-non-analysts.md)

## Sources

- Find what's changed in a file, Google Docs Editors Help (undated help page) — https://support.google.com/docs/answer/190843
- View a file's version history, Figma Help Center (undated help page) — https://help.figma.com/hc/en-us/articles/360038006754-View-a-file-s-version-history
- About comparing branches in pull requests, GitHub Docs (undated help page) — https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-comparing-branches-in-pull-requests
- The Before-After Slider Is a Trust Interface, Not a Gallery, DEV Community, October 19, 2026 — https://dev.to/voorai/the-before-after-slider-is-a-trust-interface-not-a-gallery-5d1m
