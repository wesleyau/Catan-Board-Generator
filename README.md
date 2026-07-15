# Catan Tournament Boards

A random Catan board generator that produces tournament layouts.

---

## Use it now

# **[https://wesleyau.github.io/Catan-Board-Generator/](https://wesleyau.github.io/Catan-Board-Generator/)**

---

## What it does
 
Generates a random Catan board (resources + number tokens + ports) in one of two sizes:
 
- **3–4 player** *(default)* — the standard 19-hex hexagonal board with 9 ports
- **5–6 player** — the 30-hex stretched-hex board from the official 5–6 Player Extension (rows of 3-4-5-6-5-4-3)
Two number-placement methods are available on the 3–4 board:
 
- **Random** *(default)* — number tokens placed randomly with configurable tournament constraints
- **Spiral (A–R)** — official rulebook method using the letters on the back of the number tokens
The 5–6 board uses random placement only (there's no port support for it yet).

## Default rules
 
1. No 6 or 8 touching another 6 or 8
2. No 2 touching a 12
3. No two of the same number touching
4. No duplicate number on the same resource
The desert is placed at random, and there's no requirement on where 2 or 12 land — both can be tightened in the Rules panel.

## Ports (3–4 player)
 
Every 3–4 board includes 9 ports on the coast — **4 generic 3:1 ports** and **5 resource-specific 2:1 ports** (one for each of wood, sheep, wheat, brick, ore). Two options:
 
- **Standard** *(default)* — ports appear in fixed positions matching the standard Catan layout, with the two 3:1 ports along the bottom of the board. Walking clockwise from the bottom-left:
  > 3:1, 3:1, Sheep 2:1, 3:1, Ore 2:1, Wheat 2:1, 3:1, Wood 2:1, Brick 2:1
- **Randomized** — the 9 port types are shuffled into the 9 port slots. Useful if you have individual port pieces and want a fully random setup.
Each port is drawn just off the coast with its symbol: 🌲 wood, 🐑 sheep, 🌾 wheat, 🧱 brick, ⛰ ore, or a plain "3:1" for generic ports.

## 5–6 player extension
 
Selecting **5–6 player** switches the whole board:
 
- **30 hexes**: 6 wood, 6 sheep, 6 wheat, 5 brick, 5 ore, plus **2 deserts**
- **28 number tokens**: three each of 3, 4, 5, 6, 8, 9, 10, 11 and two each of 2, 12
- **Layout**: stretched hex, 7 rows of 3-4-5-6-5-4-3
- **Both desert positions** honor the desert placement setting
- **"2 or 12 on edge"** in this mode: "At least 1" = at least one 2 or 12 on any edge hex; "Both" = at least one 2 AND at least one 12 on edge
Spiral mode and ports are 3–4 player only.

## Spiral mode (3–4 player)
 
Uses the official Catan rulebook method. Number tokens have letters A through R on the back; place A on a corner hex and continue counter-clockwise around the outer ring (skipping the desert), then spiral inward to the center.
 
The official 3–4 player letter-to-number mapping is built in:
 
> A=5, B=2, C=6, D=3, E=8, F=10, G=9, H=12, I=11, J=4, K=8, L=10, M=9, N=4, O=5, P=3, Q=11, R=6
 
In spiral mode, the constraint rules grey out — they only apply when numbers are placed randomly. Resources, desert position, and ports still vary, so each board is different.

## Configurable options
 
Open the **Rules** panel above the Generate button. Each rule can be relaxed or tightened independently:
 
| Rule | Options |
|---|---|
| Board size | 3–4 player *(default)* · 5–6 player |
| Number placement (3–4 only) | Random *(default)* · Spiral (A–R) |
| 6/8 separation | No touching *(default)* · Allowed |
| 2-and-12 separation | No touching *(default)* · Allowed |
| Same number touching | Forbidden *(default)* · Allowed |
| Same number on same resource | Forbidden *(default)* · Allowed |
| 2 or 12 on edge | No requirement *(default)* · At least 1 · Both |
| Desert placement | Random *(default)* · Center · 2nd ring · Edge |
| Ports (3–4 only) | Standard *(default)* · Randomized |
 
A "Reset to default" button restores everything in one click.
 
> Note: "Allowed" means *not enforced* — the situation may or may not occur by chance. It does not force the situation to happen.

## Other features

- **Shareable seeds.** Every board has a hex seed shown next to the Generate button. Click it to copy a URL like `?seed=deadbeef` — open that URL anywhere and you get the exact same board. Useful for tournaments where players need a reproducible setup.
- **Mobile-friendly.** Works on iPhone and Android. 

## Run locally

Open `index.html` in a browser. That's it — no build step, no install.

## How it works (briefly)
 
Resources are shuffled into 19 or 30 hexes with deserts placed per the user's setting. Number tokens are then placed via constrained backtracking that visits the most-constrained hexes first (highest neighbor count), checking each candidate against whichever rules are currently active. If number placement can't complete within the step budget, the resource layout is re-shuffled and tried again.
 
In spiral mode (3–4 only), the spiral path is walked counter-clockwise from the top-left corner inward, skipping the desert hex and assigning A through R as it goes.
 
Ports on the 3–4 board sit at 9 fixed coastal positions matching the standard Catan layout. In standard mode the port types are placed in a fixed order; in randomized mode all 9 port types are shuffled into the 9 slots.
 
The algorithm has been validated across all rule combinations in both board sizes with zero validation failures.

## Credit

Created by Wesley Au — aucwesley@gmail.com

## License

MIT License — Copyright (c) 2026 Wesley Au
