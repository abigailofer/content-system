# Templates: Validation Articles

---

## Article structure

Use the following template for every validation article. Refer to [SKILL.md](SKILL.md) for the rules governing each conditional section.

**Pattern title structures — choose one and apply it consistently within each section:**

- **Structure A:** Title is an H3 (no trailing period), followed by one explanation sentence, then the code block. The title may be a noun phrase.
- **Structure B:** Title is body text (no heading), a full sentence with a present-tense verb that describes the example, followed directly by the code block. No explanation sentence.

**Conditional sections:**

- **Related WCAG Techniques** — include only when `wcag_sc != "best practice"` and published techniques exist.
- **Advisory techniques subsection** — include if advisory techniques exist; if none are known, omit and flag for review.
- **ACT Rules** — optional. Include after Related WCAG Techniques (or after Fail Patterns for best-practice entries) if ACT Rules apply. The heading must be exactly "ACT Rules".
- **Recommended Reading** — optional. Include only if relevant external references exist.

**Review suggestions:**

- If a description paragraph exceeds 50 words, suggest the best way to break it into shorter paragraphs.
- If a Pass or Fail pattern uses an H3 title but has no explanation sentence, suggest an appropriate one.

---

## Full article template

~~~markdown
## {{validation_name}}

**{{violation_rule}}**

{{description_paragraph_1}}

{{description_paragraph_2_if_needed}}

### Pass Patterns

#### {{pass_pattern_title}}

{{pass_pattern_explanation}}

```html
{{pass_pattern_code}}
```

### Fail Patterns

#### {{fail_pattern_title}}

{{fail_pattern_explanation}}

```html
{{fail_pattern_code}}
```

### Related WCAG Techniques

#### Sufficient techniques

[{{technique_name}}]({{technique_url}})

#### Advisory techniques

[{{technique_name}}]({{technique_url}})

#### Failure techniques

[{{technique_name}}]({{technique_url}})

### ACT Rules

[{{act_rule_title}}]({{act_rule_url}})

### Try It Yourself

#### {{testing_method_1}}

**Steps to follow:**
1. {{step_1}}
2. {{step_2}}
3. {{step_3}}

**Expected results:** {{expected_result}}

**Actual results:** {{actual_result}}

#### {{testing_method_2_if_applicable}}

**Steps to follow:**
1. {{step_1}}
2. {{step_2}}

**Expected results:** {{expected_result}}

**Actual results:** {{actual_result}}

### FAQ

**Why is this issue marked as {{severity}}?**

{{severity_explanation}}

**How does this issue relate to SC {{wcag_sc}}?**

{{wcag_sc_explanation}}

### Recommended Reading

- [{{reference_title}}]({{reference_url}})
~~~

---

## Variable reference

| Variable | Description | Format |
|---|---|---|
| `{{validation_name}}` | The slug for this validation | Lowercase, hyphenated — for example, `placeholder-as-label` |
| `{{violation_rule}}` | The one-line rule statement | Bold, 1 sentence, ends with a period; "must" for WCAG SC, "should" for best practice |
| `{{description_paragraph_1}}` | Explanation of the validation | 50 words maximum per paragraph; no SC name or number; plain language |
| `{{wcag_sc}}` | SC name and number | For example, `1.3.1 Info and Relationships` |
| `{{severity}}` | The assigned severity level | As assigned in the validation record |
| `{{wcag_techniques_url}}` | URL to the WCAG techniques page | Only used when `wcag_sc != "best practice"` |

---

## Conditional logic at a glance

| Entry type | Related WCAG Techniques section | Rule modal word | FAQ item 2 question |
|---|---|---|---|
| WCAG SC with published techniques | Include | "must" | "How does this issue relate to SC [name and number]?" |
| WCAG SC without published techniques | Omit | "must" | "How does this issue relate to SC [name and number]?" |
| Best practice | Omit | "should" | "Why is this rule considered a best practice?" |

---

## Try It Yourself — common testing methods

Include an H3 subsection for each method that applies to the validation.

| Method (H3 heading — sentence case) | When to include |
|---|---|
| Using a screen reader | When the issue affects how assistive technology reads content |
| Using a keyboard | When the issue affects keyboard navigation or operation |
| Inspecting the browser's accessibility tree | When the issue involves ARIA roles, states, or properties |
| Testing color contrast | When the issue involves contrast ratios |

Each subsection must follow this structure. **Steps to follow:** appears immediately above the numbered steps with no blank line between the label and the first step.

```markdown
**Steps to follow:**
1. {{step}}

**Expected results:** {{expected_result}}

**Actual results:** {{actual_result}}
```
