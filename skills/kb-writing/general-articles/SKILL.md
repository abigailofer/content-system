# General Articles

---
name: general-articles
description: Rewrite an existing accessibility article to meet style, tone, and content guidelines. Use when an article needs to be revised for clarity, structure, terminology, or reading level — not when writing a new article from scratch.
---

## Quick start
Collect or confirm:
- The original article (full text)
- Any specific focus areas or sections to prioritize

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Read the original article in full before making any changes
2. Identify content to preserve, restructure, enhance, or flag
3. Rewrite following the style, tone, and structure rules below
4. Add code examples where they improve understanding — only where you are certain they are correct
5. Add real-world use cases to illustrate why a technique matters
6. Clarify technical terms with plain language explanations on first use
7. Improve headings for scannability
8. Convert dense paragraphs to bullet points where content is non-sequential
9. Write the Notes on Rewrite section
10. Validate output against [RUBRIC.md](RUBRIC.md) before delivering

---

## Degrees of freedom

- **Fixed:** Style rules, tone, heading capitalization, terminology, Notes on Rewrite section
- **Allowed:** Reorganize content if it improves clarity; convert paragraphs to bullets; improve headings; break complex steps into sequences
- **Enhance with:** Code examples (correct only), real-world use cases, plain language explanations of technical terms, analogies for complex concepts
- **Not allowed:** Adding substantial new content beyond clarifications and examples; removing technical information; making content overly basic; using terminology that contradicts the style guide

---

## Constraints

| Element | Rule |
|---|---|
| H1 headings | Title Case (MLA rules) |
| H2, H3, H4 headings | Sentence case |
| Bullet points | No period for fragments; period required for full sentences |
| ARIA attributes, roles, states, landmark regions, form labels | Wrap in backticks |
| Code examples | Only include where certain — never speculate |
| Spelling | American English |
| Reading level | Grade 9 |
| Tone | Guidance over mandates — see Tone section below |

### Capitalization — Title Case (MLA rules)
Capitalize the first and last word and every major word (nouns, pronouns, verbs, adjectives, adverbs). Do not capitalize articles, prepositions, or conjunctions of three letters or fewer unless they start or end the heading.

### Tone
Write as a knowledgeable guide, not a gatekeeper. Favor recommendations over directives.

- Avoid: "you need to", "you must", "you have to"
- Prefer: "It's a good practice to...", "We recommend...", "Consider doing X to achieve Y", "You can achieve this by...", "One way to approach this is..."
- Explain the benefit or outcome of an action rather than just mandating it
- Use practical framing: "Here's how this benefits real users..."
- Use analogies to explain complex concepts
- Balance technical terms with plain language explanations
- Maintain optimism about accessibility implementation

**Sample tone reference:**

| | Example |
|---|---|
| Too technical | "The `aria-expanded` attribute must be dynamically toggled to `true` when the controlled element is visible and to `false` when collapsed." |
| Too casual | "Just flip the `aria-expanded` thingy to true or false depending on if your stuff is showing or not!" |
| Correct | "When your menu opens, set `aria-expanded='true'` so screen readers announce this change to users. When it closes, update it to `aria-expanded='false'`. This keeps all users informed about the current state." |

### Structure
- Add a short, descriptive title to each paragraph for scannability
- Front-load information — put the most important content at the start of each sentence or paragraph
- One topic per paragraph; paragraphs must be fewer than 70 words
- Use numbered lists for sequential steps; bullet points for non-sequential information
- Vary sentence beginnings and lengths to avoid a monotonous rhythm
- Note text goes in a self-contained callout prefaced by "Note:"

### Words and phrases to avoid
Write at Grade 9 reading level. Avoid words that are too formal, literary, or academic for everyday use. If a simpler word exists, use it.

Refer to [`shared/words-to-avoid.md`](../../../shared/words-to-avoid.md) for the full list.

### Accessibility terminology
- Use "people with disabilities," not "disabled people"
- Use "screen reader user," not "blind user"
- Use "assistive technology" instead of "screen reader" unless the trait is exclusive to screen readers
- Use "accessible name," not "label" when referring to the computed accessible name
- Use "focus indicator," not "focus outline"
- Use "alt text" or "alternative text," not "image description"
- Use "tab sequence," not "focus sequence"
- Use "interactive element," not "clickable element"
- Use "color contrast ratio," not "contrast level"
- Use "keyboard focus," not "tab focus"
- Use "landmark region," not "ARIA section"
- Use "skip link," not "skip navigation"
- Use "WCAG success criterion," not "WCAG rule"
- Use "accessibility barrier," not "accessibility problem"
- Use "accessibility issue," not "accessibility error"
- Use "A, AA, AAA," not "Level A, Level AA, Level AAA"
- Use "automated testing," not "automated checking"
- Use "manual testing," not "human testing"

### Notes on Rewrite section
Every rewritten article must end with a "Notes on Rewrite" section covering three things:
1. **Contradictions** — any information in the original that contradicts current accessibility best practices
2. **Suggested removals** — any content that appears irrelevant or could be removed
3. **Major structural changes** — what was reorganized and why

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
