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

---

## Workflow
1. Verify the validation name as an H2 — lowercase, words separated by hyphens
2. Verify the one-line violation rule in bold — use "must" if a WCAG SC applies; use "should" if best practice
3. Verify the description (~50 words per paragraph, no SC name or number, plain language)
4. Verify Pass Patterns — 1–2 code examples, each preceded by a short explanation; only include examples you are certain about
5. Verify Fail Patterns — 1–2 code examples, each preceded by a short explanation; only include examples you are certain about
6. Verify the Related WCAG Techniques section — only if `wcag_sc != "best practice"` AND published techniques exist at `wcag_techniques_url`
7. Verify the Try It Yourself section — H3 subsections per applicable testing method, each with Steps to follow:, Expected results, and Actual results
8. Verify the FAQ — 2 required items plus any additional ones that apply
9. Validate output against [RUBRIC.md](RUBRIC.md) before delivering

---

## Degrees of freedom

- **Fixed:** Section order, H2/H3 heading hierarchy, bold violation rule, required FAQ items 1 and 2
- **Conditional:** Related WCAG Techniques section — include only when `wcag_sc != "best practice"` and published techniques are available
- **Variable:** Number of Try It Yourself subsections (include all applicable testing methods); FAQ item 2 question phrasing; optional additional FAQ items
- **Omit:** Related WCAG Techniques section entirely if no techniques are published at `wcag_techniques_url`

---

## Constraints

| Element | Rule |
|---|---|
| Validation name (H2) | Lowercase, hyphenated, no trailing period |
| One-line violation rule | Bold, exactly 1 sentence, ends with a period |
| "must" vs "should" | Use "must" when a WCAG SC applies; use "should" for best-practice entries |
| Description paragraphs | ~50 words each; no paragraph exceeds 70 words; do not mention SC name or number |
| Code examples | Only include examples you are certain are correct — never speculate |
| ARIA attributes, roles, states, landmark regions, form labels | Wrap in backticks |
| Attribute references in prose | Always include the word "attribute" when referring to an HTML or ARIA attribute in prose — for example, "the `alt` attribute", not "the `alt`" |
| Bullet points | No period for fragments; period required for full sentences |
| H1 and H2 headings | Title Case (MLA rules) |
| H3 and H4 headings | Sentence case |
| Spelling | American English |
| Tone | Active voice; address the reader as "you"; Grade 9 reading level; no emojis |

### Capitalization — Title Case (MLA rules)
Capitalize the first and last word and every major word (nouns, pronouns, verbs, adjectives, adverbs). Do not capitalize articles, prepositions, or conjunctions of three letters or fewer unless they start or end the heading.

### Words and phrases to avoid
Do not use: Additionally, Bespoke, Comprehensive, Curate, Cutting-edge, Delve into, e.g. / i.e. (use "for example", "such as", or "like"), Effortlessly, Empower/Empowering, etc. (use "and so on"), Foster, Furthermore, Harness, Holistic approach, In the realm of, In today's fast-paced world, Indeed, Innovative solutions, It's important to understand that, It's worth noting that, Leverage, Moreover, Myriad (of), Navigate (challenges), Optimal/Optimize, Paradigm shift, Plethora (of), Robust (unless referring to WCAG), Seamless/Seamlessly, See/Open (use "refer to"), Show (use "indicate"), Streamline, Synergy/Synergistic, Undoubtedly, Utilize (use "use").

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
