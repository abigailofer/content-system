# Rubric: Writing Accessible UI Copy

Evaluation criteria for accessible content across four proficiency levels.

---

## Table of contents
- [Scoring guide](#scoring-guide)
- [Dimension 1: Alt text quality](#dimension-1-alt-text-quality)
- [Dimension 2: Interactive element labels](#dimension-2-interactive-element-labels)
- [Dimension 3: Content structure](#dimension-3-content-structure)
- [Dimension 4: Language clarity](#dimension-4-language-clarity)
- [Dimension 5: Assistive technology support](#dimension-5-assistive-technology-support)
- [Dimension 6: Cognitive accessibility](#dimension-6-cognitive-accessibility)
- [Dimension 7: Error handling and recovery](#dimension-7-error-handling-and-recovery)
- [Dimension 8: Navigation and location](#dimension-8-navigation-and-location)
- [Scoring thresholds](#scoring-thresholds)
- [Quick-fail criteria](#quick-fail-criteria)
- [Scoring worksheet](#scoring-worksheet)

---

## Scoring guide

| Score | Level | Description |
|-------|-------|-------------|
| 4 | Expert | Exceeds WCAG AA; exemplary inclusive design |
| 3 | Proficient | Meets WCAG AA; consistently accessible |
| 2 | Developing | Partial compliance; some barriers remain |
| 1 | Novice | Significant barriers; fails basic requirements |

---

## Dimension 1: Alt text quality
*WCAG 1.1.1, style guide §6.1, §11.2, §11.3*

### Level 4 — Expert
- All images have appropriate alt text (informative, decorative, or functional)
- Complex images have extended descriptions via aria-describedby or linked page
- Alt text is concise yet complete (under 125 chars for simple images)
- Alt text ends with a period (style guide §6.1.4)
- Context-appropriate: same image may have different alt in different contexts
- No redundant "image of" or "photo of" prefixes
- Time-based media (video, audio) has captions or transcripts
- Charts and graphs describe type, key trends, and insight (style guide §11.3)

### Level 3 — Proficient
- Informative images have descriptive alt text ending with a period
- Decorative images have empty alt (alt="")
- Alt text describes what matters, not just what's visible
- Length is appropriate for image complexity

### Level 2 — Developing
- Alt text present but may be too brief, too verbose, or missing period
- Some decorative images incorrectly labeled
- May include "image of" prefixes
- Complex images lack extended descriptions

### Level 1 — Novice
- Alt text missing or uses filename
- Decorative images have meaningless alt
- Over-describes or under-describes consistently
- No awareness of context-dependent descriptions or period requirement

---

## Dimension 2: Interactive element labels
*WCAG 2.4.4, 2.4.6, 2.4.9, 3.2.4, 4.1.2, COGA P3, style guide §11.4, §11.7*

### Level 4 — Expert
- All buttons use title case with verb + noun pattern (style guide §4.1.1, §11.4.1)
- Buttons use familiar, conventional verbs (COGA P3)
- "Select" used instead of "click" throughout (style guide §7.1)
- Links are meaningful out of context; tested in screen reader links list (WCAG 2.4.9)
- Download links disclose file type, size, and/or new-window behavior (WCAG 2.4.4)
- Form labels are visible, associated, and unambiguous
- Optional fields explicitly marked "(optional)" (WCAG 3.3.2, style guide §11.7.4)
- No duplicate labels where differentiation matters
- Icon-only controls have a descriptive accessible name (WCAG 4.1.2)
- Identical controls use consistent labels across all pages and views (WCAG 3.2.4)

### Level 3 — Proficient
- Buttons have action verbs + objects in title case
- Links avoid "click here" and "learn more" patterns; use "select" not "click"
- Form fields have visible labels (not placeholder-only)
- Error messages are associated with their fields
- Navigation labels are consistent across responsive breakpoints (WCAG 3.2.3)

### Level 2 — Developing
- Some generic labels ("Submit", "Continue") without context
- "click" used instead of "select"
- Links sometimes rely on surrounding text for meaning
- Labels present but occasionally ambiguous
- Navigation labels differ between mobile and desktop views

### Level 1 — Novice
- Generic labels throughout ("Select here", "Submit")
- Links meaningless out of context
- Placeholder text used as primary label
- No awareness of label + action relationship

---

## Dimension 3: Content structure
*WCAG 2.4.1, 2.4.2, 2.4.6, 2.4.8, 2.4.10, style guide §11.9*

### Level 4 — Expert
- H1 uses title case; H2–H4 use sentence case (style guide §4.1.1, §4.1.2)
- Heading hierarchy is logical and complete (h1 → h2 → h3)
- Single h1 per page describes page purpose
- Headings alone tell the page story (navigable by heading)
- Lists used for related items (not forced into paragraphs)
- Landmarks properly applied (nav, main, aside, etc.)
- Skip link present, keyboard accessible, and describes its destination (WCAG 2.4.1)
- Page titles are unique, descriptive, and front-loaded (WCAG 2.4.2)
- SPAs update page title and h1 on route changes (WCAG 2.4.2, 2.4.10)
- Breadcrumbs or step indicators show location with current + total counts (WCAG 2.4.8)
- Every distinct content section begins with a semantic heading (WCAG 2.4.10)

### Level 3 — Proficient
- No skipped heading levels
- Headings are descriptive (not "Section 1")
- Major content sections have headings
- One h1 per page in title case
- Page titles distinguish pages from one another
- Skip link exists even if not always visible

### Level 2 — Developing
- Heading levels occasionally skipped
- Some headings used for styling, not structure
- Inconsistent capitalization on headings
- Page titles generic or not updated in SPAs

### Level 1 — Novice
- Headings used for visual styling only
- No logical hierarchy; missing h1
- Content structure invisible to assistive tech
- No skip links; no page titles

---

## Dimension 4: Language clarity
*WCAG 3.1.3, 3.1.4, 3.1.5, 3.1.6, COGA P1, P2, P4, P5, P9, P10, style guide §1, §2, §7*

### Level 4 — Expert
- Reading level does not exceed Grade 9 (WCAG 3.1.5); aim for Grade 8 or below
- Sentences do not exceed 25 words (WCAG 3.1.5, COGA P1, style guide §2.2)
- Action or outcome stated first in instructions (COGA P2, style guide §1.6)
- Multi-step instructions chunked into numbered lists or bullets (COGA P4)
- Repeated information shown inline rather than referencing earlier content (COGA P5)
- Icons always paired with visible text labels (COGA P9)
- No all-caps, color-only emphasis, or fixed font-size reliance (COGA P10)
- No exclamation points (style guide §1.7.5)
- No filler words ("quickly", "simply") (style guide §1.7.1)
- No pleasantries ("please", "sorry") unless softening high-friction copy (style guide §1.7.2)
- "Select" used instead of "click"; "turn on/off" instead of "enable/disable" (style guide §7.1)
- Uncommon terms defined at first appearance (WCAG 3.1.3)
- Abbreviations expanded on first use with programmatic support (WCAG 3.1.4)
- Words requiring specific pronunciation provide a cue (WCAG 3.1.6)
- Consistent terminology throughout; no synonym confusion

### Level 3 — Proficient
- Plain language used for most content
- Jargon avoided or explained
- Instructions are task-focused and front-loaded
- Abbreviations expanded on first use
- Steps broken into lists where appropriate
- Preferred word choices followed (style guide §7.1)

### Level 2 — Developing
- Some unnecessary complexity or jargon without explanation
- "click" used instead of "select"
- Instructions sometimes buried after the action
- Multi-step instructions written as prose

### Level 1 — Novice
- Dense, complex language throughout
- Heavy jargon without explanation
- Relies on visual/spatial references
- Long, unbroken instruction paragraphs
- Exclamation points present

---

## Dimension 5: Assistive technology support
*WCAG 1.3.3, 1.4.1, 2.2.1, 2.2.3, 2.2.4, 3.2.1, 3.2.2, 3.2.5, 4.1.2, 4.1.3, style guide §10*

### Level 4 — Expert
- Status changes announced with specific, descriptive messages (WCAG 4.1.3)
- Status messages reference the affected element (WCAG 4.1.3)
- Toast success pattern: `{action} + {object}` (style guide §11.13.2)
- Toast failure pattern: `Failed to {action} {object}` (style guide §11.13.3)
- Dynamic content updates communicated to screen readers via aria-live (style guide §10.4)
- Focus managed on modals: traps focus on open, restores on close (WCAG 2.2.4, style guide §11.11.7)
- No information conveyed by color alone; supplemented with text or icon (WCAG 1.4.1)
- Instructions do not rely on sensory characteristics (WCAG 1.3.3)
- Non-emergency interruptions can be dismissed or postponed (WCAG 2.2.4)
- Time-limited tasks provide visible, announced timer and option to extend (WCAG 2.2.1)
- Keyboard focus does not trigger context changes (WCAG 3.2.1)
- User input does not unexpectedly change context (WCAG 3.2.2)
- Context changes occur only on explicit user request (WCAG 3.2.5)
- Tested with actual assistive technology

### Level 3 — Proficient
- Important status changes have polite or assertive announcements
- Toast patterns followed for success and failure
- Form errors are announced and associated with their fields
- Color is supplemented with text or icons
- Focus order is logical
- Interruptions have a visible dismiss control
- ARIA roles and states applied correctly (WCAG 4.1.2)

### Level 2 — Developing
- Some status changes not announced
- Toast patterns inconsistent
- Errors may not be programmatically associated
- Color sometimes only differentiator
- Focus not always managed on modal open/close

### Level 1 — Novice
- No consideration for screen reader announcements
- Errors not associated with fields
- Color-only differentiation common
- No assistive technology testing
- Interruptions cannot be dismissed

---

## Dimension 6: Cognitive accessibility
*COGA P6, P7, P8, WCAG 3.3.4, 3.3.6, 3.3.7, 3.3.8, 3.3.9, style guide §12*

### Level 4 — Expert
- Error messages state what happened and give a clear fix (COGA P6, style guide §12.1)
- Tone is neutral and task-focused; no blaming language (COGA P7, style guide §12.1)
- Blocking steps include a direct help link or phone number (COGA P8)
- Destructive or critical actions require confirmation before committing (WCAG 3.3.4, 3.3.6)
- Confirmation modal uses action + question mark title format (style guide §11.11.2)
- Undo or cancel option available for high-impact changes (WCAG 3.3.6)
- Repeated information pre-filled or offered via reuse mechanism (WCAG 3.3.7)
- Authentication can be completed without memory or transcription tasks (WCAG 3.3.8, 3.3.9)
- Cognitive-free sign-in method is the primary/default option (WCAG 3.3.9)
- Password fields allow paste and autofill (WCAG 3.3.8)

### Level 3 — Proficient
- Errors explain the issue and suggest a fix
- Tone avoids accusatory "you" constructions
- Confirmation dialogs present before irreversible actions
- Help available on complex or blocking steps
- Password paste not blocked

### Level 2 — Developing
- Some errors are vague or use blaming language
- Confirmation steps missing for some destructive actions
- Help difficult to find on blocking steps
- Repeated data must be re-entered without a reuse option

### Level 1 — Novice
- Errors are generic ("Error", "Invalid") or accusatory
- No confirmation before destructive actions
- No help links on blocking steps
- Authentication relies entirely on memory and transcription

---

## Dimension 7: Error handling and recovery
*WCAG 3.3.1, 3.3.2, 3.3.5, COGA P6, P7, P8, style guide §12.2, §12.3*

### Level 4 — Expert
- All validation errors visible, associated with input, and have no trailing period (WCAG 3.3.1, style guide §4.4.2)
- System errors end with a period (style guide §4.4.1)
- Error text is programmatically associated with its input (WCAG 3.3.1)
- Format requirements and help text appear before submission (WCAG 3.3.2)
- Optional fields are explicitly marked "(optional)" (WCAG 3.3.2)
- Complex inputs provide adjacent, keyboard-accessible context-sensitive help (WCAG 3.3.5)
- Help triggers use consistent labels across all pages (WCAG 3.3.5)
- Success messages include a reversal path where appropriate (WCAG 3.3.6)
- Errors use neutral language and focus on the fix (COGA P6, P7)
- Validation errors follow approved patterns (style guide §12.2.2)
- System errors follow problem + recovery structure (style guide §12.3.4)

### Level 3 — Proficient
- Errors visible and associated with fields
- Validation errors have no trailing period; system errors end with a period
- Format guidance present before submission
- Optional fields marked
- Errors explain what went wrong

### Level 2 — Developing
- Some errors missing association to fields
- Period rules inconsistently applied
- Format guidance may appear only after error
- Optional/required indication inconsistent

### Level 1 — Novice
- Errors missing or generic
- No association with input fields
- Period rules ignored
- No format guidance

---

## Dimension 8: Navigation and location
*WCAG 2.4.1, 2.4.2, 2.4.8, 3.2.3, 3.2.4, 3.2.6*

### Level 4 — Expert
- Skip link present, visible on focus, and describes destination (WCAG 2.4.1)
- Page titles are unique, descriptive, and front-load the page-specific part (WCAG 2.4.2)
- SPAs update title and h1 dynamically on route change (WCAG 2.4.2)
- Breadcrumb or step indicator shows location; prior steps are links (WCAG 2.4.8)
- Step counters show current and total (e.g. "Step 2 of 4") (WCAG 2.4.8)
- Navigation order and labels consistent across all pages (WCAG 3.2.3)
- Navigation consistent across responsive breakpoints (WCAG 3.2.3)
- Identical controls use the same visible label everywhere (WCAG 3.2.4)
- Help mechanisms appear in consistent location with identical labels (WCAG 3.2.6)

### Level 3 — Proficient
- Skip link present
- Page titles distinguish pages
- Breadcrumb or step counter present
- Navigation labels mostly consistent

### Level 2 — Developing
- Skip link missing or non-functional
- Page titles generic or duplicated
- No step counter or location indicator
- Navigation labels differ across views

### Level 1 — Novice
- No skip links
- Identical or missing page titles
- No location indicators
- Navigation inconsistent across pages and breakpoints

---

## Scoring thresholds

| Total score | Rating | Recommendation |
|-------------|--------|----------------|
| 29–32 | Exemplary | Ship with confidence |
| 22–28 | Passing | Minor refinements recommended |
| 15–21 | Needs work | Address gaps before shipping |
| 8–14 | Failing | Major revision required |

---

## Quick-fail criteria

Any of these result in automatic failure regardless of other scores:

| Criterion | Standard |
|-----------|----------|
| Missing alt text on informative images | WCAG 1.1.1 |
| Alt text missing trailing period | Style guide §6.1.4 |
| No visible form labels | WCAG 1.3.1, 3.3.2 |
| "Select here" or "Learn more" as sole link text | WCAG 2.4.4 |
| Information conveyed by color alone | WCAG 1.4.1 |
| No programmatic heading structure | WCAG 1.3.1 |
| Errors with no explanation or fix | WCAG 3.3.1, COGA P6 |
| Period on validation errors | Style guide §4.4.2 |
| Paste blocked on password or code fields | WCAG 3.3.8 |
| Destructive action with no confirmation | WCAG 3.3.6 |
| Non-emergency modal cannot be dismissed | WCAG 2.2.4 |
| Exclamation points in UI copy | Style guide §1.7.5 |

---

## Scoring worksheet

```yaml
evaluation:
  component: "[Name]"
  evaluator: "[Name]"
  date: "[Date]"

  scores:
    alt_text_quality:           [1-4]
    interactive_labels:         [1-4]
    content_structure:          [1-4]
    language_clarity:           [1-4]
    assistive_tech_support:     [1-4]
    cognitive_accessibility:    [1-4]
    error_handling_recovery:    [1-4]
    navigation_location:        [1-4]

  total: "[Sum / 32]"
  quick_fail: "[yes|no]"
  quick_fail_reason: "[If applicable]"

  recommendation: "[Ship|Refine|Revise|Reject]"
  priority_fixes: |
    1. [Most critical issue]
    2. [Second priority]
    3. [Third priority]
```
