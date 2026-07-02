---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-01-16
author: Traveler Stansberry
source_type: chat
tags: [chat, math/calculus, ib-math]
status: active
---

# Graphing a Function from Its Derivative Graph

A short, post-mortem [[IB Math (SL)]] tutoring session. Traveler "bombed a question with a cubic first derivative and couldn't figure out how to graph its base function," and came to ChatGPT to fix the misconception so it wouldn't recur. It is a clean window into the kind of calculus reasoning he was drilling: graphical (not algebraic) reconstruction of $f$ from $f'$.

## The method he extracted
The conversation lays out the standard derivative-graph interrogation, which Traveler clearly internalized:
- **$f' = 0$** → horizontal tangent on $f$ (max/min if $f'$ crosses, flat inflection if it only touches).
- **Sign of $f'$** → $f$ increasing (above axis) or decreasing (below).
- **Shape of $f'$** (increasing/decreasing) → concavity of $f$, since $f'' $ is the slope of $f'$.
- **Extrema of $f'$** → inflection points of $f$.
- A cubic $f'$ implies a **quartic $f$**: up to three critical points and two inflection points. You can never fix the vertical position of $f$ without a given point like $f(0)=2$.

## The actual confusion
His core error, surfaced through two follow-up questions and an uploaded graph, was conflating three distinct signals: a sign change of $f'$ (gives a max/min in $f$), a local extremum of $f'$ (gives an inflection in $f$), and a sign change of $f$ itself (only where $f$ crosses the x-axis — undeducible from $f'$ alone). He had assumed "$f'$ starts increasing" forced a sign change in the original function. The fix: $f'$ increasing only tells you the graph **bends** upward (concave up), not where it **lives** vertically.

![[369639FF-903A-428C-B3D4-15C23EE0EB6A.jpeg]]

Using the picture above (red = $f$, orange = $f'$), the tutor walked the relationships as a "crime scene reconstruction": where the orange curve bottoms out and rises, the red curve has an inflection (not a crossing); where orange crosses the x-axis, red flattens.

## What it shows
A characteristic Traveler study move: rather than re-grind problem sets, he isolates the *conceptual* failure point after a graded miss and demands the underlying rule ("explain with my original scenario"). The exchange reflects his exam-oriented, structural approach to [[IB Math (SL)]] and fits his broader analytical, [[Intellectual Interests|systems-minded]] disposition — wanting calculus to "behave like a system" rather than feel like guesswork. Connects to his quantitative ambitions documented in [[UVA and the Quant Question]].
