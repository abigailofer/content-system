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

## Workflow
1. Identify empty state type using [reference/empty-state-types.md](reference/empty-state-types.md)
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
- **First-run**: include primary CTA to create or get started
- **No-results**: offer "Clear Filters" or "View All [Items]" to reset
- **User-cleared**: include CTA if user can populate; omit if they cannot
- **Error-caused**: include recovery CTA ("Refresh Page" or "Back to Home")
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
