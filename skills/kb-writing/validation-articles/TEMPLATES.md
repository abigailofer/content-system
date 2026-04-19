# Templates: Validation Articles

---

## Article structure

Use the following template for every validation article. Sections marked **[conditional]** are included or omitted based on the entry type. Refer to [SKILL.md](SKILL.md) for the rules governing each condition.

---

## Full article template

```markdown
## {{validation_name}}

**{{violation_rule}}**

{{description_paragraph_1}}

{{description_paragraph_2_if_needed}}

### Pass Patterns

<!-- Description line: one short sentence describing what the example shows. Must contain a verb, use present tense, describe the example — not explain why it passes. Example: "A list contains the required `listitem` children." -->
{{pass_pattern_1_description}}

<!-- Explanation sentence: one sentence providing more context about the example. -->
{{pass_pattern_1_explanation}}

```html
{{pass_pattern_1_code}}
```

{{pass_pattern_2_description_if_applicable}}

{{pass_pattern_2_explanation_if_applicable}}

```html
{{pass_pattern_2_code_if_applicable}}
```

### Fail Patterns

<!-- Description line: one short sentence describing what the example shows. Must contain a verb, use present tense, describe the example — not explain why it fails. Example: "A list is missing its required children." -->
{{fail_pattern_1_description}}

<!-- Explanation sentence: one sentence providing more context about the example. -->
{{fail_pattern_1_explanation}}

```html
{{fail_pattern_1_code}}
```

{{fail_pattern_2_description_if_applicable}}

{{fail_pattern_2_explanation_if_applicable}}

```html
{{fail_pattern_2_code_if_applicable}}
```

<!-- Related WCAG Techniques — include only when wcag_sc != "best practice" AND published techniques exist -->
### Related WCAG Techniques

#### Sufficient techniques

[{{technique_name}}]({{technique_url}})

#### Advisory techniques

<!-- Include if advisory techniques exist. If omitted on a non-best-practice entry, flag for review. -->
[{{technique_name}}]({{technique_url}})

#### Failure techniques

[{{technique_name}}]({{technique_url}})
<!-- End Related WCAG Techniques -->

### Try It Yourself

#### {{testing_method_1}}

**Steps to follow:**

1. {{step_1}}
2. {{step_2}}
3. {{step_3}}

**Expected results**

{{expected_result}}

**Actual results**

{{actual_result}}

#### {{testing_method_2_if_applicable}}

**Steps to follow:**

1. {{step_1}}
2. {{step_2}}

**Expected results**

{{expected_result}}

**Actual results**

{{actual_result}}

### FAQ

**Why is this issue marked as {{severity}}?**

{{severity_explanation}}

<!-- WCAG entry — use this phrasing when wcag_sc != "best practice" -->
**How does this issue relate to SC {{wcag_sc}}?**

{{wcag_sc_explanation}}

<!-- Best-practice entry — use this phrasing when wcag_sc == "best practice" -->
**Why is this rule considered a best practice?**

{{best_practice_explanation}}
<!-- End conditional FAQ item 2 -->

<!-- Recommended Reading — optional. Include only if relevant external references exist. -->
### Recommended Reading

- [{{reference_title}}]({{reference_url}})
<!-- End Recommended Reading -->
```

---

## Variable reference

| Variable | Description | Format |
|---|---|---|
| `{{validation_name}}` | The slug for this validation | Lowercase, hyphenated — for example, `placeholder-as-label` |
| `{{violation_rule}}` | The one-line rule statement | Bold, 1 sentence, ends with a period; "must" for WCAG SC, "should" for best practice |
| `{{description_paragraph}}` | Explanation of the validation | ~50 words, no SC name or number, plain language |
| `{{wcag_sc}}` | SC name and number, or `"best practice"` | For example, `1.3.1 Info and Relationships` |
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

Include an H3 subsection for each method that applies to the validation. Common methods are listed below.

| Method (H3 heading — sentence case) | When to include |
|---|---|
| Using a screen reader | When the issue affects how assistive technology reads content |
| Using a keyboard | When the issue affects keyboard navigation or operation |
| Inspecting the browser's accessibility tree | When the issue involves ARIA roles, states, or properties |
| Testing color contrast | When the issue involves contrast ratios |

Each subsection must follow this structure. **Steps to follow:** appears immediately above the numbered steps, with no blank line between the label and the first step.

```markdown
**Steps to follow:**
1. {{step}}

**Expected results**

{{expected_result}}

**Actual results**

{{actual_result}}
```
