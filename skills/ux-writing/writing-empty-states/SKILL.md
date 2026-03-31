# Writing Empty States

---
name: writing-empty-states
description: Write helpful, actionable empty state messages for UI. Use when displaying screens with no data, first-run experiences, zero results, or cleared content states.
---

## Quick start
Collect or infer:
- Empty state type (first-run, no-results, user-cleared, error-caused)
- What content would normally appear here
- User's likely goal or task
- Available actions to populate the state

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Interaction protocol
When the user sends a screenshot for review or asks for empty state copy, always follow these steps before writing anything:

**Step 1** — Show the user this list and ask which use case applies:
1. New user, first time using a feature
2. User searches and gets no results
3. User deleted all items or marked everything as done
4. Error

**Step 2** — Once the user selects a category, show the relevant sublist and ask which sub-case applies:
- If 1: Ask if it's 1a (user can act directly, with CTA) or 1b (user must act elsewhere or wait, no CTA)
- If 2: Ask if it's 2a (search or filter returned nothing) or 2b (possible typo — corrected query available)
- If 3: Ask if it's 3a (user can create more, with CTA) or 3b (user cannot add content themselves, no CTA)
- If 4: Ask if it's 4a (retry available) or 4b (back to home is better recovery)

**Step 3** — Once the sub-case is confirmed, proceed to analyze the screenshot or write copy using the correct template and examples.

Do not skip steps or combine them. Do not attempt to infer the use case from the screenshot without asking first.

---

## Workflow
1. Follow the interaction protocol above to identify the correct use case
2. Determine what the user expects to see
3. Write the headline (acknowledge the state) — sentence case, no period
4. Write supporting text (explain or guide) — sentence case, ends with period unless ending with a link
5. Provide primary action if applicable — title case, no period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Structure (headline + support + action) is fixed
- **Medium**: Tone can be warmer for first-run, neutral for no-results
- **Allowed variation**: Support text optional if action is self-explanatory

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Headline (usually H2) | Sentence case | No | 50 chars | Required in all empty states; heading level depends on page structure |
| Support text | Sentence case | Yes — unless ending with a link | 120 chars | Optional if action is self-explanatory |
| Action label | Title case | No | 25 chars | Omit if user cannot take action |

### Approved single-word action label exceptions
The following single-word labels are approved without a noun:
- Save
- Done
- Apply
- Delete
- Remove
- Archive
- Discard
- Edit
- Retry

### Support contact copy
- Button: "Contact Support" (title case, no brand name)
- Inline text: "Contact Evinced Support"
- Never: "Contact us", "Get help", "Support"
- **First-run 1a (with CTA)**: include primary CTA to create or get started
- **First-run 1b (no CTA)**: omit CTA; support text either guides user to take action elsewhere in the product, or sets expectation that content will appear here
- **No-results 2a**: offer "Clear Filters" or "View All [Items]" to reset
- **No-results 2b**: offer corrected query as CTA
- **User-cleared 3a**: include CTA to create or get started
- **User-cleared 3b**: omit CTA; support text sets expectation
- **Error-caused 4a**: include "Refresh Page" CTA
- **Error-caused 4b**: include "Back to Home" CTA
- **No action possible**: omit action entirely; use support text to set expectation

### Word choice
- Use "select" not "click" in support text (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Empty state types: [reference/empty-state-types.md](reference/empty-state-types.md)
- Glossary: [../../reference/glossary.md](../../reference/glossary.md)
- Words to use: [../../reference/words-to-use.md](../../reference/words-to-use.md)
- Words to avoid: [../../reference/words-to-avoid.md](../../reference/words-to-avoid.md)
