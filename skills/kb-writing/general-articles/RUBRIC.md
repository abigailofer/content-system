# Rubric: General Articles

---

## Pass if all are true

### Content
- [ ] All technical information from the original article is preserved
- [ ] No substantial new content added beyond clarifications, code examples, and use cases
- [ ] Code examples are included only where the writer is certain they are correct — no speculation
- [ ] Real-world use cases are included where they help illustrate a concept
- [ ] Technical terms are explained in plain language on first use
- [ ] Any contradictions with current accessibility best practices are flagged in Notes on Rewrite
- [ ] Any irrelevant content is flagged for removal in Notes on Rewrite — not silently deleted

### Structure
- [ ] H1 headings use Title Case (MLA rules)
- [ ] H2, H3, and H4 headings use sentence case
- [ ] Each paragraph has a descriptive title for scannability
- [ ] No paragraph exceeds 70 words
- [ ] Each paragraph covers only one topic
- [ ] Numbered lists are used for sequential steps
- [ ] Bullet points are used for non-sequential information
- [ ] Information is front-loaded — key content appears at the start of sentences and paragraphs

### Style
- [ ] ARIA attributes, roles, states, landmark regions, and form labels are wrapped in backticks
- [ ] No periods at the end of bullet-point fragments
- [ ] Periods present on bullet points that are full sentences
- [ ] American English spelling used throughout
- [ ] Reading level is approximately Grade 9
- [ ] No banned words from SKILL.md word list
- [ ] Link text is descriptive — no "click here" or "see here"
- [ ] Note text is in a self-contained callout prefaced by "Note:"

### Tone
- [ ] Active voice used throughout
- [ ] "You" addresses the reader directly
- [ ] Guidance favored over mandates — no "you must", "you need to", "you have to"
- [ ] Actions are framed as recommendations or explained with their benefit
- [ ] Tone is professional and conversational — not overly technical or overly casual
- [ ] No emojis

### Accessibility terminology
- [ ] "People with disabilities," not "disabled people"
- [ ] "Assistive technology" preferred over "screen reader" unless the trait is screen-reader-specific
- [ ] "Accessible name," not "label" for the computed accessible name
- [ ] "Focus indicator," not "focus outline"
- [ ] "WCAG success criterion," not "WCAG rule"
- [ ] "Accessibility issue," not "accessibility error"
- [ ] "A, AA, AAA," not "Level A, Level AA, Level AAA"

### Notes on Rewrite section
- [ ] Notes on Rewrite section is present at the end of the article
- [ ] Contradictions with accessibility best practices are listed (or noted as none found)
- [ ] Content suggested for removal is listed (or noted as none found)
- [ ] Major structural changes are described with a brief rationale

---

## Fail if any are true

### Content
- [ ] Technical information from the original has been removed without flagging it in Notes on Rewrite
- [ ] Substantial new content added that goes beyond clarifications, examples, and use cases
- [ ] A code example is speculative or incorrect
- [ ] Terminology contradicts the style guide

### Structure
- [ ] H2, H3, or H4 headings use Title Case instead of sentence case
- [ ] A paragraph exceeds 70 words
- [ ] A paragraph covers more than one topic
- [ ] Sequential steps use bullet points instead of a numbered list

### Style
- [ ] ARIA terms appear without backticks
- [ ] Periods appear at the end of bullet-point fragments
- [ ] British English spelling used ("cancelled", "labelled", "pop-up", and so on)
- [ ] Banned words from SKILL.md word list appear in the output
- [ ] Link text is non-descriptive ("click here", "learn more", and so on)

### Tone
- [ ] Directives used instead of guidance ("you must", "you need to", "you have to")
- [ ] Tone is condescending or overly casual
- [ ] Passive voice used without a clear reason

### Notes on Rewrite section
- [ ] Notes on Rewrite section is missing
- [ ] A contradiction with best practices is present in the article but not flagged
- [ ] Content was silently removed without noting it in Notes on Rewrite

---

## Pre-ship checklist
Run before delivering any rewritten article:

- [ ] All original technical information retained or flagged if removed
- [ ] Code examples are certain — no speculation
- [ ] H1 uses Title Case; H2–H4 use sentence case
- [ ] Each paragraph has a title; no paragraph exceeds 70 words
- [ ] Guidance tone used throughout — no mandates
- [ ] ARIA terms wrapped in backticks
- [ ] American English spelling; Grade 9 reading level
- [ ] No banned words
- [ ] Notes on Rewrite section present and complete
