# Writing Loading and Latency Messaging

---
name: writing-loading-and-latency-messaging
description: Write clear loading states and latency messages for UI. Use when users wait for content to load, actions to complete, or when explaining delays in system response.
---

## Quick start
Collect or infer:
- Loading type (initial load, action response, background refresh)
- Expected duration (instant, short, long, unknown)
- User interruptibility (can user do other things?)
- Fallback if loading fails

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Classify latency tier using [reference/latency-tiers.md](reference/latency-tiers.md)
2. Determine if user can continue working or must wait
3. Write loading message appropriate to duration — fragment, no period
4. Write detail text if needed — sentence case, ends with period
5. Plan transition to loaded or error state
6. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Must show loading indicator for >1 second waits
- **Medium**: Message detail scales with expected wait time
- **Allowed variation**: Silent loading for <1 second operations

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Loading message | Sentence case | No — it's a fragment | 40 chars | Omit for short waits |
| Detail text | Sentence case | Yes | 100 chars | Include for waits >10s |
| Cancel label | Title case | No | 25 chars | Required for interruptible operations |
| Fallback error message | Sentence case | Yes | 150 chars | Always required; follow system error pattern |

### Tone rules for fallback messages
- Follow the system error pattern: problem statement + recovery action
- Use "We couldn't" not "Couldn't" for system-caused failures
- Never use "failure" or "failed"
- Avoid "please" unless the user is being asked to do something genuinely effortful
- Never imply the user caused the delay

### Word choice
- Use "select" not "click" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

### Accessibility
- Use aria-live regions for dynamic loading state changes (style guide §10.4)
- Announce loading completion and errors to screen readers
- Loading indicators must have accessible text equivalents

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Latency tiers: [reference/latency-tiers.md](reference/latency-tiers.md)
