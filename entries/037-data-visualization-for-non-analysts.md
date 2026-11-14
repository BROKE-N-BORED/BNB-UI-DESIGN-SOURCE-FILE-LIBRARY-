# 037 — Data visualization for non-analysts

> Entry 037 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*One chart, one message, readable at a glance by someone who never asked for a chart.*

**What it is.** Charts in his apps are for a person checking something, not an analyst studying data. ACR shows a resonance trace, Fyrn shows a download filling up, Data Pack Builder shows what a dataset is made of. The technique is to design each chart around one question it answers, pick the mark that answers that question (bars for comparing amounts, lines for change over time), and strip everything that does not help answer it. Apple's WWDC22 chart talk puts it as a rule: an effective chart focuses on a few key pieces of information, and you design charts with intention.

**Why it feels good.** The eye reads length and 2D position before attention even engages, a process Nielsen Norman Group calls preattentive processing. A bar twice as tall reads as twice as much without thinking, and a dip in a line chart is visible the instant you look. A chart with a plain-language title that states the takeaway tells you the answer before you read a single axis: Apple's example rewrites a chart title as "Total Sales: 1,234 Pancakes" so the main number is front and center. That is the whole trick. The chart does the reading so the person does not have to.

**The numbers.** Apple's WWDC22 talk works a real example through and lands on concrete values: around 4 horizontal grid lines for a 30-day sales chart, where 7 felt overwhelming and 2 were too few to estimate values in the middle; grid labels in intuitive steps (multiples of 20 for values, 7-day steps for time, which gives 5 grid lines across 30 days); and a bar chart's vertical axis fixed at 0 at the bottom, so a bar twice as tall really means twice as much. The same talk limits a chart to three priorities at most (pattern, range, and values in its example). Nielsen Norman Group adds that up to 4.5% of the general population has some form of color blindness (around 8% of men versus 0.5% of women), which is why color must never be the only thing carrying meaning. Tufte's data-ink ratio (1983) gives the test for every element: if removing it changes nothing about the message, it is chartjunk and it goes.

**Where it fits his apps.** ACR: the resonance trace over steps is already a chart, and this entry is how to make it readable, with a plain takeaway title and a 0-based axis instead of a bare line. Fyrn: download progress and model sizes as simple bars, one bar per model, longest bar obvious at a glance. Data Pack Builder: dataset composition (how many examples per category) as a sorted bar chart with direct labels, no legend to flick back to. GITDATA: dataset size and coverage overviews when browsing search results, where a glance has to separate a big dataset from a small one.

**Watch out.** Pie charts, donut charts, and gauges rely on area and angle, which people judge poorly: Nielsen Norman Group notes we can see that one area is bigger than another but not how much bigger, and donut charts make it worse by shrinking each slice. Never put a 2-variable chart in 3D; it distorts the shapes and makes it hard to tell which value the top of a bar represents. Legends force the eye to bounce between the chart and the key, so label series directly on the lines or bars instead. Color alone fails colorblind readers, so pair it with shape or position (circles versus squares on two lines, as Apple does). And test with real messy data early: Apple's talk shows point marks looking great on smooth ideal data and unreadable on realistic data. Default chart styles from spreadsheet apps are generic and cluttered, built to look interesting rather than to answer a question.

## See also

- [021 Glanceable surfaces](021-glanceable-surfaces.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [015 Accessibility presets](015-accessibility-presets.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [038 Comparison and diff views](038-comparison-and-diff-views.md)

## Sources

- Design an effective chart, WWDC22 session 110340, Apple, June 2022 (full transcript via mirror; canonical page developer.apple.com/videos/play/wwdc2022/110340/ would not load) — https://apple-docs.everest.mt/docs/wwdc/wwdc2022-110340/
- Dashboards: Making Charts and Graphs Easier to Understand, Nielsen Norman Group, June 18, 2017 — https://www.nngroup.com/articles/dashboards-preattentive/
- Clutter-Free: One of the 3 Cs for Better Charts, Nielsen Norman Group, February 6, 2022 — https://www.nngroup.com/articles/clutter-charts/
