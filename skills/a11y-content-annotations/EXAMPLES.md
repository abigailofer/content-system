# Examples: A11y Content Annotations Review

Annotated examples showing correct, incorrect, and corrected annotation patterns.

---

## Table of contents
- [Interactive elements](#interactive-elements)
- [Images and icons](#images-and-icons)
- [Form inputs](#form-inputs)
- [Dialogs and modals](#dialogs-and-modals)
- [Landmark regions](#landmark-regions)
- [Stateful widgets](#stateful-widgets)
- [Live regions](#live-regions)
- [Review report sample](#review-report-sample)

---

## Interactive elements

### Toggle button — correct
```yaml
element: "Mute button"
role: button
accessible_name: "Mute"
aria-pressed: false
# aria-pressed becomes true when activated
```

### Toggle button — incorrect
```yaml
element: "Mute button"
role: button
label: "Mute"
aria-checked: false   # ❌ aria-checked is for checkboxes, not toggle buttons
```
**Correction:** Replace `aria-checked` with `aria-pressed`.

---

### Link — correct
```yaml
element: "Documentation link"
role: link
accessible_name: "Read the API documentation"
# Meaningful out of context — WCAG 2.4.9
```

### Link — incorrect
```yaml
element: "Documentation link"
role: link
accessible_name: "Click here"  # ❌ Generic — not meaningful out of context
```
**Correction:** Use a descriptive accessible name that identifies the destination.

---

### Icon button — correct
```yaml
element: "Delete row button"
role: button
accessible_name: "Delete row"   # Explicit label since icon has no visible text
aria-label: "Delete row"
```

### Icon button — incorrect
```yaml
element: "Delete row button"
role: button
# No accessible name annotation     ❌ Fails WCAG 4.1.2
```
**Correction:** Add an accessible name annotation.

---

## Images and icons

### Informative image — correct
```yaml
element: "Chart: Monthly active users"
type: informative
alt: "Line chart showing monthly active users rising from 1.2M in January to 3.8M in June."
# Describes meaning, not appearance — WCAG 1.1.1
```

### Informative image — incorrect
```yaml
element: "Chart: Monthly active users"
type: informative
alt: "image of chart"   # ❌ Describes format, not content
```
**Correction:** Write alt text that conveys the meaning or key insight of the image.

---

### Decorative image — correct
```yaml
element: "Background illustration"
type: decorative
alt: ""
aria_hidden: true
```

### Decorative image — incorrect
```yaml
element: "Background illustration"
type: decorative
alt: "decorative swirl pattern"   # ❌ Decorative images should have empty alt
```
**Correction:** Set `alt: ""` and `aria-hidden: true`.

---

## Form inputs

### Text field — correct
```yaml
element: "Email field"
role: textbox
label: "Email address"
aria_required: true
aria_describedby: "email-help"   # Points to: "We'll send confirmation here."
error_state:
  aria_invalid: true
  aria_describedby: "email-error"   # Points to error message
  error_text: "Enter a valid email address (e.g., name@company.com)"
```

### Text field — incorrect
```yaml
element: "Email field"
role: textbox
placeholder: "Enter email"   # ❌ Placeholder is not a label
# No aria-required annotation
# No error state annotation
```
**Correction:** Add a visible label annotation, `aria-required`, and error state annotations.

---

## Dialogs and modals

### Confirmation dialog — correct
```yaml
element: "Delete account dialog"
role: dialog
aria_labelledby: "dialog-title"   # Points to: "Delete Account?"
aria_describedby: "dialog-body"   # Points to: "This permanently removes..."
focus:
  on_open: "Cancel button (first focusable element)"
  on_close: "Delete Account trigger button"
focus_trap: true   # Focus contained within dialog while open
```

### Confirmation dialog — incorrect
```yaml
element: "Delete account dialog"
role: dialog
# No aria-labelledby                       ❌ WCAG 4.1.2
# No focus management annotations          ❌ WCAG 2.4.3
```
**Correction:** Add `aria-labelledby` pointing to the dialog title, and annotate focus on open and close.

---

## Landmark regions

### Page landmark structure — correct
```yaml
landmarks:
  - role: banner          # Header
  - role: navigation
    aria_label: "Primary"
  - role: navigation
    aria_label: "Breadcrumb"
  - role: main
  - role: complementary
    aria_label: "Related articles"
  - role: contentinfo     # Footer
```

### Page landmark structure — incorrect
```yaml
landmarks:
  - role: navigation      # ❌ No label, but there are two nav regions
  - role: navigation      # ❌ Indistinguishable from first
  - role: main
  # Missing banner and contentinfo          ❌ WCAG 1.3.6
```
**Correction:** Label each navigation region distinctly; add `banner` and `contentinfo`.

---

## Stateful widgets

### Accordion — correct
```yaml
element: "Billing details accordion"
role: button   # The trigger
aria_expanded: false   # Initial state — becomes true when expanded
aria_controls: "billing-panel"   # Points to the panel
```

### Accordion — incorrect
```yaml
element: "Billing details accordion"
role: button
expanded: false   # ❌ Not a valid ARIA attribute name
```
**Correction:** Use `aria-expanded`, not `expanded`.

---

### Tabs — correct
```yaml
tablist:
  role: tablist
  aria_label: "Account sections"
  tabs:
    - role: tab
      accessible_name: "Profile"
      aria_selected: true
      aria_controls: "profile-panel"
    - role: tab
      accessible_name: "Security"
      aria_selected: false
      aria_controls: "security-panel"
```

### Tabs — incorrect
```yaml
tablist:
  role: tablist
  tabs:
    - role: tab
      label: "Profile"
      # No aria-selected annotation         ❌ WCAG 4.1.2
      # No aria-controls annotation         ❌ WCAG 4.1.2
```
**Correction:** Add `aria-selected` to each tab and `aria-controls` pointing to its panel.

---

## Live regions

### Success toast — correct
```yaml
element: "Save confirmation toast"
role: status   # Polite, atomic
text: "Changes saved."
# aria-live: polite (implicit in role="status")
```

### Error alert — correct
```yaml
element: "Payment failure alert"
role: alert   # Assertive, atomic
text: "Payment didn't go through. Try another card."
```

### Live region — incorrect
```yaml
element: "Save confirmation toast"
aria_live: assertive   # ❌ Assertive interrupts immediately — use polite for success messages
text: "Changes saved."
```
**Correction:** Use `aria-live="polite"` or `role="status"` for non-urgent updates.

---

## Review report sample

A sample output for a set of annotations on a search combobox:

---

## A11y Annotation Review

**Scope:** Search combobox — global header
**Style guide:** Provided
**Standard:** WCAG 2.2 AA

---

### Style issues  2

- **Search input label** — Style guide requires "Accessible name:" prefix; annotation uses "label:" → **Suggested fix:** Change to `Accessible name: "Search"`
- **Popup list annotation** — Style guide requires role values in lowercase; annotation uses `Role: LISTBOX` → **Suggested fix:** Change to `role: listbox`

---

### Completeness gaps  2

- **Missing:** `aria-autocomplete` on combobox input — required by WCAG 2.2 SC 4.1.2 (Name, Role, Value)
- **Missing:** `aria-activedescendant` on combobox input — required when focus stays on input while list is navigated — SC 4.1.2

---

### Correctness errors  1

- **Combobox popup** — Annotated as `role: listbox` but `aria-haspopup` on the input is missing the popup type → **Should be:** `aria-haspopup: listbox` *(ARIA: aria-haspopup requires explicit popup type)*

---

### Consistency issues  1

- **Expanded state** is written as `aria-expanded: true` on the combobox and `expanded: true` on the accordion trigger → **Use:** `aria-expanded: true` throughout

---

### Summary

**6 issue(s) found** — 2 style · 2 completeness · 1 correctness · 1 consistency
