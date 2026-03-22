# Rubric: Writing Empty States

---

## Pass if all are true
- [ ] Empty state type is correctly identified
- [ ] Headline is present (required in all empty states)
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
- [ ] Action is relevant to populating or resolving the empty state
- [ ] CTA rules followed by empty state type:
  - First-run: primary CTA present
  - No-results: "Clear Filters" or "View All [Items]" offered
  - User-cleared: CTA present if user can populate; omitted if they cannot
  - Error-caused: recovery CTA present ("Refresh Page" or "Back to Home")
- [ ] First-run states include motivation or value, not just "nothing here"
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
- [ ] No-results state offers no way to reset or adjust (no "Clear Filters" or "View All")
- [ ] Error-caused state offers no recovery action
- [ ] First-run state is demotivating ("You have no data")
- [ ] No-results state doesn't help user adjust their search
- [ ] Empty state conveys meaning through imagery only, with no text
- [ ] Character limits exceeded
- [ ] Wrong empty state type diagnosed (e.g., treating error as first-run)
- [ ] Technical language used ("null", "0 records")
