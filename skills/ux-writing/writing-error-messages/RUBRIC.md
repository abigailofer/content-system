# Rubric: Writing Error Messages

---

## Pass if all are true
- [ ] Title states what went wrong in user terms (not technical jargon)
- [ ] Title is ≤60 characters
- [ ] Title uses sentence case
- [ ] Title has no trailing period
- [ ] Body (if present) is ≤150 characters
- [ ] Body uses sentence case and ends with a period
- [ ] Action label is ≤25 characters
- [ ] Action label uses title case
- [ ] Action label has no trailing period
- [ ] Action is specific and actionable (not generic "OK" unless dismissal is the only option)
- [ ] Message does not blame the user ("You entered..." → "Enter...")
- [ ] Message does not expose internal errors, codes, or stack traces
- [ ] Message does not use the word "failure"
- [ ] Tone is neutral, direct, and action-oriented — no humor, drama, or over-apologizing
- [ ] Message tells user how to recover or what to do next
- [ ] Error type is correctly classified per reference/error-categories.md

---

## Fail if any are true
- [ ] Title is vague ("Error", "Couldn't complete your request" with no context)
- [ ] Title uses title case or has a trailing period
- [ ] Title uses "Something went wrong" with no further context
- [ ] Body is missing a trailing period
- [ ] Action label uses sentence case or has a trailing period
- [ ] Message uses technical terms users won't understand
- [ ] Message uses the word "failure"
- [ ] Message blames or scolds the user
- [ ] Action is missing when recovery is possible
- [ ] Action label is vague when specific action exists ("OK" instead of "Try Again")
- [ ] Character limits exceeded
- [ ] Message creates anxiety disproportionate to severity
- [ ] Tone uses humor, drama, or over-apologizing
- [ ] Error code or exception text visible to user

---

## Pre-ship checklist
Run before shipping any error message:

- [ ] Clear problem statement — does the title state what failed in user terms?
- [ ] Clear next step — does the user know what to do next?
- [ ] No "failure" — is the word "failure" absent from all copy?
- [ ] No "Something went wrong" — is a specific problem stated instead?
- [ ] No technical exposure — are stack traces, error codes, and exception text hidden?
- [ ] Meets character limits — title ≤60, body ≤150, action ≤25?
- [ ] Accessible — is error text programmatically associated with its field or component?
- [ ] Uses aria-live when dynamic — is the error announced to screen readers?
