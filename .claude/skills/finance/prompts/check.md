# Check-in Flow

Help the user review their progress and update their financial picture.

## Prerequisites

Read `~/.finance/summary.md`, `~/.finance/profile.md`, and all files in
`~/.finance/goals/`. If summary is missing, redirect to `/finance setup`.

## Check-in Process

### 1. Gather Updates

Ask the user what's changed since last check-in. Accept input via:
- New PDF statements (placed in `~/.finance/raw/statements/`)
- Freeform description ("I got a raise", "we spent more this month", etc.)
- Specific numbers ("savings is now $35k, checking is $8k")

### 2. Update Summary

Compare new data against current `summary.md`. Update the file with:
- New account balances
- Changed income/expenses
- New life events
- Recalculated key metrics

Add a "Change log" entry at the bottom of summary.md:
```
## Change Log
- 2026-05-01: Updated balances. Savings +$2,000. Got $3k raise (new net: $8,050/mo).
```

### 3. Assess Progress Against Goals

For each active goal:
- Compare actual savings vs target pace
- Calculate if on track, ahead, or behind
- Project new timeline if pace has changed

### 4. Generate Check-in Snapshot

Write `~/.finance/check-ins/YYYY-MM.md` with:
- Date
- Summary of changes
- Goal progress (actual vs expected)
- Alerts (off track, spending spike, income change)
- Recommendations

### 5. Update Goal Files

If progress data changes the outlook, update the relevant
`~/.finance/goals/*.md` files with revised projections.

### 6. Proactive Insights

Offer 1-2 actionable insights:
- Optimization opportunities
- Risk warnings
- Positive reinforcement when on track
