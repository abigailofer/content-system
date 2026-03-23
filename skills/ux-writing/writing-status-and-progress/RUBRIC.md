# Rubric: Writing Status and Progress

---

## Pass if all are true
- [ ] Status label accurately reflects current system state
- [ ] Status label is ≤30 characters
- [ ] Status label uses sentence case
- [ ] Status label has no trailing period
- [ ] Detail text (if present) is ≤100 characters
- [ ] Detail text uses sentence case
- [ ] Complete sentence detail text ends with a period
- [ ] Fragment detail text (e.g. "3 of 10 files") has no trailing period
- [ ] Action label (if present) uses title case and has no trailing period
- [ ] Status labels are consistent for the same state across all pages and views
- [ ] Progress indicator type matches actual knowledge (determinate only if known)
- [ ] Indeterminate progress doesn't show fake percentages
- [ ] State transitions make sense (pending → in-progress → completed/failed)
- [ ] Failed states include recovery guidance or action
- [ ] User knows if action is required from them
- [ ] Long-running tasks set duration expectations
- [ ] Completed states confirm what happened

---

## Fail if any are true
- [ ] Progress percentage shown when actual progress is unknown
- [ ] Status doesn't update as state changes
- [ ] Stuck states with no timeout or recovery
- [ ] "Loading..." used for everything without context
- [ ] Failed state with no explanation or next step
- [ ] Character limits exceeded
- [ ] Status label uses title case or has a trailing period
- [ ] Complete sentence detail text is missing a trailing period
- [ ] Action label uses sentence case or has a trailing period
- [ ] Same state uses different labels across pages (e.g. "Saved" in one place, "All changes saved" in another)
- [ ] Past-tense label for in-progress state ("Uploaded" while still uploading)
- [ ] No visual indicator accompanying status text
