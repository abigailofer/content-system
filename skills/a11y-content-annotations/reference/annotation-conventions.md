# Accessibility Annotation Conventions

Conventions for writing a11y **content** annotations. These apply when no team style guide overrides them.

---

## Division of responsibilities

| Responsibility | Owner |
|---|---|
| Accessible names — `aria-label`, `aria-labelledby` values | Content annotator (this skill) |
| Descriptions — `aria-describedby` values | Content annotator (this skill) |
| Image alt text | Content annotator (this skill) |
| Landmark and region labels | Content annotator (this skill) |
| ARIA roles | A11y engineer |
| ARIA states — `aria-selected`, `aria-expanded`, `aria-checked`, `aria-pressed`, etc. | A11y engineer |
| Focus management and keyboard interaction | A11y engineer |
| Reading order and focus order | A11y engineer |
| `aria-controls`, `aria-owns`, `aria-haspopup`, live regions | A11y engineer |

---

## Tooling

Use **Figma's native annotations tool** to attach annotations to nodes. Do not create custom annotation frames, sticky notes, or overlay layers.

---

## Accessible name notation

- Write the exact ARIA attribute and value: `aria-label="<text>"` or `aria-labelledby="<id>"`
- When using `aria-labelledby`, also annotate the referenced element with its `id`: `id="<id>"`
- Wrap the value in double quotes to make the exact string unambiguous
- When a visible label already provides a clear, unambiguous accessible name, no annotation is needed

---

## Landmark and region labels

- Annotate landmark regions that lack a visible heading: `aria-label="<region purpose>"`
- For tab lists: `aria-label="<purpose of the tab group>"`
- Do not annotate the landmark role — that is the a11y engineer's responsibility

---

## Images and icons

- Decorative images: `alt=""` — confirms the image is intentionally hidden from assistive technology
- Informative images: `alt="<description>"` — describe meaning, not appearance
- Functional icon buttons have no visible label; an `aria-label` annotation is always required

---

## What to annotate

| Element | Annotation needed |
|---|---|
| Icon-only buttons | `aria-label="<action>"` |
| Links that open in a new tab/window | `aria-label="<link text> (opens in new window)"` |
| Dialogs / modals | `aria-labelledby="<heading-id>"` + `id="<heading-id>"` on the heading |
| Landmark regions without a visible heading | `aria-label="<region name>"` |
| Tab lists | `aria-label="<purpose of tabs>"` |
| Form fields without a visible label | `aria-label="<field name>"` |
| Informative images | `alt="<meaningful description>"` |
| Decorative images | `alt=""` |

---

## What to avoid

- Do not annotate ARIA roles — that is the a11y engineer's responsibility
- Do not annotate ARIA states (`aria-selected`, `aria-expanded`, `aria-checked`, etc.) — that is the a11y engineer's responsibility
- Do not duplicate a visible label as an `aria-label` value — redundant and prone to mismatch if visible text changes
- Do not annotate default browser behaviour that requires no override
- Do not use "TBD" or "see dev" as an annotation value — provide the text or flag it as an open content decision
