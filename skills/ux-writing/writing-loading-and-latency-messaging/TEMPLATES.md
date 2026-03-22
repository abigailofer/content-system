# Templates: Writing Loading and Latency Messaging

---

## Default loading structure
```md
[Loading indicator]
**[Loading message]**
[Detail text — for long waits.]
```

## Structured output format
```yaml
loading_state:
  tier: "<instant|short|medium|long|unknown>"
  message: "<what's loading - fragment, no period, max 40 chars>"
  detail: "<additional context - sentence case, ends with period, max 100 chars, optional>"
  indicator: "<spinner|skeleton|progress-bar|none>"
  interruptible: <true|false>
  cancel_label: "<title case, no period, max 25 chars>"
  timeout:
    duration_seconds: <number>
    fallback: "<error message - sentence case, ends with period, max 150 chars>"
```

---

## Variations by latency tier

### Instant (<300ms) — no loading state
```yaml
loading_state:
  tier: "instant"
  message: null
  indicator: "none"
```

### Short (300ms–2s)
```yaml
loading_state:
  tier: "short"
  message: null
  indicator: "spinner"
  interruptible: false
  timeout:
    duration_seconds: 10
    fallback: "We couldn't complete this action. Try again."
```

### Medium (2–10s)
```yaml
loading_state:
  tier: "medium"
  message: "Loading..."
  detail: null
  indicator: "spinner"
  interruptible: true
  timeout:
    duration_seconds: 15
    fallback: "We couldn't load this. Try refreshing."
```

### Long (10s–60s)
```yaml
loading_state:
  tier: "long"
  message: "Loading your data..."
  detail: "This may take a moment."
  indicator: "progress-bar"
  interruptible: true
  cancel_label: "Cancel"
  timeout:
    duration_seconds: 60
    fallback: "We couldn't load your data. Check your connection and try again."
```

### Very long (>60s)
```yaml
loading_state:
  tier: "long"
  message: "Processing your request..."
  detail: "This usually takes 2-3 minutes. You can close this page."
  indicator: "progress-bar"
  interruptible: true
  cancel_label: "Cancel"
  notification_on_complete: true
  completion_toast:
    text: "[Action] [object]."
    # Toast pattern: {Action} + {object} — style guide §11.13.2
    # Example: "Report generated." / "Import complete."
    aria_live: "polite"
  timeout:
    duration_seconds: 300
    fallback: "We couldn't complete your request. Try again or contact support."
```

### Unknown duration
```yaml
loading_state:
  tier: "unknown"
  message: "Working on it..."
  detail: "This may take a few moments."
  indicator: "spinner"
  interruptible: true
  cancel_label: "Cancel"
  timeout:
    duration_seconds: 180
    fallback: "This is taking longer than expected. Try again or check back later."
```

---

## Skeleton loading (for content areas)
```yaml
loading_state:
  tier: "medium"
  message: null
  indicator: "skeleton"
  skeleton_areas: ["header", "content-list", "sidebar"]
  timeout:
    duration_seconds: 15
    fallback: "We couldn't load this content. Try refreshing."
```

---

## Fallback error message patterns
Follow the system error pattern: `We couldn't {action} {object}. {Recovery action}.`

| Scenario | Pattern | Example |
|----------|---------|---------|
| Load failure | `We couldn't load {item}. {Recovery}.` | `We couldn't load your dashboard. Try refreshing.` |
| Save failure | `We couldn't save {item}. {Recovery}.` | `We couldn't save your changes. Try again.` |
| Action failure | `We couldn't complete {action}. {Recovery}.` | `We couldn't complete your request. Try again.` |
| Timeout | `{Item/action} timed out. {Recovery}.` | `Report generation timed out. Try again or contact support.` |
| Unknown duration exceeded | `This is taking longer than expected. {Recovery}.` | `This is taking longer than expected. Check back later or try again.` |

---

## Allowed variations
- Use skeleton screens for content-heavy pages
- Show partial content as it loads (progressive)
- Allow cancel for interruptible operations
- For very long operations, notify on completion via toast: `{Action} {object}.`
