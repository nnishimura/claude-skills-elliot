# Setup Flow

Build the user's financial profile using template files they fill in, with PDF
statements to fill any gaps.

## Step 1: Create template files

Create the `.finance/` directory structure:
```
mkdir -p .finance/goals .finance/check-ins .finance/raw/statements
```

Copy the templates to create the user's files:
- Copy [[templates/summary.md]] → `.finance/summary.md`
- Copy [[templates/profile.md]] → `.finance/profile.md`

If `.finance/summary.md` already exists, ask the user if they want to update it
or start fresh before overwriting.

Tell the user:
> I've created two files for you to fill in:
> - `.finance/summary.md` — your financial data (income, expenses, assets, debts)
> - `.finance/profile.md` — personal info (household, employment, risk tolerance)
>
> Open them in your editor, fill in what you know, and leave `[X]` for anything
> you're unsure about. Let me know when you're done.

## Step 2: Wait for user

The user will edit the files and tell you when they're ready. Do NOT ask
questions yet — let them fill in what they can first.

## Step 3: Read and validate

Read both `.finance/summary.md` and `.finance/profile.md`. Check for:

- Fields still containing `[X]` or placeholder text
- Obvious inconsistencies (expenses > income, missing totals, etc.)
- Missing critical data (net income is essential for all planning)

Compile a list of **missing or unclear fields**.

## Step 4: Fill gaps with PDF statements (if needed)

If important data is missing, ask the user:
> Some fields are still missing. You can:
> 1. **Upload PDF statements** — place them in `.finance/raw/statements/` and I'll
>    extract the data
> 2. **Tell me** — describe the missing info conversationally
> 3. **Skip** — I'll work with what we have (some features may be limited)

If the user provides PDFs:
- Read each PDF in `.finance/raw/statements/`
- Extract: account balances, income deposits, recurring expenses, debt payments
- Update `.finance/summary.md` with extracted data
- Show the user what was extracted so they can verify

If the user describes it conversationally:
- Update the relevant fields in `.finance/summary.md` and/or `.finance/profile.md`

## Step 5: Investment portfolio discovery

If the user has any investment accounts (401(k), IRA, RRSP, TFSA, brokerage, etc.
with non-zero balances), ask about their portfolio:

> I see you have investment accounts. To project how your money will grow, I'd
> like to understand your portfolio:
> 1. **What's in them?** (e.g., index funds, target-date funds, individual stocks,
>    bonds, GICs, etc.)
> 2. **What's the rough allocation?** (e.g., "mostly stocks", "60/40 stocks/bonds",
>    "all in S&P 500 index")
> 3. **Do you contribute regularly?** How much per month, and does your employer match?

Fill in the **Investment Portfolio** section of `summary.md` with what the user
provides.

Then **estimate the annual growth rate** based on their allocation:

| Portfolio Type | Estimated Annual Return |
|----------------|------------------------|
| Aggressive (90%+ stocks) | 8-10% |
| Growth (70-90% stocks) | 7-9% |
| Balanced (40-70% stocks) | 5-7% |
| Conservative (< 40% stocks) | 3-5% |
| Cash/GICs/savings only | 1-3% |

Write the estimated return and basis into the **Estimated Annual Growth Rate**
subsection. Be transparent: "Based on your ~80% equity allocation, I'm estimating
~8% annual growth. This is a long-term average — actual returns will vary year
to year."

If the user doesn't know their allocation, ask what platform/funds they use and
look up typical allocations for those products (e.g., target-date funds have a
known glide path).

If the user has NO investments, skip this step and note "N/A" in the portfolio
section.

## Step 6: Calculate metrics and finalize

Once data is sufficient, calculate and fill in the **Key Metrics** section:
- Monthly surplus = household net monthly income - total monthly expenses
- Monthly savings rate = (surplus / net income) × 100
- Emergency fund = (checking + savings) / total monthly expenses
- Net worth = total assets - total debt
- Debt-to-income ratio = (total monthly debt payments / gross monthly income) × 100

Update the "Last updated" date and "Sources" field.

## Step 7: Final review

Show the user a concise summary of their financial picture:
- Income, expenses, surplus
- Assets, debts, net worth
- Key metrics

Ask if anything needs correcting. Apply any corrections to the files.

## Step 8: Output as Artifacts

After finalizing, output the complete content of both files as **Artifacts**:
- Output `summary.md` content as an Artifact titled **"Financial Summary"**
- Output `profile.md` content as an Artifact titled **"Personal Profile"**

This ensures the data persists in the conversation for Claude desktop app users
and is visible for review in any environment.

## Important rules
- ALWAYS separate gross vs net income
- ALWAYS separate user vs partner income
- Label any estimated values in the "Estimates" field at the top
- If net income is unknown but gross is provided, estimate net as ~70% of gross
  and clearly mark it as an estimate
