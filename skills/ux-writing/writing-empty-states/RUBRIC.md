# Rubric: Writing Empty States

---

## Pass if all are true
- [ ] Empty state type is correctly identified
- [ ] Headline is present (required in all empty states)
- [ ] If headline is H1, it is unique across pages — flag if it matches a known page title and confirm with user if unsure
- [ ] Headline acknowledges the current state clearly
- [ ] Headline is ≤50 characters
- [ ] Headline uses sentence case
- [ ] Headline has no trailing period
- [ ] Support text (if present) is ≤120 characters
- [ ] Support text uses sentence case
- [ ] Support text ends with a period — unless it ends with a link
- [ ] Action label is ≤25 characters
- [ ] Action label uses title case
- [ ] Action label has no trailing period
- [ ] Support button label is "Contact Support"
- [ ] Support inline text is "Contact Evinced Support"
- [ ] CTA rules followed by empty state type:
  - First-run 1a (with CTA): primary CTA present
  - First-run 1b (no CTA): no CTA present; support text guides user or sets expectation
  - No-results 2a: "Clear Filters" or "View All [Items]" offered
  - No-results 2b: corrected query offered as CTA
  - User-cleared 3a: CTA present
  - User-cleared 3b: CTA omitted; support text sets expectation
  - Error-caused 4a: "Refresh Page" CTA present
  - Error-caused 4b: "Back to Home" CTA present
- [ ] First-run states include motivation or value, not just "nothing here"
- [ ] First-run 1b support text either guides the user to act elsewhere, or sets expectation that content will appear here
- [ ] No-results states suggest how to get results
- [ ] Message does not make user feel they did something wrong
- [ ] Copy matches the content type (items, projects, messages, etc.)

---

## Fail if any are true
- [ ] Headline is missing
- [ ] Headline is generic ("Nothing here") without context
- [ ] Headline uses title case or has a trailing period
- [ ] Support text repeats the headline
- [ ] Support text is missing a trailing period (unless ending with a link)
- [ ] Action label uses sentence case or has a trailing period
- [ ] No action provided when user can take action to populate
- [ ] CTA present in first-run 1b state
- [ ] No-results state offers no way to reset or adjust (no "Clear Filters" or "View All")
- [ ] Error-caused state offers no recovery action
- [ ] First-run state is demotivating ("You have no data")
- [ ] No-results state doesn't help user adjust their search
- [ ] Empty state conveys meaning through imagery only, with no text
- [ ] Character limits exceeded
- [ ] Wrong empty state type diagnosed (e.g., treating error as first-run)
- [ ] Technical language used ("null", "0 records")
