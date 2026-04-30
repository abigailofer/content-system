# Templates: A11y Content Annotations Review

Annotation templates for common element types. Use these as starting points when writing or correcting annotations.

---

## Table of contents
- [Interactive elements](#interactive-elements)
- [Images](#images)
- [Form inputs](#form-inputs)
- [Dialogs and modals](#dialogs-and-modals)
- [Landmark structure](#landmark-structure)
- [Tabs](#tabs)
- [Combobox / autocomplete](#combobox--autocomplete)
- [Accordion / disclosure](#accordion--disclosure)
- [Live regions](#live-regions)
- [Review report template](#review-report-template)

---

## Interactive elements

### Button
```yaml
element: "[Button name]"
role: button
accessible_name: "[Visible label text]"
# Add if toggle:
aria_pressed: false   # becomes true when activated
# Add if disabled:
aria_disabled: true
```

### Link
```yaml
element: "[Link name]"
role: link
accessible_name: "[Descriptive destination or action — meaningful out of context]"
# If opens new tab:
# accessible_name: "[Label] (opens in new tab)"
```

### Icon-only button
```yaml
element: "[Button name]"
role: button
accessible_name: "[Action + object, e.g., 'Delete row']"
aria_label: "[Same as accessible name]"
# No visible text — label is provided programmatically
```

---

## Images

### Informative image
```yaml
element: "[Image name]"
type: informative
alt: "[What it shows and why it matters in this context]."
# Ends with period; no "image of" prefix; max 125 chars for simple images
```

### Decorative image
```yaml
element: "[Image name]"
type: decorative
alt: ""
aria_hidden: true
```

### Complex image (chart, diagram)
```yaml
element: "[Image name]"
type: complex
alt: "[Key insight, max 125 chars]."
aria_describedby: "[id of full description or data table]"
# Full description available: [location of extended description]
```

### Functional icon
```yaml
element: "[Icon name]"
type: functional
alt: "[Action the icon performs]."
# Or: accessible_name on the parent button
```

---

## Form inputs

### Text / email / password field
```yaml
element: "[Field name]"
role: textbox
label: "[Visible label text]"
aria_required: true   # or false — always annotate
aria_describedby: "[help-text-id]"   # if help text exists
error_state:
  aria_invalid: true
  aria_describedby: "[error-id]"
  error_text: "[What went wrong and how to fix it]"
```

### Checkbox
```yaml
element: "[Checkbox name]"
role: checkbox
accessible_name: "[Label text]"
aria_checked: false   # true | false | mixed
aria_required: true   # if required
```

### Radio button
```yaml
element: "[Radio group name]"
role: radiogroup
accessible_name: "[Group label]"
options:
  - role: radio
    accessible_name: "[Option label]"
    aria_checked: false
```

### Select / listbox
```yaml
element: "[Select name]"
role: listbox   # or combobox if editable
accessible_name: "[Label]"
aria_required: true
options:
  - role: option
    accessible_name: "[Option text]"
    aria_selected: false
```

---

## Dialogs and modals

### Confirmation dialog
```yaml
element: "[Dialog name]"
role: dialog
aria_labelledby: "[dialog-title-id]"   # Points to dialog heading
aria_describedby: "[dialog-body-id]"   # Points to description paragraph
focus:
  on_open: "[First focusable element — usually Cancel or first interactive element]"
  on_close: "[Trigger element that opened the dialog]"
focus_trap: true
```

### Alert dialog (irreversible action)
```yaml
element: "[Dialog name]"
role: alertdialog
aria_labelledby: "[dialog-title-id]"
aria_describedby: "[dialog-body-id]"
focus:
  on_open: "[Confirm button or least destructive action]"
  on_close: "[Trigger element]"
focus_trap: true
```

---

## Landmark structure

### Full page landmark set
```yaml
landmarks:
  - role: banner          # Site header — one per page
  - role: navigation
    aria_label: "[Label — required if multiple nav regions]"
  - role: main            # Primary content — one per page
  - role: complementary   # Sidebar or aside content
    aria_label: "[Label — required if multiple complementary regions]"
  - role: contentinfo     # Site footer — one per page
```

### Search region
```yaml
element: "Search"
role: search
aria_label: "[Label if multiple search regions]"
```

---

## Tabs

```yaml
tablist:
  role: tablist
  aria_label: "[Label describing the tab group]"
  tabs:
    - role: tab
      accessible_name: "[Tab label]"
      aria_selected: true   # Active tab
      aria_controls: "[panel-id]"
    - role: tab
      accessible_name: "[Tab label]"
      aria_selected: false
      aria_controls: "[panel-id]"
  panels:
    - role: tabpanel
      aria_labelledby: "[tab-id]"
      id: "[panel-id]"
```

---

## Combobox / autocomplete

```yaml
element: "[Combobox name]"
role: combobox
accessible_name: "[Label]"
aria_expanded: false   # becomes true when popup opens
aria_autocomplete: list   # none | list | inline | both
aria_controls: "[listbox-id]"
aria_activedescendant: "[focused-option-id]"   # when navigating within popup

popup:
  role: listbox
  id: "[listbox-id]"
  options:
    - role: option
      accessible_name: "[Option text]"
      aria_selected: false
```

---

## Accordion / disclosure

```yaml
element: "[Accordion section name]"
trigger:
  role: button
  accessible_name: "[Section heading text]"
  aria_expanded: false   # becomes true when expanded
  aria_controls: "[panel-id]"
panel:
  role: region   # optional; use for landmark-like sections
  aria_labelledby: "[trigger-id]"
  id: "[panel-id]"
```

---

## Live regions

### Status message (polite)
```yaml
element: "[Status region name]"
role: status   # aria-live: polite, aria-atomic: true
text: "[Status message text]"
```

### Alert (assertive)
```yaml
element: "[Alert region name]"
role: alert   # aria-live: assertive, aria-atomic: true
text: "[Alert message text]"
```

### Log (scrolling history)
```yaml
element: "[Log name]"
role: log   # aria-live: polite, aria-atomic: false
aria_label: "[Log label]"
```

---

## Review report template

Copy this template for each review output:

```markdown
## A11y Annotation Review

**Scope:** [component or screen name, or "not specified"]
**Style guide:** [provided / not provided — style checks skipped]
**Standard:** WCAG 2.2 AA

---

### Style issues  [N]

- **[Element / annotation ref]** — [Deviation from style guide] → **Suggested fix:** [corrected text]

*None found.*

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
```
