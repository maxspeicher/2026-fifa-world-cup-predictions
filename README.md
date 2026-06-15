# 2026 FIFA World Cup Predictions

A self-contained static prediction dashboard for the 2026 FIFA World Cup.

## Overview

This repository contains a browser-ready HTML dashboard that simulates the full 2026 World Cup tournament using Monte Carlo methods. The predictions are generated entirely in the browser via embedded JavaScript, with no separate build process or runtime dependencies.

## Files

- `README.md` — project overview and usage notes.
- `predictions/` — output drafts of the prediction dashboard.
  - `draft_2026-06-10_group-matches-only.html` — early draft showing match-level predictions.
  - `draft_2026-06-11_incl-group-standings.html` — draft including projected group standings.
  - `draft_2026-06-11_incl-winner.html` — full pre-tournament prediction page with winner probabilities.
  - `draft_2026-06-14-incl-actual-results.html` — live tracker that locks in actual results, allows editing/saving match scores in your browser (localStorage), and simulates remaining matches.

## What it does

The HTML dashboard:

- Defines all 48 teams and the 12 group-stage match schedule.
- Uses predicted expected goals (`xG`) for each group match.
- Builds team strength ratings from a blend of FIFA rankings, betting odds, and group-stage xG calibration.
- Simulates 100,000 full tournaments from group stage through the final.
- Computes probabilities for every team reaching each round, including the championship.
- Implements FIFA Round of 32 bracket wiring and the official 495-combination lookup for third-place assignments.
- Displays:
  - predicted winner probability
  - advancement heatmap (R32 → R16 → QF → SF → Final)
  - group-stage standings projections
  - match-by-match win/draw/loss and xG predictions
  - methodology and model details

## Key modeling details

- Group stage outcomes are derived from Poisson goal simulations using per-match xG.
- Group tiebreakers use a FIFA-style head-to-head mini-table for tied teams.
- The best eight third-placed teams qualify for the Round of 32.
- Knockout match xG is computed from blended attack/defense ratings and stage-specific compression factors.
- Extra time is simulated, and penalty shootouts are modeled as 50/50 outcomes.

## Usage

Open `predictions/draft_2026-06-14-incl-actual-results.html` in a modern web browser for the live tracker (locks actual scores, supports editing/saving scores locally, and lets you re-run the Monte Carlo simulations after changes). Alternatively, `predictions/draft_2026-06-11_incl-winner.html` contains the pre-tournament snapshot and full simulation UI.

## Notes

- This repository is library-free and intended as a static analytic prototype.
- The model is designed for exploration rather than official forecasting.
- The current prediction page is the most complete representation of the project.
