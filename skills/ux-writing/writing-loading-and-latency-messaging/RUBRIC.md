# Rubric: Writing Loading and Latency Messaging

---

## Pass if all are true
- [ ] Latency tier correctly identified
- [ ] Loading indicator matches expected duration
- [ ] Message (if present) is ≤40 characters
- [ ] Message is a fragment — no trailing period
- [ ] Detail text (if present) is ≤100 characters
- [ ] Detail text uses sentence case and ends with a period
- [ ] Cancel label (if present) uses title case and has no trailing period
- [ ] Fallback error message ends with a period
- [ ] Fallback error message does not use "please" unless user effort is significant
- [ ] Fallback error message does not use the word "failure"
- [ ] No loading state shown for instant operations (<300ms)
- [ ] Spinner or skeleton shown for short waits (300ms-2s)
- [ ] Message appears for medium+ waits (>2s)
- [ ] Time estimate provided for very long waits (>60s)
- [ ] Interruptible operations can be cancelled
- [ ] Support button label is "Contact Support"
- [ ] Support inline text is "Contact Evinced Support"

---

## Fail if any are true
- [ ] Loading shown for instant operations (perceived slowness)
- [ ] No indicator for operations >1 second
- [ ] Message implies faster completion than realistic
- [ ] Message has a trailing period
- [ ] Detail text is missing a trailing period
- [ ] Cancel label uses sentence case or has a trailing period
- [ ] Fallback error message uses "please" for a low-effort action (e.g. selecting retry)
- [ ] Fallback error message uses the word "failure"
- [ ] No timeout (infinite loading possible)
- [ ] Character limits exceeded
- [ ] User stuck with no way to cancel or go back
- [ ] Loading message is overly technical
- [ ] No transition to error state on failure
