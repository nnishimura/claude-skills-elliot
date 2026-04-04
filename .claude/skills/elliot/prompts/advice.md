# Advice Flow

Answer the user's financial question grounded in their actual data.

## Prerequisites

Load the user's financial context (see SKILL.md Context Loading):
1. Try reading `.finance/summary.md`, `.finance/profile.md`, and all files in
   `.finance/goals/`
2. If files don't exist, check for financial data shared earlier in the
   conversation (Artifacts or pasted text)
3. Proceed even if some context is missing, but note what you're lacking

## Guidelines

- Ground every answer in the user's real numbers from summary.md
- Be opinionated: give a clear recommendation, not "it depends"
- Consider impact on existing goals
- Think about both short-term and long-term consequences
- If the question involves a trade-off, quantify both sides
- If you need more context, ask (max 2 questions)

## Common Questions to Handle Well

- "Can I afford X?" → Calculate against disposable income + impact on goals
- "Should I pay off debt or invest?" → Compare rates, consider risk tolerance
- "What should I do with $X?" → Prioritize: emergency fund → high-interest debt → goals → invest
- "Should I change jobs for $X more?" → Consider total comp, benefits, stability, commute cost
- "How much house can I afford?" → Use the planning framework from references/planning.md

## Response Format

1. **Direct answer** (don't bury the recommendation)
2. **Why** (brief reasoning with numbers from their data)
3. **Trade-offs** (what they'd give up)
4. **Action items** (concrete next steps)
