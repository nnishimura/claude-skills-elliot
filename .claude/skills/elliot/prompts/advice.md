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

**If the user is on Claude Desktop App (claude.ai):** Output the advice as
an Artifact (type: `text/html`) titled **"Advice: [topic]"**. Build a clean,
visually polished single-page HTML dashboard that includes:
- A header with the topic and a verdict badge (clear recommendation)
- A summary card with the direct answer and key numbers from their data
- A supporting calculations section showing the math behind the recommendation
  (income vs. expense impact, goal timeline effects, rate comparisons, etc.)
- A trade-offs section quantifying what they'd gain vs. give up
- An action items checklist with concrete next steps
- Use a modern, minimal design with CSS (no external dependencies). Use a
  cohesive color palette, card-based layout, and clear typography.

**If the user is on Claude Code (CLI/IDE):** Output the advice as formatted
markdown directly in the conversation. Do not attempt to create an artifact.
Structure it as:
1. **Direct answer** (don't bury the recommendation)
2. **Why** (brief reasoning with numbers from their data)
3. **Trade-offs** (what they'd give up)
4. **Action items** (concrete next steps)
