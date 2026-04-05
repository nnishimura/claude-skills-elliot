# Elliot

Your AI Financial Planner

Elliot is a personal financial planner (CFP-level) that runs as a **Claude skill**.

- **Local-first** - Your financial data stays on your machine as local markdown files.
- **Memory across sessions** - Generated financial summary markdown files give Elliot persistent context every time you talk.

## Screenshots

<img width="600" alt="Financial Profile Dashboard" src="https://github.com/user-attachments/assets/1b9fa892-295c-47de-9433-4b2cf96949fa" />

<img width="600" alt="Goal Plan Dashboard" src="https://github.com/user-attachments/assets/afa92e93-8b42-4e4d-b463-d9b3cdc4e90a" />

<img width="600" alt="Advice Dashboard" src="https://github.com/user-attachments/assets/d03e245b-e621-498f-8a29-261d9aaf78e6" />

## Commands

### `/elliot setup`

Interactive onboarding that builds your financial profile. Choose how to get started:

- **Upload PDF statements** — Drop your bank statements, pay stubs, brokerage summaries, and credit card statements into `memory/raw/statements/`. Elliot reads and extracts everything automatically.
- **Answer onboarding questions** — Elliot walks you through a short Q&A (3-4 rounds) covering income, expenses, assets, debts, and investments.
- **Combine both** — Upload what you have and Elliot asks about the rest.

Generates two files:
- `summary.md` — Your complete financial picture (income, expenses, assets, debts, investment portfolio, key metrics)
- `profile.md` — Personal context (household, employment, risk tolerance, life events)

On Claude Desktop, outputs a visual HTML dashboard of your full financial profile.

### `/elliot plan`

Turn a life goal into a concrete financial plan. Elliot will:

1. Load your financial summary
2. Guide you through interactive discovery (timeline, location, budget)
3. Analyze feasibility across four dimensions — affordability, cash flow, safety, life impact
4. Factor in investment growth on your existing portfolio
5. Deliver a verdict: **SAFE** / **STRETCH** / **NOT RECOMMENDED**

Output: an actionable goal plan with milestones, assumptions, risks, and clear next steps. On Claude Desktop, rendered as a visual HTML dashboard with verdict badge and milestone timeline.

### `/elliot advice`

Ask any financial question grounded in your actual data:

- "Can I afford a $50k car?"
- "Should I pay off debt or invest?"
- "What should I do with a $10k bonus?"

Elliot gives an opinionated recommendation backed by your real numbers — not "it depends." On Claude Desktop, rendered as a visual HTML dashboard with verdict, supporting calculations, trade-offs, and action items.

## How Data is Stored

**Claude Code (CLI/IDE)** — All your financial data lives locally as markdown files. Data persists across sessions and never leaves your machine.

```
memory/
├── summary.md          # Financial summary (single source of truth)
├── profile.md          # Personal info, household, risk tolerance
├── goals/
│   └── buy-home.md     # Goal plans + progress tracking
└── raw/
    └── statements/     # Your uploaded PDF statements
```

**Claude Desktop App** — Your financial profile and elliot's response are output as interactive HTML artifacts.
