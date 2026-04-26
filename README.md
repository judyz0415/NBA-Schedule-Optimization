<<<<<<< HEAD
# NBA-Schedule-Optimization
=======
# NBA Schedule Optimization: Balancing Fan Demand and Player Health

This project presents an optimization framework for the NBA regular-season schedule with a clear league objective: increase fan engagement and commercial value while reducing fatigue-related travel stress.

I built this work to reflect how I think about basketball operations problems: data-driven, operationally realistic, and aligned with both business outcomes and player welfare.

## Why This Matters for the NBA

For league and team decision-makers, schedule design is a strategic lever that affects:

- National and local ratings
- Ticket demand and game-day revenue
- Star player availability and injury risk
- Competitive fairness across teams
- Long-term global growth of the NBA product

This project targets that exact intersection by optimizing game placement and controlling back-to-back travel burden.

## Problem Framing

The model evaluates and generates schedules over the 174-day NBA regular season (30 teams, 82 games per team), with:

- **Primary objective:** maximize a weighted matchup value score (popularity + calendar value)
- **Health/logistics objective:** reduce harmful back-to-back travel demands
- **Operational realism:** enforce core NBA scheduling rules and calendar constraints

I specifically imposed a **1600-mile cap** on travel between the first and second games of a back-to-back sequence to improve rest feasibility.

## Data and Features

Key inputs include:

- 2024-2025 full NBA game calendar
- Team-to-team arena distance matrix (30x30)
- League structure (conference/division relationships)
- No-game dates and showcase-day limits (Opening Night, Christmas)
- A custom game-value tensor based on:
  - team popularity proxies
  - all-star concentration
  - market size
  - franchise brand/history
  - day-of-week / showcase effects

## Optimization Approach

I formulated the problem as a mixed-integer optimization model with binary game assignment decisions.

Core constraints include:

- One game per team per day
- Exactly 82 games per team
- Pairwise matchup frequency requirements
- No games on designated blackout dates
- Daily league volume limits (avoid over/under-scheduled days)
- No three-games-in-three-days
- Back-to-back structure controls
- Back-to-back travel restriction (>=1600 miles disallowed)

## Results Snapshot

Compared to the real 2024-2025 schedule under the same scoring framework:

- **Objective value improved by ~13.5%** with travel constraints
- **Average back-to-back travel dropped by ~24%** (about 1058 -> 811 miles)
- Travel-constrained optimized schedule retained almost all value of unconstrained optimization

Interpretation for decision-makers:

- It is possible to preserve high-value national matchups **without** accepting the same level of fatigue-inducing travel.
- Data-driven scheduling can support both **business KPIs** and **player availability**.

## Repository Structure

```text
.
├── artifacts/                  # Generated tensors/outputs from optimization runs
├── data/
│   ├── raw/                    # Core scheduling and team datasets
│   └── weights/                # Baseline and bonus weight design inputs
├── notebooks/                  # Main modeling/analysis notebook
├── reports/                    # Final written report
└── README.md
```

## Tools and Repository Contents

This repository contains the analysis assets used in the project, including:

- Notebook implementation (`notebooks/nba_schedule_optimization.ipynb`)
- Scheduling and team datasets (`data/raw/schedule.csv`, `data/raw/distance.csv`, `data/raw/team_list.csv`, etc.)
- Weighting inputs (`data/weights/baseline_weights.xlsx`, `data/weights/bonus_weights.xlsx`)
- Final written report (`reports/nba_schedule_optimization_report.pdf`)

>>>>>>> b0b9f18 (Reorganize project into clean GitHub-ready structure and update README)
