# 070 — Infinite scroll vs pagination

> Entry 070 — added 2026-11-14 (Drop 6: Structure, comfort, and trust).

*Two ways through a long list, and when each wins.*

**What it is.** Pagination breaks a long list into numbered pages
with a beginning and an end. Infinite scroll loads the next chunk
automatically as you reach the bottom, so the list never ends. NN/g
puts the choice plainly: infinite scroll lowers the interaction cost
of browsing, but it is a poor fit for tasks like finding one
particular item. Between the two sit the hybrids shipping apps
actually use. A Load More button appends the next chunk only when
asked, which stops the flow long enough to reach the footer. Integrated
pagination, as Google used on its mobile Shopping page, drops page
indicators into the endless scroll as landmarks you can jump between.
Virtualized lists keep one continuous scroll but only build the rows
actually in view, measuring the rest as they enter the window, so a
huge list costs no more than a short one. The right answer is always
about what the user is doing: browsing with no target, or hunting for
something specific.

**Why it feels good.** Infinite scroll feels good because it removes
interruptions. NN/g cites a study in the Information Systems Journal
finding that even short interruptions, like clicking Next to go to
another page, can trigger users on a social ecommerce platform to
change their task. No click, no wait, no decision, just more content.
Pagination feels good for the opposite reason: control. With
pagination there is a beginning and an end, people can anticipate the
effort required to scan the page, there is a happy sense of completion
when a page is reviewed, and the choices on smaller pages are easier
to evaluate because fewer options feel less overwhelming. That is
NN/g's own summary from 2014, and it still holds. The Load More button
is the middle that keeps most of both: the list grows instead of
being replaced, so comparing across chunks stays easy, but each chunk
arrives by choice, so the user reads items instead of skimming past
them.

**The numbers.** Baymard Institute tested all three patterns across
year-long usability studies of more than 50 leading ecommerce sites
and found Load More buttons combined with lazy loading to be the
superior implementation, with infinite scrolling downright harmful
for search results and on mobile. The observed behaviour: subjects
browsed much less of a list under pagination and were discouraged by
more than a handful of page links, while on infinite scroll they
browsed vastly more, often 100 or more products, which they virtually
never did under pagination. But the benefit turned at scale: infinite
scroll was efficient for the first 50 to 150 products, then subjects
kept scrolling without focusing on individual items. On mobile they
scrolled through more than twice as many products with infinite scroll
as with pagination. Baymard's thresholds, from the same testing: for
category browsing, show 10 to 30 products, lazy-load 10 to 30 more at
a time until 50 to 100 are showing, then a Load More button; for
search results, load only 25 to 75 by default and never use infinite
scroll, since relevance falls off fast; on mobile, load 15 to 30
before the button and load them all at once instead of lazy-loading.
Only 8% of the top 50 US ecommerce sites benchmarked used a Load More
button at all. And the back button is where Load More usually fails:
of the benchmarked sites that had one, over 90% got it wrong, dumping
the user at the top of the list instead of their old spot. NN/g's
2022 guidance adds the rule for when to avoid infinite scroll
entirely: when users want to find something specific, compare items
in a long list, or inspect only a few items at the top. Infinite
scroll dates to 2006, and NN/g's conclusion is that no solution is
overall superior: it always depends on the site and the user's goals.

**Where it fits his apps.** GITDATA: search results get
pagination or a Load More button with a 25 to 75 first chunk, since a
dataset search is a find task, not a browse; a long repo list gets
Load More with the position remembered on return. Qwkhnd: task
lists are short enough to paginate simply, and returning from a task
detail must land back on the same task, not the top of the list.
MIMIK: the capture library is a browse surface, so Load More
with lazy thumbnails fits, with the count shown ("24 of 180 clips")
so the list never feels endless. ACR: the trace log is a long
list that is read top to bottom, so virtualize it, build only the
visible rows, and keep the scroll position when jumping to a detail
and back. In Qt, the model/view pattern is virtualization by another
name: the view only builds delegates for visible rows, which is what
keeps a 10,000 row trace smooth on 8 GB with no GPU. The Load More
button needs a visible `border` on `:focus`, since `outline` renders
0 pixels in this build, and a list dialog that grows a section must
scroll.

**Watch out.** Infinite scroll hides the footer: new content keeps
pushing it down, and Baymard watched users see it for a second or two
before it was shoved out of view again, which strands anything that
lives down there. It lies about progress: the scrollbar says the page
is nearly done when it is not, and NN/g calls this the worse offense
on desktop, since people still use the scrollbar to judge how much
effort is left. It destroys refinding: it is hard to remember the
location of any specific item in an endless list and return to it,
while "page 3" is easy to remember. It can create an illusion of
completeness, where a gap plus a slow load reads as the end of the
list when more is still coming; a visible loading indicator at the
bottom is the fix. It is hostile to keyboard and screen reader users:
keyboard-only users must tab through every link to get past the feed,
and screen readers may only see the first chunk, though the ARIA feed
role now gives screen readers a way through. It costs load time and
bandwidth, which hits mobile and slow connections hardest. Integrated
pagination has no user testing data behind it yet, and NN/g warns it
could confuse more than it helps while it is unfamiliar. And Baymard
is blunt about the back button: if you cannot return the user to
their exact spot, do not use Load More at all, stick with pagination.

## See also

- [051 Overview first, details on demand](051-overview-first-details-on-demand.md)
- [029 Search-as-you-type done well](029-search-as-you-type-done-well.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)

## Sources

- Infinite Scrolling is Not for Every Website, Nielsen Norman Group, 2014-02-02 — https://www.nngroup.com/articles/infinite-scrolling/
- Infinite Scrolling: When to Use It, When to Avoid It, Nielsen Norman Group, 2022-09-04 — https://www.nngroup.com/articles/infinite-scrolling-tips/
- Infinite Scrolling, Pagination Or "Load More" Buttons? Usability Findings In eCommerce, Smashing Magazine, March 2016 — https://www.smashingmagazine.com/2016/03/pagination-infinite-scrolling-load-more-buttons/
- TanStack Virtual — https://tanstack.com/virtual/latest
