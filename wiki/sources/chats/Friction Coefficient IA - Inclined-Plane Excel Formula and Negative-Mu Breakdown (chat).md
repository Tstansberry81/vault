---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-01-09
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, lab-ia, friction]
status: active
---

# Friction Coefficient IA - Inclined-Plane Excel Formula and Negative-Mu Breakdown

A working session for an [[IB Physics (HL)]] Internal Assessment on the **coefficient of kinetic friction** measured from a cart sliding down a variable-angle incline. Traveler arrives with a wrong force balance (`mg sinθ - mg cosθ = ma`), and the chat walks him to the correct model and a usable spreadsheet.

## The physics fixed
The error was treating `mg cosθ` (the normal force magnitude) as the friction force. Friction is `μN = μ mg cosθ`, so the correct force balance along the slope is:

`mg sinθ - μ mg cosθ = ma`  →  `μ = (g sinθ - a) / (g cosθ)`

Mass cancels (as it must). The Excel form he wanted, with angle in degrees:

```excel
=(C2*SIN(RADIANS(B2))-A2)/(C2*COS(RADIANS(B2)))
```

He needed reminding that Excel's `SIN`/`COS` take radians, so `RADIANS()` must wrap any degree-valued angle — a small but IA-fatal trap.

## The real intellectual content: negative μ
His data ran five angle trials (15°, 12°, 9°, 6°, 3°). At 15° and 12° the coefficient came out small and positive (μ ≈ 0.013–0.021), but at **θ ≤ 9° the computed μ went negative**, because measured acceleration exceeded `g sinθ` — physically impossible for passive sliding. Rather than treating this as a spreadsheet bug, the chat reframes it as a *model breakdown at low angle*: at small θ the gravitational driving component is tiny, so timing-resolution error, release push, and the static-to-kinetic transition dominate, making `μ` extremely sensitive when `a ≈ g sinθ`.

The key takeaway he internalized: don't average or absolute-value the negative results, and don't silently delete them. Instead, state the **validity range** of the model, flag the low-angle trials as a method limitation (not "friction acting up"), and analyze trends with and without them. This is examiner bait — IB rewards recognizing where your model stops working. A nice instance of his recurring move of turning broken data into evaluation credit (cf. the [[Vernier Cart Explosion Lab - Momentum Conservation (chat)]]).

## Spreadsheet labeling catch
On his final data table, the math across columns was internally consistent (friction matched both `mg sinθ - ma` and `μ mg cosθ`), but a column labeled **"Weight"** actually held `mg sinθ` — the weight component *parallel to the incline*, not weight. A rename to "component of weight parallel to incline" is the one-line fix separating mid- from upper-band HL work.

This chat sits alongside his other hands-on HL lab and mechanics work and shows the practical, error-aware side of his physics: getting the algebra right, wiring it into Excel correctly, and converting anomalous data into a defensible Evaluation section.
