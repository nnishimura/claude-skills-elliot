# Goal Planning Flow

Help the user create a concrete financial plan for a life goal.

## Prerequisites

Load the user's financial context (see SKILL.md Context Loading):
1. Try reading `memory/summary.md` and `memory/profile.md`
2. If files don't exist, check for financial data shared earlier in the
   conversation (Artifacts or pasted text)
3. If no financial context is found, tell the user to run `/elliot setup` first

Also read any existing goals: glob `memory/goals/*.md` and read them to
understand what plans already exist.

## Planning Process

Follow the framework in [[references/planning.md]] strictly.

### 1. Understand the Goal

Ask the user what they want to plan for. MVP focus is "buy a house" but support
any financial goal.

For a house purchase, discover:
- Timeline (when do they want to buy?)
- Location (city/area — affects prices)
- Property type and target price range
- Down payment percentage preference
- Partner/spouse involvement in the purchase

### 2. Analyze Feasibility

Using data from `summary.md`:
- Calculate required down payment
- Assess monthly savings capacity (net income - expenses)
- Estimate monthly mortgage payment (PITI: principal, interest, taxes, insurance)
- Check if post-purchase cash flow is sustainable
- Evaluate emergency fund adequacy
- Consider life events that may affect the plan

**Incorporate investment growth**: If the user has an investment portfolio with an
estimated annual growth rate (from the Investment Portfolio section of summary.md),
factor that growth into projections:
- Project future value of existing investments over the goal timeline using:
  `FV = PV × (1 + r)^n` where r = annual rate, n = years
- For ongoing contributions, project using future value of annuity:
  `FV = PMT × [((1 + r)^n - 1) / r]`
- Show the impact: "Your $65k in investments growing at ~8%/yr would be worth ~$X
  in Y years — this accelerates your goal by Z months"
- Distinguish between liquid investments (brokerage, TFSA) that can fund the goal
  vs. locked/retirement accounts (401k, RRSP) that shouldn't be touched
- If the user plans to liquidate investments for the goal, factor in capital gains
  tax implications

### 3. Give a Verdict

Categorize the plan:
- **SAFE**: financially sustainable with buffer
- **STRETCH**: possible but with meaningful trade-offs
- **NOT RECOMMENDED**: high risk or unsustainable

Explain WHY clearly.

### 4. Generate the Plan

Write a goal file to `memory/goals/<goal-name>.md` using the template from
[[templates/goal.md]].

The plan must include:
- Target amount and timeline
- Monthly savings/contribution needed
- Key milestones
- Specific assumptions (listed)
- Concrete action items (top 2-3 highest impact)
- Risks and what-if scenarios
- Confidence level

### 5. Scenario Comparison (when relevant)

Compare options: buy now vs wait, bigger vs smaller, different locations.
Show trade-offs clearly.

### 6. Review

Present the plan to the user. Ask if they want to adjust anything.
Update the goal file with any changes.

### 7. Output Format

**If the user is on Claude Desktop App (claude.ai):** Output the goal plan as
an Artifact (type: `text/html`) titled **"Goal: [name]"**. Build a clean,
visually polished single-page HTML dashboard that includes:
- A header with the goal name and verdict badge (SAFE / STRETCH / NOT RECOMMENDED)
- A summary card showing target amount, timeline, and monthly savings needed
- A progress/milestone timeline visualization
- Sections for assumptions, action items, risks, and scenarios
- Use a modern, minimal design with CSS (no external dependencies). Use a
  cohesive color palette, card-based layout, and clear typography.

**If the user is on Claude Code (CLI/IDE):** Output the plan as formatted
markdown directly in the conversation. Do not attempt to create an artifact.
