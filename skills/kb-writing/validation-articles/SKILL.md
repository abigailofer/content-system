# Validation Articles

---
name: validation-articles
description: Write a knowledge base entry for a single accessibility validation. Use when producing or editing a validation article for the knowledge base.
---

## Quick start
Collect or confirm:
- Validation name (kebab-case slug)
- WCAG success criterion name and number, or `"best practice"` if no SC applies
- Severity level assigned to the issue
- WCAG techniques URL (omit if best practice or no published techniques exist)

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

### Determining entry type
When reviewing an existing article, determine the entry type from the article content — not from supplementary metadata such as "Standards and regulations" labels. Those fields may reference WCAG criteria even for best-practice entries and must not be used to classify the article.

Use these signals from inside the article body:

| Signal | WCAG SC entry | Best practice entry |
|---|---|---|
| Rule modal word | "must" | "should" |
| FAQ item 2 question | "How does this issue relate to SC [name and number]?" | "Why is this rule considered a best practice?" |
| Related WCAG Techniques section | Present | Absent |

If signals conflict, the FAQ item 2 phrasing is the most reliable indicator.

---

## Workflow
1. Verify the validation name as an H2 — lowercase, words separated by hyphens
2. Verify the one-line violation rule in bold — use "must" if a WCAG SC applies; use "should" if best practice
3. Verify the description (50 words maximum per paragraph, no SC name or number, plain language) — if a paragraph exceeds 50 words, suggest the best way to break it into shorter paragraphs
4. Verify Pass Patterns — 1–2 code examples, each preceded by a title; only include examples you are certain about (see Constraints for title format rules) — if a pattern uses the H3 title structure but has no explanation sentence, suggest an appropriate one
5. Verify Fail Patterns — 1–2 code examples, each preceded by a title; only include examples you are certain about (see Constraints for title format rules) — if a pattern uses the H3 title structure but has no explanation sentence, suggest an appropriate one
6. Verify the Related WCAG Techniques section — only if `wcag_sc != "best practice"` AND published techniques exist at `wcag_techniques_url`
7. Verify the Try It Yourself section — H3 subsections per applicable testing method, each with Steps to follow:, Expected results:, and Actual results: — the label and content are on the same line, not separated by a blank line
8. Verify the FAQ — 2 required items plus any additional ones that apply
9. Validate output against [RUBRIC.md](RUBRIC.md) before delivering

---

## Degrees of freedom

- **Fixed:** Section order, H2/H3 heading hierarchy, bold violation rule, required FAQ items 1 and 2
- **Conditional:** Related WCAG Techniques section — include only when `wcag_sc != "best practice"` and published techniques are available
- **Variable:** Number of Try It Yourself subsections (include all applicable testing methods); FAQ item 2 question phrasing; optional additional FAQ items
- **Optional:** ACT Rules section — include after Related WCAG Techniques (or after Fail Patterns for best-practice entries) if ACT Rules apply to the validation. The heading must be exactly "ACT Rules"
- **Optional:** Recommended Reading section — include after FAQ if there are relevant external references. The heading must be exactly "Recommended Reading" — do not use "Learn more", "Related Reading", or any other variant
- **Omit:** Related WCAG Techniques section entirely if no techniques are published at `wcag_techniques_url`

---

## Constraints

| Element | Rule |
|---|---|
| Validation name (H2) | Lowercase, hyphenated, no trailing period |
| One-line violation rule | Bold, exactly 1 sentence, ends with a period |
| "must" vs "should" | Use "must" when a WCAG SC applies; use "should" for best-practice entries |
| Description paragraphs | 50 words maximum per paragraph; no minimum; do not mention SC name or number. The description must answer two questions: what is the issue, and why is it a problem |
| Pass/fail pattern structure | Each code example must be preceded by a title that describes what the example shows. The title format depends on whether an explanation sentence follows: (1) if an explanation sentence is present, the title must be an H3 with no trailing period — it can be a concise noun phrase (for example, "Valid landmark role", "Misspelled role value"); (2) if no explanation sentence is present, the title must be body text (not a heading) and must be a full sentence with a verb in present tense that describes the example — not why it passes or fails (good: "A list contains the required `listitem` children"; bad: "A list with the required `listitem` children" — no verb; "A menu contains a list, which causes a semantics conflict" — explains the failure). Explanation sentences must be used consistently — if any pattern in the section has one, all patterns in that section must have one |
| Code examples | Only include examples you are certain are correct — never speculate |
| ARIA attributes, roles, states, landmark regions, form labels | Wrap in backticks everywhere in prose — including FAQ question text, step-by-step instructions, and headings. Do not use shorthand or abbreviated forms — write `` `aria-allowed-attr` ``, not "Allowed-attr". Do not put ARIA state value names in quotation marks — use backticks instead (for example, `` `aria-checked` ``, not "checked") |
| Bullet points | No period for fragments; period required for full sentences |
| H1 and H2 headings | Title Case (MLA rules) |
| H3 and H4 headings | Sentence case |
| Spelling | American English |
| Tone | Active voice; address the reader as "you"; Grade 9 reading level; no emojis — passive voice is acceptable when rewriting to active would make the sentence longer |
| Em dash | Do not use em dashes (—) in any prose |
| Punctuation | Do not overuse punctuation — especially semicolons (;) and commas (,). Rewrite for clarity using the most logical approach: a conjunction, a restructured sentence, or two shorter sentences |
| Clarity | Writing must be plain, direct, and easy to read. Do not use convoluted sentence structures |

### Capitalization — Title Case (MLA rules)
Capitalize the first and last word and every major word (nouns, pronouns, verbs, adjectives, adverbs). Do not capitalize articles, prepositions, or conjunctions of three letters or fewer unless they start or end the heading.

### Words and phrases to avoid
Write at Grade 9 reading level. Avoid words that are too formal, literary, or academic for everyday use. If a simpler word exists, use it.

Refer to [`shared/words-to-avoid.md`](../../../shared/words-to-avoid.md) for the full list.

### Accessibility terminology
- Use "people with disabilities," not "disabled people"
- Use "screen reader user," not "blind user"
- Use "assistive technology" instead of "screen reader" unless the trait is exclusive to screen readers
- Use "accessible name," not "label" when referring to the computed accessible name
- Use "focus indicator," not "focus outline"
- Use "WCAG success criterion," not "WCAG rule"
- Use "accessibility barrier," not "accessibility problem"
- Use "accessibility issue," not "accessibility error"
- Use "A, AA, AAA," not "Level A, Level AA, Level AAA"

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
