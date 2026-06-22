# MyBank · Vendor Evaluation Simulator

Interactive evaluation simulator for MyBank's core platform replacement
programme, comparing three anonymised vendor options — CAKE, BinB and DIY —
across five weighted dimensions, with a strategic-lens layer on top.

**Live:** https://kennelm2025.github.io/MyBank/

## What it does

- Scores each vendor on **D1 Functional Fit (35%)**, **D2 Technology & Architecture (25%)**, **D3 Implementation & Delivery (20%)**, **D4 Operational (10%)** and **D5 Risk & Vendor (10%)**.
- Two scores per requirement (0–3): the **vendor's capability claim** and the **SME's validation** of that claim. Method D combines them into a *validated capability* — a claim only counts to the extent the SME confirms it.
- Headline = **Weighted SME Score** = Σ(dimension SME validation × strategic weight). SME validation is the authoritative metric; the vendor's own claim is shown alongside.
- Import completed vendor workbooks (CAKE / BinB / DIY) to load real evidence; imported evidence is immutable and overrides the embedded baseline.

## Two layers, behind a firewall

- **L1 — Evidence.** The capability-and-cost data set. Views: Executive Summary, SME Slider Scores, Dimension Drill-Down, Build vs Buy, Critical Functions, TCO Comparison, Risk Heatmap, and the **Evaluation Scorecard**.
- **L2 — Strategic Analysis.** Re-weights the L1 evidence through a strategic lens: Strategic Lens (seat-based weighting — CEO / CFO / CIO / CRO / Board), Board Paper Alignment (rolls up to the board-paper areas, 0–4) and a Monte Carlo sweep.
- A hard firewall keeps the two apart: L2 reads L1 but can never mutate it.

## Simulate, snapshot and the dark gate

The simulator behaves like a real scenario tool: set up the sliders, **Simulate**, then read the results.

- **Simulate L1** is the single commit point. It freezes the current deflected data set into a snapshot, and every output reads only from that snapshot.
- Move any slider and the outputs **go dark** with a "Simulate L1 to refresh" prompt — no output ever shows a number that isn't from the last committed run.

## Evaluation Scorecard (data-integrity check)

The last L1 tab — run it to confirm the scenario is internally coherent before trusting the decision views. It stacks the Weighted SME Score cards, Claimed vs Validated, and the Vendor vs SME Material Discrepancy Map, under a single **green / amber / red** status headline:

- **green** — SME validation sits at or below the vendor's claim wherever it matters;
- **amber** — some rows have SME validating above the claim;
- **red** — the SME exceeds the vendor's claim in too many rows (an incoherent scenario).

The tab itself carries a matching status light, so an accepted-but-odd setup keeps signalling until it is re-balanced.

## Vendor / SME coherence

- SME sliders that rise above the matching vendor claim are flagged red live as you drag.
- Simulate is **gated**: if the pending scenario is amber/red it asks before committing — **Run anyway** (commit as-is) or **Pull SME to the claim** (lower the over-reaching SME scores to the vendor claim, then commit).

## Use

Open `index.html` directly, or use the GitHub Pages URL above. Single
self-contained HTML file — no build step, no dependencies.
