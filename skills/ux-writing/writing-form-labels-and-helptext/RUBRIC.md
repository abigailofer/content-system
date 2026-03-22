# Rubric: Writing Form Labels and Help Text

---

## Pass if all are true
- [ ] Every field has a visible label (not placeholder-only)
- [ ] Label is a noun or noun phrase — not an instruction or verb phrase
- [ ] Label clearly states what to enter
- [ ] Label is ≤40 characters
- [ ] Label uses sentence case
- [ ] Label has no trailing period
- [ ] Placeholder (if present) is a format hint, not the label
- [ ] Placeholder is ≤40 characters
- [ ] Placeholder uses sentence case
- [ ] Placeholder has no trailing period
- [ ] Select/dropdown labels are singular and lowercase (style guide §11.6.1)
- [ ] Select/dropdown placeholders follow the pattern "Select {property}" with no article
- [ ] Help text (if present) adds useful information not in label
- [ ] Help text is ≤100 characters
- [ ] Help text uses sentence case and ends with a period
- [ ] Required fields are marked with a red asterisk (*)
- [ ] Optional fields have no indicator
- [ ] Validation errors are specific to what's wrong
- [ ] Validation errors are ≤80 characters
- [ ] Validation errors use sentence case
- [ ] Validation errors have no trailing period

---

## Fail if any are true
- [ ] Field relies on placeholder as only label
- [ ] Label is an instruction or verb phrase ("Select country", "Enter your email")
- [ ] Label is vague ("Input", "Enter value")
- [ ] Label uses title case or has a trailing period
- [ ] Placeholder repeats the label ("Email" placeholder on Email field)
- [ ] Placeholder doesn't follow approved patterns (Enter {name}, Select {property}, Describe the {collection}, Search {item})
- [ ] Select/dropdown label is plural or uses title case
- [ ] Select/dropdown placeholder includes an article ("Select a country")
- [ ] Placeholder uses title case or has a trailing period
- [ ] Help text repeats label or placeholder
- [ ] Help text is missing a trailing period
- [ ] Required fields not marked with a red asterisk
- [ ] Optional fields marked with any indicator
- [ ] Validation error is generic ("Invalid input")
- [ ] Validation error has a trailing period
- [ ] Character limits exceeded
- [ ] Label uses unnecessary articles ("The email address")
- [ ] Placeholder shows fake data that looks real ("John Smith")
