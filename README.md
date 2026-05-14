# Catan Tournament Boards

A random Catan board generator that produces tournament-legal layouts.

Single HTML file, no dependencies, runs in any browser — including offline.

---

## Use it now

# **[https://wesleyau.github.io/Catan-Board-Generator/](https://wesleyau.github.io/Catan-Board-Generator/)**

Works on any device. Open on your phone and add to home screen for an app-like icon.

---

## What it does

Generates a standard 19-hex Catan board (resources + number tokens). Two number-placement methods are supported:

- **Random** *(default)* — number tokens placed randomly with configurable tournament constraints (no 6/8 touching, etc.)
- **Spiral (A–R)** — official rulebook method using the letters on the back of the number tokens

## Default rules

1. No 6 or 8 touching another 6 or 8
2. No 2 touching a 12
3. No two of the same number touching

The desert is placed at random, and there's no requirement on where 2 or 12 land — both can be tightened in the Rules panel.

## Spiral mode

Uses the official Catan rulebook method. Number tokens have letters A through R on the back; place A on a corner hex and continue counter-clockwise around the outer ring (skipping the desert), then spiral inward to the center.

The official 3–4 player letter-to-number mapping is built in:

> A=5, B=2, C=6, D=3, E=8, F=10, G=9, H=12, I=11, J=4, K=8, L=10, M=9, N=4, O=5, P=3, Q=11, R=6

In spiral mode, the constraint rules grey out — they only apply when numbers are placed randomly. Resources and desert position still vary, so each board is different.

## Configurable options

Open the **Rules** panel above the Generate button. Each rule can be relaxed or tightened independently:

| Rule | Options |
|---|---|
| 6/8 separation | No touching *(default)* · Allowed |
| 2-and-12 separation | No touching *(default)* · Allowed |
| Same number touching | Forbidden *(default)* · Allowed |
| Same number on same resource | Forbidden *(default)* · Allowed |
| 2 or 12 on edge | At least 1 · Both · No requirement *(default)* |
| Desert placement | Random *(default)* · Center · 2nd ring · Edge |

A "Reset to default" button restores everything in one click.

> Note: "Allowed" means *not enforced* — the situation may or may not occur by chance. It does not force the situation to happen.

## Other features

- **Shareable seeds.** Every board has a hex seed shown next to the Generate button. Click it to copy a URL like `?seed=deadbeef` — open that URL anywhere and you get the exact same board. Useful for tournaments where players need a reproducible setup.
- **Mobile-friendly.** Works on iPhone and Android. 
- **Works offline.** Once the page loads, no network is required.

## Run locally

Open `index.html` in a browser. That's it — no build step, no install.

## How it works (briefly)

Resources are shuffled into 19 hexes with the desert placed per the user's setting. Number tokens are then placed via randomized backtracking, checking each candidate against whichever rules are currently active. If number placement fails, the resource layout is re-shuffled and tried again. Almost every board solves on the first try; the hardest setting combinations average 3–5 tries and complete in well under a second.

The algorithm has been validated across all 192 possible rule combinations (~38,400 boards), with zero validation failures and the expected statistical variance for permissive settings.

## Credit

Created by Wesley Au — aucwesley@gmail.com

## License

MIT License — Copyright (c) 2026 Wesley Au
