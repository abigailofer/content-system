# Rubric: Validation Articles

---

## Pass if all are true

### Structure
- [ ] Validation name is H2, lowercase, hyphenated, with no trailing period
- [ ] One-line violation rule is bold and exactly one sentence ending with a period
- [ ] Rule uses "must" when a WCAG success criterion applies
- [ ] Rule uses "should" when the entry is a best practice
- [ ] Description does not mention the SC name or number
- [ ] Each description paragraph is approximately 50 words and does not exceed 70 words
- [ ] Pass Patterns section includes 1–2 code examples, each preceded by an explanation
- [ ] Fail Patterns section includes 1–2 code examples, each preceded by an explanation
- [ ] No code example is speculative — all examples are included with full certainty
- [ ] Related WCAG Techniques section is present when `wcag_sc != "best practice"` and published techniques exist
- [ ] Related WCAG Techniques section is absent when the entry is a best practice
- [ ] Related WCAG Techniques section includes Sufficient techniques and Failure techniques subsections
- [ ] Advisory techniques subsection is present if advisory techniques exist; if missing on a non-best-practice entry, it is flagged for review
- [ ] Each WCAG technique is a linked box with the technique name as the link text
- [ ] Try It Yourself heading uses Title Case
- [ ] Each Try It Yourself method is an H3 in sentence case
- [ ] Each Try It Yourself method has Steps to follow:, Expected results, and Actual results
- [ ] FAQ item 1 asks "Why is this issue marked as {severity}?"
- [ ] FAQ item 2 asks "How does this issue relate to SC [SC name and number]?" (WCAG entries)
- [ ] FAQ item 2 asks "Why is this rule considered a best practice?" (best-practice entries)

### Style
- [ ] ARIA attributes, roles, states, landmark regions, and form labels are wrapped in backticks
- [ ] Attribute references in prose include the word "attribute" — for example, "the `alt` attribute", not "the `alt`"
- [ ] No periods at the end of bullet-point fragments
- [ ] Periods present on bullet points that are full sentences
- [ ] H1 and H2 headings use Title Case (MLA rules)
- [ ] H3 and H4 headings use sentence case
- [ ] American English spelling throughout
- [ ] Active voice used throughout; "you" addresses the reader
- [ ] Grade 9 reading level maintained
- [ ] No banned words from SKILL.md word list

---

## Fail if any are true

### Structure
- [ ] Validation name uses Title Case, contains spaces, or has a trailing period
- [ ] One-line rule is not bold, is more than one sentence, or is missing a trailing period
- [ ] Rule uses "must" for a best-practice entry
- [ ] Rule uses "should" for a WCAG SC entry
- [ ] Description mentions the SC name or number
- [ ] Any description paragraph exceeds 70 words
- [ ] A code example is speculative or uncertain
- [ ] Related WCAG Techniques section appears in a best-practice entry
- [ ] Related WCAG Techniques section is missing from a WCAG SC entry that has published techniques
- [ ] Try It Yourself heading is not Title Case
- [ ] A Try It Yourself subsection is missing Steps to follow:, Expected results, or Actual results
- [ ] FAQ item 1 is missing or incorrectly phrased
- [ ] FAQ item 2 is missing, incorrectly phrased, or uses the wrong phrasing variant for the entry type

### Style
- [ ] ARIA terms appear without backticks
- [ ] An attribute is referenced in prose without the word "attribute" — for example, "the `alt`" instead of "the `alt` attribute"
- [ ] Periods appear at the end of bullet-point fragments
- [ ] H3 or H4 headings use Title Case instead of sentence case
- [ ] British English spelling used ("cancelled", "labelled", "pop-up", and so on)
- [ ] Passive voice used without a clear reason
- [ ] Banned words from SKILL.md word list appear in the output

---

## Pre-ship checklist
Run before delivering any validation article:

- [ ] Validation name is H2, lowercase, hyphenated
- [ ] One-line rule is bold; "must" vs "should" matches the entry type
- [ ] Description avoids SC name and number; each paragraph is 70 words or fewer
- [ ] All code examples are certain — no speculation included
- [ ] Related WCAG Techniques section included only when applicable; technique boxes are linked
- [ ] Try It Yourself has an H3 per testing method with Steps to follow:, Expected results, and Actual results
- [ ] Both required FAQ items are present and use the correct phrasing for the entry type
- [ ] ARIA terms are wrapped in backticks
- [ ] American English spelling used throughout
- [ ] No banned words present
