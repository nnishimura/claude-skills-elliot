# Setup Flow

Build the user's financial profile through guided onboarding — never ask them
to manually fill in template files.

## Step 1: Create directory structure

Create the `.finance/` directory structure:
```
mkdir -p .finance/goals .finance/raw/statements
```

If `.finance/summary.md` already exists, ask the user if they want to update it
or start fresh before overwriting.

## Step 2: Choose onboarding method

Ask the user how they'd like to get started:

> **How would you like to set up your financial profile?**
>
> 1. **Upload PDF statements** — Download statements from your bank, brokerage,
>    credit card, and payroll accounts (account summaries, transaction history,
>    salary/pay stubs, etc.), place them in `.finance/raw/statements/`, and I'll
>    extract everything automatically.
> 2. **Answer onboarding questions** — I'll walk you through a short Q&A to
>    build your profile from scratch.
>
> You can also combine both — upload what you have and I'll ask about the rest.

## Step 3A: PDF Statement Path

If the user chooses to upload statements:

1. Tell them what's most useful to upload:
   - Bank account statements (checking & savings — last 1-3 months)
   - Credit card statements (last 1-3 months)
   - Brokerage / retirement account summaries (latest)
   - Pay stub or salary statement (most recent)
   - Mortgage or loan statements (if applicable)

2. Ask them to place the files in `.finance/raw/statements/` and let you know
   when they're ready.

3. Read each PDF in `.finance/raw/statements/`. Extract:
   - **Income**: salary/pay amounts, frequency, gross vs net, employer name
   - **Expenses**: recurring charges, categories of spending, rent/mortgage
   - **Assets**: account balances (checking, savings, investment, retirement)
   - **Debts**: loan balances, interest rates, minimum payments
   - **Investment details**: holdings, allocation, contributions, employer match

4. Show the user a summary of what was extracted and ask them to confirm or
   correct anything. Fill any remaining gaps by asking targeted questions (see
   Step 3B question bank — only ask what the PDFs didn't cover).

## Step 3B: Conversational Onboarding Path

If the user chooses Q&A, walk through these topics in order. Group related
questions together — don't ask one question at a time. Aim for 3-4 rounds of
questions max.

### Round 1: Basics & Income
- Where do you live? (city, state/province)
- Household status: single, married, or partnered? Any dependents?
- Employment: job title, employer, how long? Self-employed or W-2/salaried?
- Gross annual salary? Net monthly take-home pay? Pay frequency?
- Does a partner/spouse contribute income? If so, same details.

### Round 2: Expenses & Lifestyle
- Monthly housing cost? (rent or mortgage — include amount and type)
- Estimate your total monthly spending across: utilities, groceries,
  transportation, childcare/education, insurance, subscriptions, dining out
  & discretionary. (They can give a lump sum or break it down — be flexible.)
- Any other recurring monthly expenses?

### Round 3: Assets, Debts & Investments
- Bank accounts: checking and savings balances (approximate is fine)
- Retirement accounts: 401(k), IRA, RRSP, TFSA, etc. — balances?
- Brokerage or other investment accounts? Balances?
- Any debts? For each: type (student loan, car, credit card, mortgage, etc.),
  balance, interest rate, monthly payment.
- Do you have an emergency fund? How many months of expenses does it cover?

### Round 4: Investments & Risk (if they have investment accounts)
- What's in your investment accounts? (index funds, target-date funds, stocks,
  bonds, etc.)
- Rough allocation? (e.g., "mostly stocks", "60/40", "all S&P 500 index")
- Monthly contributions? Does your employer match?
- Risk tolerance: conservative, moderate, or aggressive?
- Any upcoming life events that will affect your finances? (baby, job change,
  big purchase, etc.)

**Adapt as you go**: If a previous answer makes a question irrelevant, skip it.
If an answer is vague, ask one clarifying follow-up. Don't over-interrogate.

## Step 4: Build the profile files

Using the collected data (from PDFs, Q&A, or both), populate the template
files:

- Read [[templates/summary.md]] and [[templates/profile.md]] for the structure
- Create `.finance/summary.md` and `.finance/profile.md` filled in with real
  values — no `[X]` placeholders should remain for data the user provided
- For anything truly unknown, mark it as "Unknown" and note it in the Estimates
  field

## Step 5: Investment portfolio analysis

If the user has investment accounts with non-zero balances:

**Estimate the annual growth rate** based on their allocation:

| Portfolio Type | Estimated Annual Return |
|----------------|------------------------|
| Aggressive (90%+ stocks) | 8-10% |
| Growth (70-90% stocks) | 7-9% |
| Balanced (40-70% stocks) | 5-7% |
| Conservative (< 40% stocks) | 3-5% |
| Cash/GICs/savings only | 1-3% |

Fill in the **Investment Portfolio** section and **Estimated Annual Growth
Rate** subsection. Be transparent: "Based on your ~80% equity allocation, I'm
estimating ~8% annual growth. This is a long-term average — actual returns will
vary year to year."

If the user doesn't know their allocation, ask what platform/funds they use and
look up typical allocations for those products.

If the user has NO investments, skip this step and note "N/A" in the portfolio
section.

## Step 6: Calculate metrics and finalize

Calculate and fill in the **Key Metrics** section:
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
- Never ask the user to manually edit template files — Elliot always writes them
- Be conversational and encouraging, not clinical — this is sensitive data
