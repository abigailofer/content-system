# Accessibility Annotation Conventions

Industry-standard conventions for writing a11y annotations. These apply when no team style guide overrides them.

---

## Role notation

- Write roles in lowercase matching the ARIA spec: `button`, `checkbox`, `dialog`, `listbox`, `combobox`, `tabpanel`
- Use the format `role: <role-name>` or a clear label such as "ARIA role: combobox"
- Do not write role names in ALL CAPS
- For landmark roles, use the semantic term: `banner`, `main`, `navigation`, `complementary`, `contentinfo`, `form`, `search`, `region`

---

## Accessible name notation

- Use `label: "<text>"` or `accessible name: "<text>"` for static names
- When referencing another element: `aria-labelledby: <element-id>` or "labelled by: [element description]"
- When the name comes from a native HTML label: "labelled by visible text" — no need to repeat the value
- Wrap the accessible name value in quotes to make the exact string clear

---

## State notation

Write states using their ARIA attribute names and values:

```
aria-expanded: true | false
aria-checked: true | false | mixed
aria-pressed: true | false | mixed
aria-selected: true | false
aria-disabled: true  (omit when false)
aria-invalid: true | grammar | spelling  (omit when false)
```

Always annotate the initial state and note which event changes it.

**Example:**
```
aria-expanded: false → becomes true when trigger is activated
```

---

## Property notation

- Write properties in lowercase hyphenated form: `aria-describedby`, `aria-controls`, `aria-owns`, `aria-haspopup`
- Reference target elements by annotation ID or description: `aria-controls: [dropdown list]`
- For `aria-haspopup`, specify the popup type: `aria-haspopup: listbox`, `aria-haspopup: dialog`

---

## Reading order

- Use numbered callouts or a sequential list: "Reading order: 1 → 2 → 3"
- Explicitly note divergence from visual order: "Reading order differs from visual layout — [element A] announced before [element B]"
- For focus order, note the first tab stop and progression through interactive elements

---

## Focus management

- Dialogs: "On open: focus moves to [element]" / "On close: focus returns to [trigger]"
- Modal dialogs: "Focus contained within dialog while open"
- Complex widgets: annotate arrow-key navigation separately from Tab navigation

---

## Relationship notation

| Property | Annotation format |
|---|---|
| `aria-controls` | "[Source] controls [target]" |
| `aria-owns` | "[Parent] owns [child elements]" — use sparingly |
| `aria-describedby` | "[Element] described by [description element]" |
| `aria-flowto` | Note explicitly — rarely used |

---

## Live regions

- State politeness level explicitly: `aria-live: polite` or `aria-live: assertive`
- Note `aria-atomic: true` when full region content is announced as a unit
- Shorthand roles: `role: status` (polite, atomic), `role: alert` (assertive, atomic), `role: log` (polite, non-atomic)

---

## Landmark annotations

- Annotate each landmark region and its label
- For labeled landmarks: `navigation: "Primary"` or `aria-label: "Site navigation"`
- List all landmarks in page order to make structural completeness easy to verify

---

## Images and icons

- Decorative: `alt: ""` or "decorative — hidden from assistive technology"
- Informative: `alt: "<description>"` — convey meaning, not appearance
- Functional icon button: accessible name annotation required; do not rely on tooltip text

---

## What to avoid

- Do not annotate implementation details (CSS class names, DOM IDs) unless part of an ARIA relationship
- Do not annotate default browser behavior that requires no override
- Do not use "TBD" or "see dev" as an annotation value — fill it in or flag it as incomplete
- Do not duplicate the visible label as an `aria-label` value — redundant and prone to mismatch
