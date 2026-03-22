# Templates: Writing Error Messages

---

## Default error message structure
```md
## [Error title]
[Body explaining cause or context - optional]
**Action:** [Button Label]
```

## Structured output format
```yaml
error:
  title: "<what went wrong - sentence case, no period, max 60 chars>"
  body: "<why it happened - sentence case, ends with period, max 150 chars, optional>"
  action:
    label: "<button text - title case, no period, max 25 chars>"
    type: "<retry|dismiss|navigate|contact>"
```

---

## Variations by error type

### Validation error (inline)
```md
[Field-specific message under the input — sentence case, no period]
```

Common patterns (style guide §12.2.2):
- Missing required field → `Enter {field}`
- Missing selection → `Select {option}`
- Range/limit exceeded → `Select up to {n} {items}`
- Character limit → `{Name} can't be longer than {n} characters`
- Invalid characters → `{Field} can't contain {restriction}`
- Format required → `{Field} must be {format}`
- Already exists → `{Name} already exists`
- Dependency gating → `You need to {required action} before you can {attempted action}`

### System error (modal or banner)
```md
## Couldn't load [item/feature]
We're working on it. Try again in a few minutes.
**Action:** Try Again
```

### System error (toast)
```md
Failed to [action] [object]
```
Examples:
- "Failed to save changes."
- "Failed to load results."

### Network error
```md
## Couldn't save your changes
Check your internet connection and try again.
**Action:** Retry
```

### Permission error
```md
## You don't have access to [feature]
Contact your admin to request access.
**Action:** Request Access
```

### Not found error
```md
## [Item] not found
This [item] may have been moved or deleted.
**Action:** Go Back
```

---

## Allowed variations
- Omit body if the title + action make the situation and fix obvious
- Use inline format for field validation; use modal/banner for system-level errors
- Adjust formality based on product voice, but never add humor to errors
- Never use the word "failure" in error copy
