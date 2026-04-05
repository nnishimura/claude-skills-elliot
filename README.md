# Elliot

Your AI Financial Planner

Elliot is a personal financial planner (CFP-level) that runs as a **Claude skill**.

- **Local-first** — Your financial data stays on your machine as local markdown files.
- **Memory across sessions** — Structured files give Elliot persistent context every time you talk.

## Commands

### `/elliot setup` — Build Your Financial Profile

Interactive onboarding that creates your financial profile. Provide data through:

- **PDF bank/brokerage statements** — Elliot reads and extracts the numbers
- **Freeform description** — e.g., "I make $120k, spend about $4k/month on rent..."

Generates two files:
- `summary.md` — Your complete financial picture (income, expenses, assets, debts, key metrics)
- `profile.md` — Personal context (household, employment, risk tolerance, life events)

### `/elliot plan` — Goal Planning

Turn a life goal into a concrete financial plan. Elliot will:

1. Load your financial summary
2. Guide you through interactive discovery (timeline, location, budget)
3. Analyze feasibility across four dimensions — affordability, cash flow, safety, life impact
4. Factor in investment growth on your existing portfolio
5. Deliver a verdict: **SAFE** / **STRETCH** / **NOT RECOMMENDED**

Output: an actionable goal plan with milestones, assumptions, risks, and clear next steps.

### `/elliot check` — Progress Check-in

Provide updated data (new statements, balances, income changes) and get:

- Progress vs. plan comparison
- Updated financial summary with recalculated metrics
- Investment growth tracking
- Alerts if you're off track with adjusted timelines
- Monthly snapshot saved to `check-ins/`

### `/elliot advice` — On-Demand Guidance

Ask any financial question grounded in your actual data:

- "Can I afford a $50k car?"
- "Should I pay off debt or invest?"
- "What should I do with a $10k bonus?"

## How Data is Stored

All your financial data lives locally as markdown files:

```
.finance/
├── summary.md          # Financial summary (single source of truth)
├── profile.md          # Personal info, household, risk tolerance
├── goals/
│   └── buy-home.md     # Goal plans + progress tracking
├── check-ins/
│   └── 2026-04.md      # Monthly check-in snapshots
└── raw/
    └── statements/     # Your uploaded PDF statements
```

In Claude Desktop App, data is also output as **Artifacts**
