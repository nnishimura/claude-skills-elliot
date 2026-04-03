# Setup Flow

Guide the user through building their financial profile. This creates two files:
`~/.finance/profile.md` and `~/.finance/summary.md`.

## Step 1: Gather Data

Ask the user how they'd like to provide their financial data:

1. **PDF statements** — Ask them to place PDF files in `~/.finance/raw/statements/`
   then tell you. Read the PDFs and extract financial data.
2. **Describe it** — Have a conversation where they tell you about their finances.
3. **Both** — Read statements AND fill gaps through conversation.

## Step 2: Extract & Clarify

From whatever input the user provides, extract:

**Income** (CRITICAL: always separate gross vs net, user vs partner)
- Gross annual income (user)
- Net monthly income (user) — after tax
- Income source and type (W-2, 1099, etc.)
- Pay frequency
- Partner/spouse income (same breakdown, if applicable)

**Expenses** (monthly)
- Housing (rent/mortgage)
- Utilities
- Groceries
- Transportation
- Childcare/education
- Insurance
- Subscriptions
- Discretionary
- Other

**Assets**
- Checking accounts (with balances)
- Savings accounts
- Retirement accounts (401k, IRA, etc.)
- Investment/brokerage accounts
- Other assets

**Debts**
- Type, balance, interest rate, monthly payment for each

Ask clarifying questions for anything unclear or missing. Ask at most 2–3
questions at a time. If the user doesn't know exact numbers, make reasonable
estimates and clearly label them as estimates.

## Step 3: Personal Profile

Ask about:
- Employment status
- Household structure (partner, kids, dependents)
- Location (city/state — for cost of living context)
- Recent or upcoming life events (baby, mat leave, job change, marriage, move)
- Risk tolerance (conservative / moderate / aggressive — or ask a few questions
  to assess)

## Step 4: Generate Files

### profile.md

Write `~/.finance/profile.md` using the template from [[templates/profile.md]].

### summary.md

Write `~/.finance/summary.md` using the template from [[templates/summary.md]].

**CRITICAL requirements for summary.md:**
- Always include BOTH gross and net income
- Always separate user vs partner income
- Calculate key metrics: savings rate, emergency fund months, net worth, DTI
- Note the data sources and any estimates/assumptions
- Include a "Last updated" date

## Step 5: Review

Show the user a summary of what was generated. Ask them to review and correct
anything that's wrong. Update the files if they provide corrections.

If `~/.finance/summary.md` already exists, ask the user if they want to update
it or start fresh.
