# Templates: Writing Confirmation Dialogs

---

## Default confirmation dialog structure
```md
## [Headline - what will happen? Sentence case, no period]
[Body - consequences or details. Sentence case, ends with period.]
[Cancel button] | [Confirm button]
```

---

## Structured output format
```yaml
confirmation_dialog:
  headline: "<what will happen - sentence case, no period, max 60 chars>"
  body: "<consequences - sentence case, ends with period, max 200 chars, optional>"
  confirm:
    label: "<specific verb - title case, no period, max 20 chars>"
    style: "<default|destructive>"
  cancel:
    label: "<safe exit - title case, no period, max 15 chars>"
```

---

## Variations by action type

### Destructive action (delete, remove permanently)
```yaml
confirmation_dialog:
  headline: "Delete [item name]?"
  body: "You cannot undo this action. All associated data will be permanently removed."
  confirm:
    label: "Delete"
    style: "destructive"
  cancel:
    label: "Cancel"
```

### Significant change (affects others or hard to reverse)
```yaml
confirmation_dialog:
  headline: "Remove [person] from [team]?"
  body: "They'll lose access to all team projects and files."
  confirm:
    label: "Remove"
    style: "destructive"
  cancel:
    label: "Cancel"
```

### Simple confirmation (reversible)
```yaml
confirmation_dialog:
  headline: "Archive this project?"
  body: "You can restore it anytime from the archive."
  confirm:
    label: "Archive"
    style: "default"
  cancel:
    label: "Cancel"
```

### Bulk action
```yaml
confirmation_dialog:
  headline: "Delete 15 items?"
  body: "This will permanently delete all selected items. You cannot undo this action."
  confirm:
    label: "Delete 15 items"
    style: "destructive"
  cancel:
    label: "Cancel"
```

### Abort (all progress lost)
```yaml
confirmation_dialog:
  headline: "Quit [task name]?"
  body: "Your progress will be lost. You'll need to start from the beginning."
  confirm:
    label: "Quit [Task]"
    style: "destructive"
  cancel:
    label: "Cancel"
```

### Abort (progress saved, activity ends)
```yaml
confirmation_dialog:
  headline: "Stop [task name]?"
  body: "Your progress has been saved. You can resume anytime."
  confirm:
    label: "Stop"
    style: "default"
  cancel:
    label: "Cancel"
```

### Leave page (unsaved changes)
```yaml
confirmation_dialog:
  headline: "Leave without saving?"
  body: "Changes that you made will not be saved."
  confirm:
    label: "Leave Anyway"
    style: "destructive"
  cancel:
    label: "Cancel"
```

### Non-destructive confirmation
```yaml
confirmation_dialog:
  headline: "Apply [change name]?"
  body: "This replaces your current [item] with [change]. You can undo this in settings."
  confirm:
    label: "Apply"
    style: "default"
  cancel:
    label: "Cancel"
```

---

## Allowed variations
- Omit body for simple, reversible, single-item actions where consequences are obvious
- Include count in confirm button for bulk actions (e.g. "Delete 15 items")
- Use "Keep [item]" instead of "Cancel" when it more clearly describes the safe outcome
- Use "Quit" when all progress will be lost; use "Stop" when progress is saved but activity ends
