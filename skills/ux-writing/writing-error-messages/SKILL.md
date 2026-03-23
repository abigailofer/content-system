# Writing Error Messages

---
name: writing-error-messages
description: Write clear, actionable error messages for UI. Use when users encounter validation failures, system errors, connection problems, or any state where something went wrong.
---

## Quick start
Collect or infer:
- Error type (validation, system, network, permission, not-found)
- Severity (blocking, degraded, informational)
- User action that triggered error
- Available recovery actions

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Classify error using [reference/error-categories.md](reference/error-categories.md)
2. Identify what the user was trying to do
3. Write the error title (what happened) — sentence case, no period
4. Write the body (why it happened, if helpful) — sentence case, ends with period
5. Write the action (how to fix it) — title case, no period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Error structure (title + body + action) is fixed
- **Medium**: Tone adjusts by severity per [reference/error-categories.md](reference/error-categories.md)
- **Allowed variation**: Body can be omitted if cause is obvious and action is clear

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Title (H2) | Sentence case | No | 60 chars | States what went wrong in user terms |
# H1 uniqueness
- If an error message appears on a full page with an H1, the H1 must be unique across all pages — flag if it matches a known page title and ask the user to confirm uniqueness if unsure
| Body | Sentence case | Yes | 150 chars | Optional if cause and fix are obvious |
| Action label | Title case | No | 25 chars | Omit if no recovery action exists |

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
- Dismiss

### Support contact copy
- Button: "Contact Support" (title case, no brand name)
- Inline text: "Contact Evinced Support"
- Never: "Contact us", "Get help", "Support"
Must be:
- Neutral
- Direct
- Calm
- Action-oriented

Avoid:
- Humor
- Drama
- Over-apologizing
- Vague statements without a next step
- The word "failure"
- "Something went wrong" — always specify what failed instead

### Word choice
- Use "select" not "click" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)
- Never expose technical details (stack traces, error codes, exception text)
- Never blame the user

### Validation error patterns
- Missing required field → `Enter {field}`
- Missing selection → `Select {option}`
- Range/limit exceeded → `Select up to {n} {items}`
- Character limit → `{Name} can't be longer than {n} characters`
- Invalid characters → `{Field} can't contain {restriction}`
- Format required → `{Field} must be {format}`
- Already exists → `{Name} already exists`
- Dependency gating → `You need to {required action} before you can {attempted action}`

### System error toast pattern
`Failed to {action} {object}`
Examples:
- "Failed to save changes."
- "Failed to load results."

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Error categories: [reference/error-categories.md](reference/error-categories.md)
