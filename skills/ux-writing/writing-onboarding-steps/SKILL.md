# Writing Onboarding Steps

---
name: writing-onboarding-steps
description: Write clear, motivating onboarding step content for new users. Use when designing first-run experiences, setup wizards, feature tours, or progressive user education flows.
---

## Quick start
Collect or infer:
- Onboarding type (setup wizard, feature tour, contextual tip)
- Total number of steps
- Goal of each step
- User's prior knowledge level

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Define the onboarding goal and step count
2. For each step, identify the single action or concept
3. Write step headline (what to do or learn) — sentence case, no period, no exclamation point
4. Write step body (why it matters or how to do it) — sentence case, ends with period
5. Write action label — title case, no period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: One concept per step is mandatory
- **Medium**: Tone can be enthusiastic for welcome, focused for setup
- **Allowed variation**: Body text length varies by step complexity

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Headline (H2) | Sentence case | No | 50 chars | No exclamation points |
| Body | Sentence case | Yes | 150 chars | One concept per step |
| Action label | Title case | No | 25 chars | Verb + noun preferred; single-word only where step context makes outcome clear |

### Step structure rules
- First step must set expectations — state what the user will accomplish and how long it takes
- Final step must confirm completion and provide a clear next action
- Each step must provide enough context so the user doesn't need to remember details from previous steps (style guide §13.7)
- Never disguise mandatory setup as an optional tour

### Tone rules
- Focus on the user as the actor — avoid centering the product (style guide §13.9)
- Good: "You're ready to review your results"
- Bad: "We're excited to show you what we built"
- Communicate feature value before the flow starts — inside the flow, focus on completing steps, not selling (style guide §13.10)
- Never use exclamation points (style guide §1.7.5)

### CTA label rules for flows (style guide §13.6)
- CTAs must include a verb and a noun to make the outcome clear
- Single-word CTAs like "Continue" or "Next" are acceptable only when surrounding step context makes the outcome unambiguous
- Avoid single-word CTAs on the final step — use a specific label like "Create Project" or "Go to Dashboard"

Good examples:
- "Create Audience"
- "Import Session"
- "Go to Dashboard"

Avoid:
- "Continue" (unless step context is very clear)
- "Next" on the final step
Use questions when gathering information from the user or reflecting what they might be asking:
- "How will you use this service?"
- "What do you need help with?"

Use statements when providing clear, direct instructions:
- "Choose how you'll use this service"
- "Select what you need help with"

### Word choice
- Use "select" not "click" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
