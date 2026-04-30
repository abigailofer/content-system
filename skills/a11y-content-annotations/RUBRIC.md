# Rubric: A11y Content Annotations Review

Evaluation criteria for annotation reviews across four dimensions.

---

## Table of contents
- [Scoring guide](#scoring-guide)
- [Dimension 1: Style compliance](#dimension-1-style-compliance)
- [Dimension 2: Completeness](#dimension-2-completeness)
- [Dimension 3: Correctness](#dimension-3-correctness)
- [Dimension 4: Consistency](#dimension-4-consistency)
- [Scoring thresholds](#scoring-thresholds)
- [Quick-fail criteria](#quick-fail-criteria)
- [Scoring worksheet](#scoring-worksheet)

---

## Scoring guide

| Score | Level | Description |
|-------|-------|-------------|
| 4 | Expert | Exceeds requirements; exemplary annotation practice |
| 3 | Proficient | Meets requirements; minor gaps only |
| 2 | Developing | Partial compliance; meaningful gaps remain |
| 1 | Novice | Significant issues; annotations unreliable for implementation |

---

## Dimension 1: Style compliance
*Applies only when a team style guide has been provided.*

### Level 4 — Expert
- All annotation language matches the style guide precisely
- Terminology is consistent with the style guide throughout
- Formatting (casing, punctuation, structure) follows the style guide exactly
- All required annotation fields specified by the style guide are present
- No disallowed abbreviations, shorthand, or placeholders

### Level 3 — Proficient
- Terminology matches the style guide with rare exceptions
- Minor formatting deviations (e.g., casing inconsistency) that do not obscure meaning
- Required fields present; minor omissions are non-critical

### Level 2 — Developing
- Multiple terminology deviations from the style guide
- Formatting inconsistencies across annotations
- Some required style guide fields missing

### Level 1 — Novice
- Consistent use of terminology not aligned with the style guide
- Formatting does not follow the style guide
- Required fields routinely absent
- Placeholders ("TBD", "see dev") used as annotation values

---

## Dimension 2: Completeness
*WCAG 2.2 AA. Reference: `reference/wcag-aria-checklist.md`.*

### Level 4 — Expert
- All annotatable elements have complete annotation sets for their type
- No WCAG 2.2 AA required annotations missing
- Focus management annotated for all dialogs and dynamic interactions
- Reading order annotated wherever visual and DOM order diverge
- State annotations cover all relevant states, including initial state
- All landmark regions present and labeled where required

### Level 3 — Proficient
- Most elements fully annotated; isolated gaps on non-critical elements
- Core WCAG 2.2 AA annotations present (name, role, state)
- Focus management annotated on dialogs
- Minor omissions that would not cause implementation errors

### Level 2 — Developing
- Repeated annotation gaps on one or more element types
- Some WCAG 2.2 AA required annotations missing (e.g., error associations, landmark labels)
- Focus management partially annotated
- State annotations incomplete

### Level 1 — Novice
- Widespread missing annotations across element types
- Core required annotations (accessible name, role) routinely absent
- No focus management annotations
- Landmark structure not annotated

---

## Dimension 3: Correctness
*ARIA 1.2 spec and WCAG 2.2 AA. Reference: `reference/wcag-aria-checklist.md` error table.*

### Level 4 — Expert
- All ARIA roles, states, and properties are used correctly
- No invalid attribute-role combinations
- No redundant ARIA that duplicates native semantics
- No conflicting annotations (e.g., `aria-hidden` on focusable elements)
- `aria-haspopup` includes popup type
- `aria-live` politeness level is appropriate to urgency

### Level 3 — Proficient
- ARIA usage is correct with rare exceptions
- No critical errors (role on wrong element, conflicting annotations)
- Minor issues that are unlikely to cause screen reader errors

### Level 2 — Developing
- Some invalid attribute-role combinations
- Redundant ARIA present (e.g., `role="button"` on native `<button>`)
- `aria-live="assertive"` used for non-urgent content
- `aria-haspopup` missing popup type specification

### Level 1 — Novice
- Multiple incorrect role assignments
- Widespread invalid attribute-role combinations
- Conflicting annotations present
- No distinction between `aria-pressed` and `aria-checked` usage

---

## Dimension 4: Consistency
*Applies across the full set of annotations provided.*

### Level 4 — Expert
- All instances of the same pattern use identical terminology and format
- Same element types annotated to the same depth throughout
- State format is uniform (e.g., `aria-expanded: true` not mixed with `expanded: true`)
- Relationship notation is consistent across all annotations

### Level 3 — Proficient
- Minor inconsistencies in notation format that do not cause ambiguity
- Same element types consistently annotated; depth varies only where context differs
- No terminology inconsistencies that would confuse implementation

### Level 2 — Developing
- Repeated notation format inconsistencies for the same pattern
- Same element type annotated in some places and not others without a clear reason
- Terminology inconsistencies across annotations

### Level 1 — Novice
- Widespread inconsistency; annotations cannot be used as a reliable spec
- Same pattern annotated differently in every instance
- Mix of formats, terminology, and detail levels with no apparent pattern

---

## Scoring thresholds

| Total score | Rating | Recommendation |
|-------------|--------|----------------|
| 14–16 | Exemplary | Ready for implementation |
| 10–13 | Passing | Minor revisions before handoff |
| 6–9 | Needs work | Revise before implementation |
| 4–5 | Failing | Major revision required |

*Style compliance is excluded from the total when no style guide was provided. In that case, scoring is out of 12.*

---

## Quick-fail criteria

Any of these result in automatic failure regardless of other scores:

| Criterion | Standard |
|-----------|----------|
| Interactive element with no accessible name annotation | WCAG 4.1.2 |
| `role="dialog"` with no `aria-labelledby` | WCAG 4.1.2 |
| `aria-hidden` annotated on a focusable element | ARIA 1.2 |
| `role="presentation"` annotated on a focusable element | ARIA 1.2 |
| `aria-required` annotated on a non-form role | ARIA 1.2 |
| Multiple `main` landmarks annotated | WCAG 1.3.6 |
| Placeholder values ("TBD", "see dev") as annotation content | — |
| Conflicting annotations on the same element | ARIA 1.2 |

---

## Scoring worksheet

```yaml
evaluation:
  component: "[Name]"
  evaluator: "[Name]"
  date: "[Date]"
  style_guide_provided: "[yes|no]"

  scores:
    style_compliance:    [1-4 | n/a]
    completeness:        [1-4]
    correctness:         [1-4]
    consistency:         [1-4]

  total: "[Sum / 16 or 12 if no style guide]"
  quick_fail: "[yes|no]"
  quick_fail_reason: "[If applicable]"

  recommendation: "[Ready|Revise|Major revision|Fail]"
  priority_fixes: |
    1. [Most critical issue]
    2. [Second priority]
    3. [Third priority]
```
