# WCAG 2.2 AA Annotation Checklist

Required annotations by element type, plus a common error reference.

---

## Interactive elements

Applies to: buttons, links, inputs, selects, checkboxes, radios, sliders, toggles, custom widgets.

| Required annotation | When required | SC |
|---|---|---|
| Accessible name | Always — every interactive element | 4.1.2 |
| Role | When native HTML element is ambiguous or custom | 4.1.2 |
| `aria-pressed` | Toggle buttons | 4.1.2 |
| `aria-checked` | Checkboxes, radios, switches | 4.1.2 |
| `aria-expanded` | Disclosures, accordions, comboboxes, menus | 4.1.2 |
| `aria-selected` | Listbox options, tabs, grid cells | 4.1.2 |
| `aria-disabled` | When element is disabled | 4.1.2 |
| `aria-required` | Required form inputs | 3.3.2 |
| `aria-invalid` + error ref | When a validation error is active | 3.3.1 |
| `aria-describedby` → error text | Form inputs with error messages | 3.3.1 |
| `aria-valuemin`, `aria-valuemax`, `aria-valuenow` | Sliders, spinbuttons | 4.1.2 |
| `aria-valuetext` | When numeric value is not meaningful (e.g., sliders) | 4.1.2 |

---

## Landmark regions

| Required annotation | When required | SC |
|---|---|---|
| `banner` (header) | Every page | 1.3.6 |
| `main` | Every page — only one allowed | 1.3.6 |
| `contentinfo` (footer) | Every page | 1.3.6 |
| `navigation` label | When multiple nav regions exist | 1.3.6 |
| `complementary` label | When multiple aside regions exist | 1.3.6 |
| `form` or `search` label | When multiple form/search regions exist | 1.3.6 |

---

## Headings

| Required annotation | When required | SC |
|---|---|---|
| Heading level (h1–h6) | All section headings | 1.3.1 |
| Sequential hierarchy | No skipped levels (e.g., h1 → h3) | 1.3.1 |

---

## Images and icons

| Required annotation | When required | SC |
|---|---|---|
| `alt=""` or `role="presentation"` | Decorative images | 1.1.1 |
| Descriptive `alt` value | Informative images | 1.1.1 |
| Accessible name | Functional icons with no visible text | 1.1.1, 4.1.2 |

---

## Live regions

| Required annotation | When required | SC |
|---|---|---|
| `aria-live` politeness level | Any content that updates without user action | 4.1.3 |
| `role="status"`, `role="alert"`, `role="log"` | Status messages and alerts | 4.1.3 |
| `aria-atomic` | When the whole region should be announced as a unit | 4.1.3 |

---

## Dialogs and modals

| Required annotation | When required | SC |
|---|---|---|
| `role="dialog"` or `role="alertdialog"` | All dialogs | 4.1.2 |
| `aria-labelledby` → dialog title | Always | 4.1.2 |
| `aria-describedby` → description | When a description paragraph exists | 4.1.2 |
| Focus on open | Where focus moves when dialog opens | 2.4.3 |
| Focus on close | Where focus returns when dialog closes | 2.4.3 |

---

## Tables

| Required annotation | When required | SC |
|---|---|---|
| `role="table"` or `role="grid"` | Data/interactive tables | 1.3.1 |
| Caption or `aria-label` | All tables | 1.3.1 |
| `columnheader` / `rowheader` | Header cells | 1.3.1 |

---

## Tabs

| Required annotation | When required | SC |
|---|---|---|
| `role="tablist"`, `role="tab"`, `role="tabpanel"` | All tab patterns | 4.1.2 |
| `aria-selected` on active tab | Always | 4.1.2 |
| `aria-controls` (tab → panel) or `aria-labelledby` (panel → tab) | Always | 4.1.2 |

---

## Comboboxes / autocompletes

| Required annotation | When required | SC |
|---|---|---|
| `role="combobox"` | Combobox input | 4.1.2 |
| `aria-expanded` | Always | 4.1.2 |
| `aria-autocomplete` | Always | 4.1.2 |
| `aria-controls` → listbox | Always | 4.1.2 |
| `role="listbox"` on popup | Always | 4.1.2 |
| `aria-activedescendant` | When focus stays on input while list is navigated | 4.1.2 |

---

## Reading order and focus

| Required annotation | When required | SC |
|---|---|---|
| Reading order note | When visual order diverges from DOM order | 1.3.2 |
| Tab stop annotations | Complex widgets with custom keyboard interaction | 2.1.1 |
| Focus management | Dialogs, route changes, dynamic content insertions | 2.4.3 |

---

## Common annotation errors

| Error | Correct |
|---|---|
| `role="button"` on a native `<button>` | Remove — native element implies the role |
| `aria-label` duplicates visible text exactly | Use `aria-labelledby` or remove `aria-label` |
| `aria-disabled="false"` stated explicitly | Omit — absence implies enabled |
| `aria-hidden="false"` stated explicitly | Omit — absence implies visible |
| `role="presentation"` on a focusable element | Remove role or remove focusability |
| `aria-required` on `role="button"` | `aria-required` is not valid on button role |
| `aria-checked` on a toggle button | Use `aria-pressed` for toggle buttons |
| `role="dialog"` with no `aria-labelledby` | Add label pointing to dialog title |
| `aria-live="assertive"` on non-urgent content | Use `aria-live="polite"` |
| Multiple `main` landmarks on one page | Only one `main` allowed per page |
| Multiple `navigation` landmarks with no labels | Add `aria-label` to distinguish each |
| `aria-haspopup` without specifying popup type | Include popup type: `aria-haspopup="listbox"` |
