# A11y Content Annotations Review

Review **content** accessibility annotations — accessible names, labels, and alt text — for style compliance, completeness, correctness, and consistency.

> **Scope boundary.** This skill covers content annotations only: `aria-label`, `aria-labelledby`, `aria-describedby`, and `alt` values. ARIA roles, states (e.g. `aria-selected`, `aria-expanded`), focus management, and keyboard interaction patterns are the a11y engineer's responsibility and are out of scope here.

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

Use this skill when reviewing accessibility content annotations. This covers:

| Input type | Examples |
|------------|----------|
| Accessible name annotations | `aria-label` values on icon buttons, links, form fields, regions |
| Labelling relationship annotations | `aria-labelledby` and `id` pairings on dialogs, sections, and form fields |
| Description annotations | `aria-describedby` values that add supplementary context |
| Image alt text | Decorative (`alt=""`) and informative (`alt="…"`) values |

**Out of scope for this skill** (handled by the a11y engineer):
- ARIA roles
- ARIA states — `aria-selected`, `aria-expanded`, `aria-checked`, `aria-pressed`, etc.
- Focus management and keyboard interaction patterns
- Reading order and focus order
- `aria-controls`, `aria-owns`, `aria-haspopup`, live regions

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

**Tooling note.** Content annotations should be attached using Figma's native annotations tool — not custom frames, sticky notes, or overlay layers.

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

| Element type | Common missing content annotations |
|---|---|
| Icon-only buttons | `aria-label` — no visible label, name must be explicit |
| Links that open in a new tab or window | `aria-label` — visible text alone does not convey the new-window behaviour |
| Dialogs / modals | `aria-labelledby` referencing the dialog heading; `id` on that heading |
| Landmark regions without a visible heading | `aria-label` to identify the region's purpose |
| Tab lists | `aria-label` describing the purpose of the tab group |
| Form fields without a visible label | `aria-label` or `aria-labelledby` |
| Informative images | `alt` with a meaningful description |
| Decorative images | `alt=""` confirming they are intentionally hidden |

Do not flag missing roles, states, or focus management — those are the a11y engineer's responsibility.

Cite the WCAG 2.2 AA success criterion for each gap.

---

### 3. Correctness

Check that accessible name and label annotations are correct.

What to flag:
- `aria-label` value that duplicates the visible label text exactly — redundant and creates a mismatch risk if visible text changes
- `aria-labelledby` that references a non-existent or mismatched `id`
- `aria-label` on an element whose accessible name is already provided clearly by visible text
- `alt` text that describes appearance rather than meaning
- `alt=""` on an image that conveys information

Use `reference/annotation-conventions.md` as a reference. Do not flag roles or states — those are out of scope.

---

### 4. Consistency

Scan across all annotations for the same pattern described differently.

What to flag:
- Same accessible name written in different formats across instances of the same component
- Same relationship (`aria-labelledby`, `aria-describedby`) expressed with different syntax in different places
- Same element type with an accessible name annotation present in one place and absent in another without a clear reason

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
| 1.3.6 | Identify Purpose | Landmark and input purpose labels |
| 2.5.3 | Label in Name | Accessible name must contain visible label text |
| 3.3.2 | Labels or Instructions | Form field label annotations |
| 4.1.2 | Name, Role, Value | Accessible name on interactive elements |
