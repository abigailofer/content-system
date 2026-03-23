# Templates: Writing Notifications and Toasts

---

## Default notification structure
```md
[Icon] **[Message]** [Action - optional] [Dismiss X]
```

## Structured output format
```yaml
notification:
  type: "<success|error|warning|info>"
  message: "<what happened - sentence case, max 80 chars>"
  action:
    label: "<button text - title case, no period, max 20 chars>"
    type: "<navigate|undo|retry|dismiss>"
  persistence: "<auto-dismiss|manual-dismiss|persistent>"
  auto_dismiss_seconds: <4-8>  # only for auto-dismiss
  aria_live: "<polite|assertive>"
  # polite: success, info; assertive: errors requiring immediate attention
```

---

## Variations by notification type

### Success
```yaml
notification:
  type: "success"
  message: "Changes saved"
  # Pattern: {Action} + {object} — style guide §11.13.2
  action: null
  persistence: "auto-dismiss"
  auto_dismiss_seconds: 4
  aria_live: "polite"
```

### Success with undo
```yaml
notification:
  type: "success"
  message: "Message archived"
  action:
    label: "Undo"
    type: "undo"
  persistence: "auto-dismiss"
  auto_dismiss_seconds: 6
  aria_live: "polite"
```

### Error (requires attention)
```yaml
notification:
  type: "error"
  message: "Failed to save changes."
  # Pattern: Failed to {action} {object} — style guide §11.13.3
  action:
    label: "Retry"
    type: "retry"
  persistence: "manual-dismiss"
  aria_live: "assertive"
```

### Warning
```yaml
notification:
  type: "warning"
  message: "Your session expires in 5 minutes."
  action:
    label: "Stay Signed In"
    type: "navigate"
  persistence: "manual-dismiss"
  aria_live: "polite"
```

### Info
```yaml
notification:
  type: "info"
  message: "New: Dark mode is now available."
  action: null
  persistence: "auto-dismiss"
  auto_dismiss_seconds: 8
  aria_live: "polite"
```

Note: If an info notification needs an action, use descriptive link text that names the destination — never "Learn more". Example: "Explore dark mode" or "See what's new in settings".

---

## Message patterns

| Type | Pattern | Example |
|------|---------|---------|
| Success | `{Action} + {object} + {quantity or name}` | `Labels added to 3 tests` |
| Success | `{Action} + {object}` | `Document saved` |
| Error | `Failed to {action} {object}.` | `Failed to save changes.` |
| Warning | State the risk clearly | `Storage almost full. 95% used.` |
| Info | State the update | `New: Dark mode is now available.` |

---

## Period rules
- Fragment messages (no verb): no period — `"Document saved"`, `"Link copied"`
- Complete sentence messages: period on each sentence — `"Failed to save changes."`, `"Your session expires in 5 minutes."`
- Action labels (buttons): no period
- Link text: no period

---

## Persistence guidelines
- **auto-dismiss**: Success, info (no action required)
- **manual-dismiss**: Warnings, errors with optional actions
- **persistent**: Errors requiring action, critical warnings

---

## Allowed variations
- Omit action for simple confirmations
- Stack notifications if multiple (max 3 visible)
- Use longer auto-dismiss for messages with actions (6-8s)
- Never use exclamation points in notification messages
