# Writing Accessible UI Copy

Write inclusive, accessible content that works for all users regardless of ability, assistive technology, or context of use.

---

## Table of contents
- [Core principles](#core-principles)
- [When to apply](#when-to-apply)
- [Key techniques](#key-techniques)
- [Inputs required](#inputs-required)
- [Quality criteria](#quality-criteria)
- [WCAG alignment](#wcag-alignment)
- [COGA alignment](#coga-alignment)

---

## Core principles

### 1. Content must be perceivable
All users must be able to access information regardless of sensory ability. Text alternatives, clear structure, sufficient contrast, and non-color indicators all matter.

### 2. Content must be understandable
Use plain language, consistent terminology, and predictable patterns. Complexity excludes users with cognitive disabilities. Instructions should be front-loaded and chunked.

### 3. Content must support assistive technology
Screen readers, voice control, and other assistive tools rely on properly structured, labeled, and announced content.

### 4. Content must work in any context
Users may have situational disabilities (bright sunlight, noisy environment, one-handed use). Accessible content is resilient content.

### 5. Content must reduce cognitive load
Users should never need to remember information from earlier in a flow, decode unfamiliar labels, or interpret blame-laden error messages. Familiar patterns, inline repetition of key data, and neutral tone all reduce friction.

---

## When to apply

| Scenario | Accessibility focus |
|----------|---------------------|
| Images and icons | Alt text, decorative vs. informative, icon + label pairing |
| Interactive elements | Button labels, link text, form labels, consistent naming |
| Dynamic content | Status announcements, live regions, state changes |
| Navigation | Headings, landmarks, skip links, breadcrumbs, page titles |
| Data visualization | Text alternatives, patterns not just color |
| Errors and validation | Clear identification, programmatic association, supportive tone |
| Time-based content | Captions, transcripts, pause controls |
| Timed tasks | Visible timers, extension controls, announcements |
| Interruptions | Dismissible modals, focus management, keyboard access |
| Authentication | Cognitive-free options, paste allowed, plain setup guidance |
| Multi-step flows | Step indicators, location context, memory-free instructions |

---

## Key techniques

### Alt text
```yaml
image:
  type: "informative"
  alt: "[What it shows and why it matters in this context]."
  # Ends with a period — style guide §6.1.4
  # Not: "image of..." or filename
  # WCAG 1.1.1

image:
  type: "decorative"
  alt: ""
  aria_hidden: true
  # Empty alt for purely decorative images
  # WCAG 1.1.1

image:
  type: "complex"
  alt: "[Key insight in under 125 chars]."
  # Ends with a period — style guide §6.1.4
  aria_describedby: "[id of full description]"
  # WCAG 1.1.1
```

### Button and link labels
```yaml
# Accessible
button: "Save Draft"           # Title case, verb + noun — style guide §11.4.1, WCAG 4.1.2, COGA P3
button: "Continue"             # Familiar verb — COGA P3
link: "View pricing plans"     # Meaningful alone — WCAG 2.4.9
link: "Download 2025 report (PDF, 2.4 MB)"  # Format disclosed — WCAG 2.4.4

# Inaccessible
button: "Proceed"              # Unfamiliar — COGA P3
button: "Select here"          # Generic — WCAG 4.1.2
link: "Learn more"             # Meaningless alone — WCAG 2.4.9
```

### Verb choice
```yaml
# Use "select" not "click" — style guide §7.1
good: "Select View to see your results."
bad:  "Click View to see your results."

# Use "turn on / turn off" not "enable / disable" — style guide §7.1
good: "Turn on notifications to receive updates."
bad:  "Enable notifications to receive updates."
```

### Icon labels
```yaml
# Accessible — COGA P9
icon_button:
  icon: "🔔"
  label: "🔔 Notifications"

# Inaccessible
icon_button:
  icon: "🔔"
  # No label
```

### Form labels
```yaml
field:
  label: "Email address"              # Visible, programmatically associated — WCAG 3.3.2
  required_indicator: "(required)"    # Or mark optional with "(optional)" — WCAG 3.3.2
  help_text: "We'll send confirmation here."  # Ends with period — style guide §4.4.1
  placeholder: "name@example.com"     # Format example only, not a label — style guide §11.7.5
  error: "Enter a valid email address (e.g., name@company.com)"
  # No period on validation errors — style guide §4.4.2
  # Explains issue and fix — WCAG 3.3.1, COGA P6
```

### Headings
```yaml
structure:
  h1: "Account Settings"   # Title case, one per page — style guide §4.1.1, WCAG 2.4.6
  h2: "Profile"            # Sentence case, major sections — style guide §4.1.2, WCAG 2.4.10
  h3: "Display name"       # Sentence case, subsections
  # No skipping levels (h1 → h3) — WCAG 2.4.10
```

### Page titles
```yaml
title: "Checkout – Step 3: Payment | Acme Store"
# Unique, front-loaded, describes view — WCAG 2.4.2
# Update dynamically in SPAs — WCAG 2.4.2
```

### Status announcements and toasts
```yaml
# Toast — success pattern: {action} + {object} — style guide §11.13.2
toast_success:
  text: "Labels added to 3 tests."
  aria_live: "polite"

# Toast — failure pattern: Failed to {action} {object} — style guide §11.13.3
toast_failure:
  text: "Failed to add labels."
  aria_live: "assertive"

# General status
status:
  message: "Settings saved."       # Specific — WCAG 4.1.3
  aria_live: "polite"

error_announcement:
  message: "Payment didn't go through. Try another card."
  aria_live: "assertive"
  role: "alert"
  # Neutral tone — COGA P7; specific and actionable — WCAG 4.1.3
```

### Error messages
```yaml
# Validation error — no period — style guide §4.4.2, §12.2.1
validation_error: "Enter a valid email address (e.g., name@company.com)"

# System error — period used — style guide §4.4.1, §12.3
system_error: "We couldn't save your changes. Try again."

# COGA P6: state what happened and how to fix
# COGA P7: neutral, task-focused tone — no blaming "you"
# COGA P8: help link on blocking steps
error_with_help:
  message: "Payment didn't go through."
  help: "Contact support or call 800-123-4567."
```

### Modals
```yaml
# Confirmation modal — style guide §11.11.2
modal:
  heading: "Delete Account?"
  # Title format: action name + question mark
  body: "This permanently removes your account and its data. You cannot undo this action."
  confirm_label: "Delete Account"
  # Primary CTA matches title action; verb + noun
  cancel_label: "Cancel"
  focus:
    on_open: "First focusable element in modal"
    on_close: "Element that triggered modal"
  aria_labelledby: "modal-heading"
  aria_describedby: "modal-body"
```

### Color and sensory
```yaml
# WCAG 1.4.1: never color alone
error_indicator:
  color: "red"
  icon: "⚠"          # Icon supplements color
  text: "Required"   # Text supplements color

# WCAG 1.3.3: no sensory-only instructions
instruction: "Select the Start button."
# Not: "Select the green button."
```

### Authentication
```yaml
# WCAG 3.3.9: cognitive-free option is primary
login:
  primary: "Sign In With Passkey"
  alternatives: ["Sign In With Magic Link", "Sign In With Password"]

# WCAG 3.3.8: paste and autofill allowed
password_field:
  paste_allowed: true
  autofill_allowed: true

# COGA P5: repeat OTP inline
otp_instruction: "Enter the 6-digit code: 482910."
# Not: "Enter the code from the email above."
```

### Instructions and cognitive load
```yaml
# Front-load the action — COGA P2
instruction: "Select View to see your results."
# Not: "To see your results, select View."

# Chunk multi-step instructions — COGA P4
steps:
  - "Enter your name"
  - "Enter your email"
  - "Select Submit"
# Not: "Enter your name, then your email, then select Submit."

# Repeat key info inline — COGA P5
message: "Track your order with number 49327."
# Not: "Use the number above to track your order."
```

### Interruptions and modals
```yaml
# WCAG 2.2.4: non-emergency modals must be dismissible
modal:
  dismiss_label: "No thanks, continue shopping"
  snooze_label: "Remind me later"
  keyboard_accessible: true
  focus_on_open: "first focusable element"
  focus_on_close: "triggering element"
```

---

## Inputs required

| Input | Purpose | Required? |
|-------|---------|-----------|
| UI component | What element needs copy | Yes |
| Visual context | What sighted users see | Yes |
| User task | What user is trying to do | Yes |
| Assistive tech context | Screen reader, voice, etc. | Recommended |
| WCAG level target | A, AA, or AAA | Recommended |
| User's cognitive context | Memory demands, familiarity | Recommended |

---

## Quality criteria

### Must have
- [ ] All images have appropriate alt text ending with a period — WCAG 1.1.1, style guide §6.1.4
- [ ] Interactive elements have descriptive labels — WCAG 4.1.2
- [ ] Buttons use title case and verb + noun pattern — style guide §4.1.1, §11.4.1
- [ ] "Select" used instead of "click" — style guide §7.1
- [ ] "Turn on / turn off" used instead of "enable / disable" — style guide §7.1
- [ ] Headings follow logical hierarchy, no skipped levels — WCAG 2.4.6, 2.4.10
- [ ] H1 uses title case; H2–H4 use sentence case — style guide §4.1.1, §4.1.2
- [ ] Link text is meaningful out of context — WCAG 2.4.9
- [ ] Form fields have visible, associated labels — WCAG 3.3.2
- [ ] Optional fields explicitly marked "(optional)" — WCAG 3.3.2
- [ ] Validation errors explain the fix and have no trailing period — WCAG 3.3.1, style guide §4.4.2
- [ ] System errors end with a period — style guide §4.4.1
- [ ] No information conveyed by color alone — WCAG 1.4.1
- [ ] Error tone is neutral, not blaming — COGA P7
- [ ] Icons paired with visible text labels — COGA P9
- [ ] No all-caps, color-only, or sensory-only emphasis — COGA P10, WCAG 1.3.3
- [ ] No exclamation points — style guide §1.7.5
- [ ] Toast success pattern: `{action} + {object}` — style guide §11.13.2
- [ ] Toast failure pattern: `Failed to {action} {object}` — style guide §11.13.3

### Should have
- [ ] Reading level does not exceed Grade 9; aim for Grade 8 — WCAG 3.1.5
- [ ] Sentences do not exceed 25 words — WCAG 3.1.5, COGA P1
- [ ] Action or outcome stated first in instructions — COGA P2
- [ ] Multi-step instructions chunked into numbered list or bullets — COGA P4
- [ ] Key information repeated inline, not referenced from earlier — COGA P5
- [ ] Blocking steps include a direct help link — COGA P8
- [ ] Consistent terminology throughout — WCAG 3.2.4
- [ ] Status changes announced to assistive tech — WCAG 4.1.3
- [ ] Time-based content has text alternatives — WCAG 1.1.1
- [ ] Complex images have extended descriptions — WCAG 1.1.1
- [ ] Button labels use familiar, conventional verbs — COGA P3
- [ ] Page titles unique and front-loaded — WCAG 2.4.2
- [ ] Abbreviations expanded on first use — WCAG 3.1.4
- [ ] Unusual terms defined at first use — WCAG 3.1.3
- [ ] Confirmation required before destructive actions — WCAG 3.3.6
- [ ] Confirmation modal title uses action + question mark format — style guide §11.11.2
- [ ] Authentication offers a cognitive-free option — WCAG 3.3.8, 3.3.9
- [ ] Password fields allow paste and autofill — WCAG 3.3.8
- [ ] Non-emergency modals can be dismissed or snoozed — WCAG 2.2.4
- [ ] Dynamic text used in toasts and buttons where possible — style guide §5.1

### Avoid
- [ ] "Click here" or "Learn more" without context — WCAG 2.4.9
- [ ] "click" — use "select" instead — style guide §7.1
- [ ] "enable" / "disable" — use "turn on" / "turn off" — style guide §7.1
- [ ] "Image of..." in alt text — WCAG 1.1.1
- [ ] Placeholder text as only label — WCAG 3.3.2
- [ ] ALL CAPS for emphasis — COGA P10
- [ ] Exclamation points — style guide §1.7.5
- [ ] Directional instructions ("select the button on the left") — WCAG 1.3.3
- [ ] Sensory-only references ("the green button") — WCAG 1.3.3
- [ ] Blaming language in errors ("You entered the wrong code") — COGA P7
- [ ] Icon-only buttons with no text label — COGA P9
- [ ] Instructions that reference earlier content ("the number above") — COGA P5
- [ ] Purpose buried at end of instruction ("To see results, select View") — COGA P2
- [ ] Multi-step instructions written as a prose paragraph — COGA P4
- [ ] Unfamiliar button verbs ("Proceed", "Go forth") — COGA P3
- [ ] Paste blocked on password or code fields — WCAG 3.3.8
- [ ] Period on validation errors — style guide §4.4.2
- [ ] Missing period on alt text — style guide §6.1.4

---

## WCAG alignment

| Guideline | Requirement | Copy implication |
|-----------|-------------|------------------|
| 1.1.1 Non-text Content | Text alternatives | Alt text for images; ends with period; captions for media |
| 1.3.3 Sensory Characteristics | No sensory-only instructions | Reference labels, not color/shape/position |
| 1.4.1 Use of Color | Color not sole indicator | Add text or icon to all color cues |
| 2.2.1 Timing Adjustable | Visible timer + extend option | Accessible countdown; "Add time" button |
| 2.2.4 Interruptions | Non-emergency modals dismissible | Dismiss/snooze controls; focus managed |
| 2.4.1 Bypass Blocks | Skip links | Descriptive skip link as first element |
| 2.4.2 Page Titled | Unique, descriptive page titles | Front-load unique part; update in SPAs |
| 2.4.4 Link Purpose (In Context) | Clear link text | Descriptive links; disclose file format |
| 2.4.6 Headings and Labels | Descriptive headings | Meaningful hierarchy; no generic labels |
| 2.4.8 Location | Location indicator | Breadcrumb with prior steps as links |
| 2.4.9 Link Purpose (Link-Only) | Links meaningful alone | Pass screen reader links list test |
| 2.4.10 Section Headings | Headings for all sections | Every region has a semantic heading |
| 3.1.3 Unusual Words | Define uncommon terms | Gloss or link on first appearance |
| 3.1.4 Abbreviations | Expand abbreviations | First-use expansion + programmatic support |
| 3.1.5 Reading Level | Max Grade 9 | Plain language; sentences ≤ 25 words |
| 3.1.6 Pronunciation | Cue for ambiguous words | Phonetic note or audio on first use |
| 3.2.1 On Focus | No context change on focus | Never navigate or submit on focus |
| 3.2.2 On Input | No unexpected context change | Warn before input triggers page change |
| 3.2.3 Consistent Navigation | Same nav order and labels | Match labels and order across all pages |
| 3.2.4 Consistent Identification | Same function = same label | Identical labels for identical controls |
| 3.2.5 Change on Request | Context change only on user action | No auto-advance without explicit action |
| 3.2.6 Consistent Help | Help in consistent location | Same label and position on every page |
| 3.3.1 Error Identification | Visible, associated errors | Error text linked to field via aria; no period on validation errors |
| 3.3.2 Labels or Instructions | Visible labels + format guidance | Labels before fields; optional marked |
| 3.3.4 Error Prevention | Review step for critical data | Confirmation before legal/financial actions |
| 3.3.5 Help | Context-sensitive help | Adjacent, keyboard-accessible help |
| 3.3.6 Error Prevention (All) | Undo/cancel for all actions | Confirmation + undo for destructive actions |
| 3.3.7 Redundant Entry | Reuse mechanism for repeated data | Pre-fill or checkbox for repeated fields |
| 3.3.8 Accessible Authentication | No cognitive function test | Allow paste; offer passkey/magic link |
| 3.3.9 Accessible Authentication (No Exception) | Cognitive-free option primary | Passkey/biometrics as default method |
| 4.1.2 Name, Role, Value | Accessible names for all controls | Labels, roles, and state for every control |
| 4.1.3 Status Messages | Announced status changes | aria-live regions; specific message text |

---

## COGA alignment

| Code | Principle | Copy implication |
|------|-----------|-----------------|
| P1 | Plain words | Common words; sentences ≤ 20 words |
| P2 | Front-load purpose | Action or outcome stated first |
| P3 | Familiar patterns | Conventional button verbs; underlined links |
| P4 | Chunk and list | Multi-step instructions as bullets or numbers |
| P5 | Memory-free flow | Repeat key info inline instead of referencing earlier content |
| P6 | Supportive errors | State what happened and exactly how to fix it |
| P7 | Non-critical tone | Neutral, task-focused; no blaming "you" |
| P8 | Help and alternatives | Direct help link on every blocking step |
| P9 | Symbol + text | Every icon paired with a visible text label |
| P10 | Personalizable | No all-caps, color-only emphasis, or fixed font reliance |

---

## Related skills
- [Writing error messages](../writing-error-messages/SKILL.md)
- [Writing form labels and help text](../writing-form-labels-and-helptext/SKILL.md)
- [Reducing cognitive load](../../content-design/reducing-cognitive-load/SKILL.md)

## Reference
- [Glossary](../../reference/glossary.md)
- [Words to use](../../reference/words-to-use.md)
- [Words to avoid](../../reference/words-to-avoid.md)
