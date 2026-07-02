---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-05-10
author: Traveler Stansberry
source_type: chat
tags: [chat, math]
status: active
---

# Area Between Curves and Signed vs Geometric Area

A tight, focused [[IB Math (SL)]] integration tutorial dated three days before [[Traveler Stansberry]]'s [[IB Math SL Paper 1 and 2 Walkthrough - Binomial, Series, and TI-84 Drills (chat)|final SL math exams]] — part of his calculus revision sprint. He asks how to find the **area between two curves**, gets the $A=\int_a^b(\text{top}-\text{bottom})\,dx$ method (find intersections, test which curve is on top, integrate), worked through the canonical $y=x^2$ vs $y=2x$ example yielding $4/3$.

The substance of the chat is him drilling down on the one point students reliably botch: when the **absolute value** actually matters. He probes it from several angles — first guessing it's "more important for curves under zero," and the model corrects him cleanly: the absolute value matters whenever the *difference* $f(x)-g(x)$ goes negative (i.e. when top and bottom swap), not when either curve individually dips below the $x$-axis. It distinguishes **signed/net area** (what a plain integral computes, where regions above and below cancel) from **geometric area** (always positive, requiring $|f(x)|$ or splitting at sign changes). He runs concrete cases: $\int_0^{10}-x^2\,dx$ giving area $1000/3$, $\int_0^4|x-2|\,dx=4$ as two triangles, and $x^3$ from $-1$ to $2$ where the net integral ($15/4$) differs from the true area ($17/4$) because of cancellation.

What it reveals is methodical, concept-first studying: rather than memorizing the formula he keeps asking "but why" until the signed-vs-geometric distinction clicks, the same depth-seeking habit visible across his [[Intellectual Interests]] and his push toward higher math for the [[UVA and the Quant Question|quant path]]. It pairs naturally with the integration-by-substitution and definite-integral work elsewhere in his exam-week chats.
