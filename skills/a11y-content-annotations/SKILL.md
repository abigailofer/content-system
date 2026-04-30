# A11y Content Annotations Review

Review accessibility annotations for style compliance, WCAG 2.2 AA completeness, ARIA correctness, and cross-annotation consistency.

---

## Table of contents
- [When to apply](#when-to-apply)
- [Inputs required](#inputs-required)
- [Review workflow](#review-workflow)
- [Review dimensions](#review-dimensions)
- [Output format](#output-format)
- [Behavior rules](#behavior-rules)
- [WCAG alignment](#wcag-alignment)

---

## When to apply

Use this skill when reviewing accessibility annotations that describe how content and UI elements should be presented to assistive technology. This includes:

| Input type | Examples |
|------------|----------|
| ARIA annotations | Role, state, property, and relationship annotations on interactive elements |
| Landmark annotations | Page structure, region labels, navigation labels |
| Content annotations | Alt text, heading levels, reading order, focus management |
| State annotations | Expanded/collapsed, selected, checked, disabled, invalid states |
| Relationship annotations | aria-labelledby, aria-describedby, aria-controls references |

This skill does not write annotations. It reviews existing ones. For writing accessible UI copy, use `writing-accessible-ui-copy`.

---

## Inputs required

| Input | Purpose | Required? |
|-------|---------|-----------|
| Accessibility annotations | The content to review (pasted text or file) | Yes |
| Team style guide | Language and terminology rules for annotation writing | Recommended |
| Component or screen context | What UI is being annotated | Recommended |
| WCAG conformance target | Level to check against (default: AA) | Optional |

If no style guide is provided, skip style checks and note the omission in the report.

---

## Review workflow

### Step 1 — Gather inputs

Ask for any missing required inputs. If the style guide is absent, confirm whether to proceed without style checks.

### Step 2 — Read reference material

Before reviewing, read:
- `reference/wcag-aria-checklist.md` for completeness and correctness checks
- `reference/annotation-conventions.md` for notation conventions

### Step 3 — Review each dimension

Work through the annotations systematically. For each annotated element, check all four dimensions. Do not skip elements, even if they appear correct.

### Step 4 — Compile report

Use the output format defined below. Always include all four sections, even if a section has zero issues.

---

## Review dimensions

### 1. Style

Compare annotation language and terminology against the provided style guide.

What to flag:
- Wrong terminology or disallowed word choices
- Formatting that violates the style guide (casing, punctuation, structure)
- Missing annotation fields the style guide requires
- Abbreviations or shorthand the style guide does not permit

Do not flag anything the style guide does not address. Do not invent style rules.

---

### 2. Completeness

Check that every annotated element has all required annotations for its type. Use `reference/wcag-aria-checklist.md` as the source of truth.

Common gaps to watch for:

| Element type | Common missing annotations |
|---|---|
| Interactive elements | Accessible name, role (if custom), state |
| Images | Alt text type (informative/decorative), alt value |
| Form inputs | Label association, required indicator, error annotation |
| Dialogs/modals | Role, aria-labelledby, focus management |
| Landmark regions | Role, label (when multiple of same type) |
| Stateful widgets | All relevant states (expanded, selected, checked, etc.) |
| Live regions | Politeness level, aria-atomic if needed |
| Tables | Caption or label, header cell roles |

Cite the WCAG 2.2 AA success criterion for each gap.

---

### 3. Correctness

Check that ARIA roles, states, properties, and values are used correctly.

What to flag:
- Role applied to the wrong element type
- Invalid attribute for the given role
- Incorrect value type for a property
- Redundant ARIA that duplicates native semantics
- Conflicting annotations (e.g., aria-hidden on a focusable element)

Use `reference/wcag-aria-checklist.md` (error table) and `reference/annotation-conventions.md` as references.

---

### 4. Consistency

Scan across all annotations for the same pattern described differently.

What to flag:
- Same role annotated with different terminology in different places
- Same state written in different formats (e.g., `aria-expanded: true` vs `expanded: true` vs `[expanded]`)
- Same relationship expressed with different syntax
- Same element type with annotation present in one place and absent in another without a clear reason

Do not flag legitimate differences (e.g., different accessible names for different instances of the same component).

---

## Output format

Always use this exact structure. Do not omit sections with zero issues — write "None found" instead.

---

## A11y Annotation Review

**Scope:** [component or screen name, or "not specified"]
**Style guide:** [provided / not provided — style checks skipped]
**Standard:** WCAG 2.2 AA

---

### Style issues  [N]

*(Omit entirely only if style guide was not provided.)*

- **[Element / annotation ref]** — [Deviation from style guide] → **Suggested fix:** [corrected annotation text]

---

### Completeness gaps  [N]

- **Missing:** [annotation] on [element] — required by WCAG 2.2 SC [number] ([SC name])

*None found.*

---

### Correctness errors  [N]

- **[Element]** — [what is wrong] → **Should be:** [correct annotation] *(ARIA: [brief note])*

*None found.*

---

### Consistency issues  [N]

- **[Pattern]** is written as "[form A]" in [location] and "[form B]" in [location] → **Use:** [recommended form]

*None found.*

---

### Summary

**[Total] issue(s) found** — [N style] · [N completeness] · [N correctness] · [N consistency]

---

## Behavior rules

- Give a concrete suggested fix for every issue. Never flag without a fix.
- Quote the relevant annotation text when referencing a specific issue.
- If the annotations cover only part of a screen, note the scope limitation above the report.
- When the style guide and WCAG requirements conflict, flag both and note the conflict.
- Do not penalize correct ARIA usage simply because it differs from conventions in the reference files — those are defaults, not absolutes.
- Keep the tone direct and constructive. Developers will act on this feedback.

---

## WCAG alignment

| SC | Name | Relevant to |
|---|---|---|
| 1.1.1 | Non-text Content | Alt text annotations |
| 1.3.1 | Info and Relationships | Heading, table, list annotations |
| 1.3.2 | Meaningful Sequence | Reading order annotations |
| 1.3.6 | Identify Purpose | Landmark and input purpose annotations |
| 2.1.1 | Keyboard | Tab stop and keyboard interaction annotations |
| 2.4.3 | Focus Order | Focus management annotations |
| 2.5.3 | Label in Name | Accessible name must contain visible label text |
| 3.3.1 | Error Identification | Error message and aria-invalid annotations |
| 3.3.2 | Labels or Instructions | aria-required, form instruction annotations |
| 4.1.2 | Name, Role, Value | All interactive widget annotations |
| 4.1.3 | Status Messages | Live region annotations |
