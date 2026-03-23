# Writing Confirmation Dialogs

---
name: writing-confirmation-dialogs
description: Write clear confirmation dialogs for user actions. Use when users trigger irreversible actions, destructive operations, or significant state changes that require explicit consent.
---

## Quick start
Collect or infer:
- Action being confirmed
- Reversibility (reversible, hard to reverse, irreversible)
- Impact scope (single item, multiple items, account-wide)
- Consequences of proceeding

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Classify the action's severity and reversibility
2. Write the headline (what will happen) — sentence case, no period
3. Write the body (consequences, if not obvious) — sentence case, ends with period
4. Write confirm button (specific verb matching action) — title case, no period
5. Write cancel button (safe exit) — title case, no period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Structure (headline + body + confirm + cancel) is fixed
- **Medium**: Body length varies by complexity of consequences
- **Allowed variation**: Body can be omitted for simple reversible actions

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Headline (H2) | Sentence case | No | 60 chars | Must state what will happen |
| Body | Sentence case | Yes | 200 chars | Optional for simple reversible actions |
| Confirm button | Title case | No | 20 chars | Must be specific verb; not "Yes", "OK", "Confirm", "Submit" |
| Cancel button | Title case | No | 15 chars | Must provide safe exit |

### Approved single-word confirm button exceptions
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

### CTA and modal title correlation
- The modal title must match or closely reflect the CTA that launched it
- Small variation is allowed to add context, but the core action must be the same
- Good: CTA "Add to Jira" → modal title "Add issue to Jira"
- Bad: CTA "Add to Jira" → modal title "Create Jira issue"
- Cancel
- Quit *(when all progress will be lost)*
- Stop *(when progress is saved but activity ends)*
- Keep [item] *(when it's clearer than "Cancel")*

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Glossary: [../../reference/glossary.md](../../reference/glossary.md)
- Words to use: [../../reference/words-to-use.md](../../reference/words-to-use.md)
- Words to avoid: [../../reference/words-to-avoid.md](../../reference/words-to-avoid.md)
