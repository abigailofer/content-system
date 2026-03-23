# Writing Form Labels and Help Text

---
name: writing-form-labels-and-helptext
description: Write clear form field labels, placeholders, and help text. Use when designing forms, input fields, registration flows, data entry screens, or any UI requiring user input.
---

## Quick start
Collect or infer:
- Field purpose (what data is being collected)
- Input type (text, email, password, select, etc.)
- Required vs. optional status
- Validation rules or format requirements

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Identify the data being collected and its purpose
2. Write the label (what to enter) — sentence case, no period
3. Decide if placeholder is needed (format hint only) — sentence case, no period
4. Write help text if format or constraints exist — sentence case, ends with period
5. Write validation error messages — sentence case, no period
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Labels must be present and visible (not placeholder-only)
- **Medium**: Help text optional if field is self-explanatory
- **Allowed variation**: Placeholder can be omitted if help text covers format

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Label | Sentence case | No | 40 chars | Always visible; never placeholder-only |
| Placeholder | Sentence case | No | 40 chars | Format hint only; never repeats label |
| Help text | Sentence case | Yes | 100 chars | Optional if field is self-explanatory |
| Validation error | Sentence case | No | 80 chars | Specific to what's wrong |

### Placeholder patterns
Follow these approved patterns (style guide §11.7.5):

| Field type | Pattern | Example |
|-----------|---------|---------|
| Text field | `Enter {name}` | `Enter project name` |
| Description/textarea | `Describe the {collection}` | `Describe the test scenario` |
| Email | Use example format | `name@example.com` |
| Select/dropdown | `Select {property}` | `Select country` |
| Search | `Search {item}` | `Search campaigns` |

### Label rules
- Labels are nouns or noun phrases — never instructions or verbs
- Good: "Country", "Email address", "Full name"
- Bad: "Select country", "Enter your email", "Type your name"
- Singular and lowercase (sentence case)
- No trailing period

### Required/optional indicators
- Required fields are marked with a red asterisk (*)
- Optional fields have no indicator
- Never use "(optional)" or "(required)" text labels

### Accessibility note
Explicit labels improve screen reader navigation. Clear placeholders help users understand expected formats without adding extra cognitive load. Labels must always be programmatically associated with their input (style guide §11.7, WCAG 3.3.2).

### Word choice
- Use "select" not "click" in help text (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Glossary: [../../reference/glossary.md](../../reference/glossary.md)
- Words to use: [../../reference/words-to-use.md](../../reference/words-to-use.md)
- Words to avoid: [../../reference/words-to-avoid.md](../../reference/words-to-avoid.md)
