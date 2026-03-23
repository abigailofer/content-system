# Writing Settings and Preferences

---
name: writing-settings-and-preferences
description: Write clear labels and descriptions for settings and preferences UI. Use when creating settings screens, preference panels, toggles, configuration options, or feature flags exposed to users.
---

## Quick start
Collect or infer:
- Setting category (account, notifications, privacy, appearance, etc.)
- Setting type (toggle, select, input, action)
- Default state
- Impact of changing the setting

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Identify the setting category and type
2. Write the label (what the setting controls) — sentence case, no period
3. Write the description (what happens when enabled/changed) — sentence case, ends with period
4. Specify the default value
5. Add helper text for complex settings — sentence case, ends with period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Label + description structure is fixed
- **Medium**: Description length varies by complexity
- **Allowed variation**: Description can be omitted for self-explanatory settings

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Label | Sentence case | No | 40 chars | Noun or noun phrase; never an instruction |
| Description | Sentence case | Yes | 120 chars | Explains effect; optional if self-explanatory |
| Action label | Title case | No | 25 chars | Verb + noun |
| Placeholder | Sentence case | No | 40 chars | Follow approved patterns |
| Helper text | Sentence case | Yes | 100 chars | Format requirements or constraints |

### Toggle and checkbox rules
- Labels describe the ON state — never the OFF state (style guide §11.5.1)
- Phrase labels positively — never use double negatives
- Good: "Email notifications" (ON = you get emails)
- Bad: "Disable email notifications" (ON = you don't get emails)
- Use "turn on / turn off" not "enable / disable" in descriptions (style guide §7.1)

### Destructive settings
- Always require confirmation before executing
- Use "You cannot undo this action" — never "This can't be undone"
- Follow the confirmation dialog pattern — see writing-confirmation-dialogs skill
- Use destructive button styling on the action label

### Link text in descriptions
- Never use "Learn more" as link text (style guide §4.3.3)
- Always describe the destination: "Learn about API rate limits"

### Word choice
- Use "select" not "click" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Confirmation dialogs: [../writing-confirmation-dialogs/SKILL.md](../writing-confirmation-dialogs/SKILL.md)
