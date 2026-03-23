# Rubric: Writing Notifications and Toasts

---

## Pass if all are true
- [ ] Notification type matches the message content
- [ ] Message clearly states what happened
- [ ] Message follows approved pattern for its type (success, error, warning, info)
- [ ] Message is ≤80 characters
- [ ] Fragment messages have no trailing period
- [ ] Complete sentence messages end with a period
- [ ] Action label (button) uses title case and has no trailing period
- [ ] Action label (link) uses sentence case and has no trailing period
- [ ] Action label (if present) is ≤20 characters
- [ ] Action label is descriptive — never "Learn more"
- [ ] No exclamation points in message or action label
- [ ] Success/info use auto-dismiss (4-8 seconds)
- [ ] Errors requiring action do NOT auto-dismiss
- [ ] Undo actions have sufficient time before dismiss (6+ seconds)
- [ ] Visual style (color, icon) matches notification type
- [ ] One notification visible at a time (or queued)
- [ ] Dismiss option always available

---

## Fail if any are true
- [ ] Error auto-dismisses before user can read/act
- [ ] Success notification used for a failed action
- [ ] Warning used when error is appropriate
- [ ] Message uses exclamation point
- [ ] Message uses "Learn more" as action text
- [ ] Message uses the word "failure"
- [ ] Success message doesn't follow `{Action} + {object}` pattern
- [ ] Error message doesn't follow `Failed to {action} {object}` pattern
- [ ] Fragment message has a trailing period
- [ ] Complete sentence message is missing a trailing period
- [ ] Button action label uses sentence case or has a trailing period
- [ ] Character limits exceeded
- [ ] No dismiss option for persistent notifications
- [ ] Multiple overlapping notifications (visual chaos)
- [ ] Undo action auto-dismisses in <5 seconds
- [ ] Message is vague ("Something happened")
