# Writing Status and Progress

---
name: writing-status-and-progress
description: Write clear status indicators and progress messages for UI. Use when showing system state, task progress, sync status, connection state, or any ongoing process feedback.
---

## Quick start
Collect or infer:
- Status type (system state, task progress, sync, connection)
- Current state (pending, in-progress, completed, failed)
- Duration expectation (instant, seconds, minutes, indefinite)
- User action required (none, optional, required)

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Identify status type using [reference/status-states.md](reference/status-states.md)
2. Determine the current state in the lifecycle
3. Write the status label (what's happening) — sentence case, no period
4. Add detail text if duration or action needed — sentence case; complete sentences end with period, fragments do not
5. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Status must accurately reflect system state
- **Medium**: Detail text optional based on context
- **Allowed variation**: Tone adjusts for success vs. waiting states

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Status label | Sentence case | No | 30 chars | Must accurately reflect current state |
| Detail text | Sentence case | Yes if complete sentence; no if fragment | 100 chars | Optional |
| Action label | Title case | No | 25 chars | Required for interruptible or failed states |

### Status label rules
- Use the same label consistently for the same state across all pages and views (WCAG 3.2.4)
- Never use "Loading..." generically — always specify what is loading
- Never show fake progress percentages for indeterminate states
- Never use past tense for in-progress states ("Uploaded" while still uploading)

### Tone rules
- Completed states should confirm what happened
- Failed states must include recovery guidance or a next action
- Long-running tasks must set duration expectations upfront
- Use "select" not "click" in detail text (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)

### Accessibility
- Use aria-live regions for dynamic status updates (style guide §10.4)
- Polite aria-live for routine updates; assertive for critical failures
- Status indicators must have accessible text — never icon-only

### Task completion
- For in-app notifications on task completion, follow the toast pattern: `{Action} + {object}` (style guide §11.13.2)
- See writing-notifications-and-toasts skill for completion toast copy

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Status states: [reference/status-states.md](reference/status-states.md)
- Notifications: [../writing-notifications-and-toasts/SKILL.md](../writing-notifications-and-toasts/SKILL.md)
- Glossary: [../../reference/glossary.md](../../reference/glossary.md)
- Words to use: [../../reference/words-to-use.md](../../reference/words-to-use.md)
- Words to avoid: [../../reference/words-to-avoid.md](../../reference/words-to-avoid.md)
