# Templates: General Articles

---

## Output structure

A rewritten general article has two parts delivered together:
1. The rewritten article
2. A Notes on Rewrite section

Both are required. Refer to [SKILL.md](SKILL.md) for the rules governing each.

---

## Rewritten article template

```markdown
# {{Article Title in Title Case}}

## {{Section heading in sentence case}}

### {{paragraph title in sentence case}}

{{paragraph content — one topic, fewer than 70 words, front-loaded}}

### {{paragraph title in sentence case}}

{{paragraph content}}

```{{language}}
{{code example — include only where certain; add a plain language explanation before the block}}
```

---

## {{Next section heading in sentence case}}

### {{paragraph title}}

{{paragraph content}}

- {{bullet point fragment — no period}}
- {{bullet point fragment — no period}}
- {{complete sentence bullet point.}}

> **Note:** {{self-contained note text prefaced by "Note:"}}

---

## Notes on Rewrite

### Contradictions with accessibility best practices

{{List any information in the original that contradicts current accessibility best practices, with a brief explanation. If none found, write: "No contradictions identified."}}

### Content suggested for removal

{{List any content that appears irrelevant or could be removed, with a brief rationale. If none found, write: "No content flagged for removal."}}

### Major structural changes

{{Describe what was reorganized and why — for example, converting a dense paragraph to a bullet list, splitting a section, or reordering topics for better flow.}}
```

---

## Section and paragraph guidance

### Headings

| Level | Capitalization | Use for |
|---|---|---|
| H1 | Title Case | Article title only |
| H2 | Sentence case | Major sections |
| H3 | Sentence case | Paragraph titles within a section |
| H4 | Sentence case | Sub-paragraphs where needed |

### Lists

| Type | When to use |
|---|---|
| Numbered list | Sequential steps where order matters |
| Bullet list | Non-sequential information, key points, options |

### Code examples

Include a code example when:
- It demonstrates a specific best practice discussed in the paragraph
- The correct implementation would otherwise be unclear from text alone
- You are certain the example is correct

Before each code block, write a short plain language sentence explaining what the code does and why. After the block, explain what the expected result or behavior is, where helpful.

```markdown
{{Plain language explanation of what this example demonstrates.}}

```html
{{code}}
```

{{Optional: what this produces or why it matters.}}
```

### Notes

Use a Note callout for information that is important but would interrupt the main flow if included inline.

```markdown
> **Note:** {{Self-contained note. Starts with "Note:" and contains a complete thought.}}
```

---

## Notes on Rewrite — guidance

The Notes on Rewrite section is not part of the published article. It is a working note for the content team. Keep it factual and brief.

### Contradictions
Flag information that directly contradicts current WCAG guidance or established accessibility best practices. Include:
- What the original said
- Why it is a contradiction
- What the current best practice is

### Content suggested for removal
Flag content that appears outdated, off-topic, or redundant. Do not silently remove content — flag it here so the content team can make the final call.

### Major structural changes
Briefly explain any significant reorganization — for example:
- Sections reordered for logical flow
- Dense paragraphs converted to bullet lists for scannability
- A long section split into two for the 70-word paragraph limit
- New headings added where the original had none
