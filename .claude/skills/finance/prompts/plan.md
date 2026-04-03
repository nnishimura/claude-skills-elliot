# Goal Planning Flow

Help the user create a concrete financial plan for a life goal.

## Prerequisites

Read `~/.finance/summary.md` and `~/.finance/profile.md`. If either is missing,
tell the user to run `/finance setup` first.

Also read any existing goals: glob `~/.finance/goals/*.md` and read them to
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

### 3. Give a Verdict

Categorize the plan:
- **SAFE**: financially sustainable with buffer
- **STRETCH**: possible but with meaningful trade-offs
- **NOT RECOMMENDED**: high risk or unsustainable

Explain WHY clearly.

### 4. Generate the Plan

Write a goal file to `~/.finance/goals/<goal-name>.md` using the template from
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
