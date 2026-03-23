# Writing Notifications and Toasts

---
name: writing-notifications-and-toasts
description: Write clear notification and toast messages for UI. Use when showing transient alerts, system notifications, success confirmations, warnings, or in-app messages that don't require immediate action.
---

## Quick start
Collect or infer:
- Notification type (success, error, warning, info)
- Urgency (immediate, informational, background)
- Action required (none, optional, required)
- Persistence (auto-dismiss, manual dismiss, persistent)

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Classify notification type using [reference/notification-types.md](reference/notification-types.md)
2. Determine urgency and persistence
3. Write the message (what happened) following the approved pattern
4. Add action if applicable — button in title case, link text descriptive
5. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Type determines visual treatment (color, icon)
- **Medium**: Message length varies by complexity
- **Allowed variation**: Actions optional for pure confirmations

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Message | Sentence case | Fragment: no period. Complete sentence: yes. | 80 chars | Follow approved patterns |
| Action label (button) | Title case | No | 20 chars | Must be specific; never "Learn more" |
| Action label (link) | Sentence case | No | 20 chars | Must describe destination |

### Message patterns
| Type | Pattern | Example |
|------|---------|---------|
| Success | `{Action} + {object} + {quantity or name}` | `Labels added to 3 tests` |
| Success | `{Action} + {object}` | `Document saved` |
| Error | `Failed to {action} {object}.` | `Failed to save changes.` |
| Warning | State the risk clearly | `Storage almost full. 95% used.` |
| Info | State the update | `New: Dark mode is now available.` |

### Persistence rules
- **auto-dismiss** (4–8s): success, info with no required action
- **manual-dismiss**: warnings, errors with optional actions
- **persistent**: errors requiring action, critical warnings
- Never auto-dismiss errors that need user attention
- Use longer auto-dismiss (6–8s) for messages with actions

### Tone rules
- Never use exclamation points (style guide §1.7.5)
- Never use "Learn more" as action text (style guide §4.3.3)
- Avoid "please" unless user effort is significant
- Never use the word "failure"

### Word choice
- Use "select" not "click" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Notification types: [reference/notification-types.md](reference/notification-types.md)
- Glossary: [../../reference/glossary.md](../../reference/glossary.md)
- Words to use: [../../reference/words-to-use.md](../../reference/words-to-use.md)
- Words to avoid: [../../reference/words-to-avoid.md](../../reference/words-to-avoid.md)
