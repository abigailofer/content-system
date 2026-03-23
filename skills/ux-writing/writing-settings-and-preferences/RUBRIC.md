# Rubric: Writing Settings and Preferences

---

## Pass if all are true
- [ ] Label clearly names what the setting controls
- [ ] Label is ≤40 characters
- [ ] Label uses sentence case
- [ ] Label has no trailing period
- [ ] Description (if present) explains the effect of the setting
- [ ] Description is ≤120 characters
- [ ] Description uses sentence case and ends with a period
- [ ] Placeholder (if present) uses sentence case and has no trailing period
- [ ] Action label (if present) uses title case and has no trailing period
- [ ] Toggle labels describe the ON state (not what's disabled)
- [ ] Toggle and checkbox labels are phrased positively
- [ ] No double negatives ("Disable notifications" toggle = confusing)
- [ ] Default value is specified and sensible
- [ ] Setting type matches the interaction (binary = toggle, options = select)
- [ ] Related settings are grouped logically
- [ ] Destructive settings have appropriate warnings and confirmation
- [ ] Links in descriptions are descriptive — never "Learn more"

---

## Fail if any are true
- [ ] Label is vague ("Setting 1", "Option")
- [ ] Label uses title case or has a trailing period
- [ ] Description is missing a trailing period
- [ ] Action label uses sentence case or has a trailing period
- [ ] Toggle describes OFF state ("Disable..." as a toggle)
- [ ] Toggle or checkbox label is phrased negatively
- [ ] Double negative logic ("Don't hide...")
- [ ] Description repeats the label without adding information
- [ ] Description uses "This can't be undone" — use "You cannot undo this action"
- [ ] Description uses vague link text ("Learn more")
- [ ] Character limits exceeded
- [ ] No default specified for required setting
- [ ] Destructive action (delete account) lacks confirmation
- [ ] Technical jargon without explanation
