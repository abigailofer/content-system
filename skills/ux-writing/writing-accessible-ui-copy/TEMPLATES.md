# Templates: Writing Accessible UI Copy

Structured templates for creating accessible content across common UI patterns.

---

## Table of contents
- [Alt text template](#alt-text-template)
- [Button label template](#button-label-template)
- [Link text template](#link-text-template)
- [Form field template](#form-field-template)
- [Heading structure template](#heading-structure-template)
- [Page title template](#page-title-template)
- [Status announcement template](#status-announcement-template)
- [Error message template](#error-message-template)
- [Data visualization template](#data-visualization-template)
- [Modal and interruption template](#modal-and-interruption-template)
- [Navigation and location template](#navigation-and-location-template)
- [Authentication template](#authentication-template)
- [Plain language instruction template](#plain-language-instruction-template)
- [Accessibility checklist template](#accessibility-checklist-template)

---

## Alt text template
*WCAG 1.1.1, style guide §6.1, §11.2, §11.3*

```yaml
alt_text:
  image_type: "[informative|decorative|functional|complex]"

  informative:
    content: "[What the image shows]"
    context: "[Why it matters in this context]"
    alt: "[Concise description: what + why, max 125 chars]."
    # Must end with a period — style guide §6.1.4
    # Never start with "image of" or "photo of"

  decorative:
    alt: ""
    aria_hidden: true

  functional:
    action: "[What selecting/activating does]"
    alt: "[Action verb + object]."

  complex:
    summary_alt: "[Key insight, max 125 chars]."
    # Chart/graph: describe type + key trend — style guide §11.3
    long_description: "[Full description via aria-describedby or link]"
    data_table: "[Available below or linked]"
```

### Alt text decision tree
```
Is the image purely decorative?
├── Yes → alt=""  aria-hidden="true"
└── No → Does it convey information?
    ├── Yes → Is it complex (chart/diagram)?
    │   ├── Yes → Short alt (ends with period) + aria-describedby + data table
    │   └── No → Concise descriptive alt ending with period (max 125 chars)
    └── No → Is it functional (button/link icon)?
        ├── Yes → Describe the action (not the icon appearance), end with period
        └── No → Evaluate if image is truly needed
```

---

## Button label template
*WCAG 4.1.2, 3.2.4, COGA P3, style guide §4.1.1, §11.4*

```yaml
button:
  context: "[Screen/feature context]"
  action: "[What happens when selected]"
  object: "[What is being acted upon]"

  label:
    case: "Title Case"              # Always title case — style guide §4.1.1
    pattern: "[Verb] + [Object]"    # Except: Save, Done, Apply — style guide §11.4.1
    familiar_verbs:
      - "Save"      # Not "Preserve"
      - "Delete"    # Not "Eradicate"
      - "Continue"  # Not "Proceed"
      - "Submit"    # Not "Go forth"
      - "Next"      # Not "Step 2"
      - "Confirm"   # Not "✔" (icon only)
      - "Cancel"
      - "Edit"
      - "Add"
      - "Remove"
    examples:
      - "Save Draft"
      - "Delete Account"
      - "Add to Cart"
      - "Reset Password"
      - "Create Report"

  constraints:
    max_chars: 25
    starts_with_verb: true
    unique_on_page: true
    consistent_across_pages: true   # WCAG 3.2.4
    no_period: true                 # Buttons never end with period — style guide §4.4.2
    no_exclamation: true            # style guide §1.7.5

  accessibility:
    aria_label: "[Only if visible text is insufficient]"
    aria_describedby: "[ID of element with additional context]"
```

---

## Link text template
*WCAG 2.4.4, 2.4.9, style guide §4.3*

```yaml
link:
  destination: "[Where the link goes]"
  context: "[Surrounding content]"

  label:
    pattern: "[Descriptive of destination or action]"
    good:
      - "View pricing plans"
      - "Read the accessibility guide"
      - "Download the 2025 report (PDF, 2.4 MB)"
      - "Open support chat"
    avoid:
      - "Select here"       # style guide §4.3.3
      - "Click here"        # style guide §4.3.3
      - "Learn more"
      - "Read more"
      - "Here"

  constraints:
    meaningful_alone: true            # WCAG 2.4.9
    underlined: true                  # style guide §4.3.2
    indicates_format: "[If non-HTML: PDF, DOC, XLS]"
    indicates_size: "[If download]"
    indicates_behavior: "[If opens new window or external site]"
    unique_on_page: true              # WCAG 2.4.9
    consistent_across_pages: true     # WCAG 3.2.4
    no_url_as_text: true              # style guide §4.3.4
    no_period_after_link: true        # style guide §4.4.2

  accessibility:
    aria_label: "[Full description if visible text cannot be made descriptive]"
```

---

## Form field template
*WCAG 3.3.1, 3.3.2, 3.3.5, 3.3.7, style guide §11.7*

```yaml
form_field:
  field_name: "[Internal identifier]"
  field_type: "[text|email|password|select|checkbox|radio|textarea|tel]"

  label:
    text: "[Visible label text]"          # Sentence case — style guide §4.1.2
    position: "above"                      # Above preferred — WCAG 3.3.2
    required_indicator: "(required)"
    optional_indicator: "(optional)"       # Mark optional explicitly — WCAG 3.3.2, style guide §11.7.4

  help_text:
    text: "[Format requirement or guidance]."  # Ends with period — style guide §4.4.1
    position: "below_label_above_input"         # Before submission — WCAG 3.3.2
    association: "aria-describedby"             # style guide §10.3

  placeholder:
    text: "[Example value only, e.g. name@example.com]"
    # Never the only label — WCAG 3.3.2, style guide §11.7.5
    # Do not repeat label — style guide §11.7.5
    # If example is in placeholder, remove it from help text or body copy — avoid duplication

  error:
    text: "[What's wrong]. [How to fix it]"   # WCAG 3.3.1, COGA P6
    # No trailing period on validation errors — style guide §4.4.2
    tone: "neutral"                            # COGA P7: not blaming
    association: "aria-describedby"            # style guide §10.3
    aria_invalid: true

  reuse:
    mechanism: "[Checkbox or pre-fill if field repeated]"  # WCAG 3.3.7
    label: "[Same as shipping address / Use saved card]"
    keyboard_accessible: true

  context_help:
    trigger_label: "Help"              # Consistent label — WCAG 3.3.5
    content: "[Adjacent, accessible]"
    keyboard_accessible: true

  constraints:
    label_always_visible: true
    help_before_submission: true
    error_near_field: true
    paste_allowed: true                # For password/code fields — WCAG 3.3.8
    autofill_allowed: true
```

---

## Heading structure template
*WCAG 2.4.6, 2.4.10, style guide §4.1, §11.9*

```yaml
page_headings:
  h1:
    text: "[Page title]"
    case: "Title Case"      # style guide §4.1.1
    one_per_page: true
    # Update h1 dynamically in SPAs — WCAG 2.4.10

  h2_h4:
    case: "Sentence case"   # style guide §4.1.2
    descriptive: true
    no_period: true         # style guide §4.4.2

  sections:
    - level: "h2"
      text: "[Major section — specific, not 'Section 1']"
      subsections:
        - level: "h3"
          text: "[Subsection name]"

  rules:
    one_h1_per_page: true
    no_skipping_levels: true          # h1 → h2 → h3, never h1 → h3
    every_section_has_heading: true   # WCAG 2.4.10
    headings_not_for_styling: true

  validation:
    - "Does h1 describe the page purpose in title case?"
    - "Do h2–h4 use sentence case?"
    - "Could someone navigate by headings alone?"
    - "Are heading levels sequential with no gaps?"
    - "Is h1 updated on route change in SPAs?"
```

---

## Page title template
*WCAG 2.4.2*

```yaml
page_title:
  pattern: "[Page-specific info] – [Section] | [Site name]"

  examples:
    static_page: "Checkout – Step 3: Payment | Acme Store"
    error_page: "Page not found | Acme Store"
    search_results: "Results for 'headphones' | Acme Store"
    settings: "Account Settings | Acme Store"

  rules:
    unique_per_page: true
    front_loaded: true          # Page-specific part comes first
    concise: true               # Fits a browser tab
    dynamic_in_spa: true        # Updated on route/modal change

  spa_pattern:
    on_route_change: "Update <title> and <h1> to match current view"
    announcement: "New page title announced via aria-live or focus"
```

---

## Status announcement template
*WCAG 4.1.3, COGA P7, style guide §11.13*

```yaml
status_announcement:
  trigger: "[What caused this status]"

  message:
    text: "[What happened or changed — specific, references the element]"
    tone: "neutral"         # COGA P7: not blaming
    max_chars: 80

  aria_live:
    region: "[polite|assertive]"
    # polite: routine updates; assertive: critical errors only

  toast_patterns:
    success:
      pattern: "{Action} + {object} + {quantity or name}"   # style guide §11.13.2
      aria_live: "polite"
      examples:
        - "Labels added to 3 tests."
        - "Labels added to Test 2."

    failure:
      pattern: "Failed to {action} {object}"               # style guide §11.13.3
      aria_live: "assertive"
      examples:
        - "Failed to add labels."
        - "Failed to save changes."

    avoid:
      - "Success!"
      - "Operation completed successfully"
      - "Error occurred"

  general_patterns:
    success:
      aria_live: "polite"
      example: "Settings saved."

    error:
      aria_live: "assertive"
      role: "alert"
      references_element: true   # WCAG 4.1.3
      example: "Payment didn't go through. Try another card."

    progress:
      aria_live: "polite"
      example: "Uploading: 50% complete."

  constraints:
    specific: true
    references_affected_element: true   # WCAG 4.1.3
    no_exclamation: true                # style guide §1.7.5
    announced_to_at: true               # WCAG 4.1.3
```

---

## Error message template
*WCAG 3.3.1, COGA P6, P7, P8, style guide §12*

```yaml
accessible_error:
  field: "[Associated form field]"

  validation_error:
    what_wrong: "[Specific problem]"         # WCAG 3.3.1
    how_fix: "[Clear, actionable step]"      # COGA P6
    tone: "neutral"                          # COGA P7: no "you" blame
    pattern: "[What's wrong] [How to fix]"   # style guide §12.2.2
    no_period: true                          # style guide §4.4.2
    max_chars: 80                            # style guide §2.1

  system_error:
    pattern: "[Problem statement]. [Recovery action]."  # style guide §12.3.4
    ends_with_period: true                              # style guide §4.4.1
    no_technical_codes: true                            # style guide §12.3.3
    no_word_failure: true                               # style guide §12.3.3

  help:
    link_text: "[Contact support / Resend code]"   # COGA P8
    href: "[/support or /contact]"
    include_on: "blocking_errors"

  accessibility:
    aria_invalid: true
    aria_describedby: "[error-message-id]"
    role: "alert"                            # For critical or page-level errors

  examples:
    validation_required:
      bad:  "Field required."
      good: "Enter your email address"       # No period — style guide §4.4.2

    validation_format:
      bad:  "Invalid."
      good: "Enter a valid email address (e.g., name@company.com)"

    validation_constraint:
      bad:  "Password error."
      good: "Password must be 8 or more characters"

    system_payment:
      bad:  "Your payment was rejected."     # Blaming — COGA P7
      good: "Payment didn't go through. Try another card or contact your bank."

    system_session:
      bad:  "Error. Try again later."
      good: "Your session timed out. Sign in again to continue."
      help: "Need help? Contact support."    # COGA P8
```

---

## Data visualization template
*WCAG 1.1.1, 1.4.1, style guide §11.3*

```yaml
data_visualization:
  type: "[chart|graph|diagram|infographic]"

  accessibility:
    alt_text:
      describe_type: true           # e.g. "Bar chart", "Pie chart" — style guide §11.3
      summary: "[Type + key trend, max 125 chars]."
      # Ends with period — style guide §6.1.4
      example: "Bar chart: revenue grew 25% from Q1 to Q4 2025."

    long_description:
      method: "[aria-describedby|details element|linked page]"
      content: |
        [Full description including:]
        - Chart type and what it represents
        - Key data points
        - Trends or patterns
        - Source and date

    data_table:
      provide: true
      location: "[below chart|linked|expandable]"

  design_requirements:
    not_color_alone: true          # WCAG 1.4.1: use patterns + labels
    patterns_on_segments: true
    text_labels_on_bars: true
    sufficient_contrast: true
    legend: "Pattern + color + text key"
```

---

## Modal and interruption template
*WCAG 2.2.4, 3.3.6, style guide §11.11*

```yaml
modal:
  trigger: "[What causes modal to appear]"
  type: "[promotional|confirmation|destructive|abort|informational]"

  heading:
    destructive_pattern: "[Action Name]?"    # Action + question mark — style guide §11.11.2
    case: "Title Case"                       # style guide §4.1.1
    no_period: true                          # style guide §4.4.2
    example: "Delete Account?"

  body:
    text: "[Consequence or context]."        # Ends with period — style guide §4.4.1
    optional: true                           # Include when consequences not obvious

  cta:
    primary:
      pattern: "[Action Name]"               # Matches heading action — style guide §11.11.2
      case: "Title Case"
      example: "Delete Account"
    secondary:
      label: "Cancel"                        # style guide §11.11.1
      # Use "Quit" when all progress lost; "Stop" when progress saved

  dismiss:
    label: "[No thanks, continue / Cancel]"  # Specific label — WCAG 2.2.4
    keyboard_accessible: true

  snooze:
    label: "Remind me later"
    # Optional postpone path — WCAG 2.2.4

  focus:
    on_open: "first focusable element in modal"   # style guide §11.11.7
    on_close: "element that triggered the modal"
    # WCAG 2.2.4

  aria:
    labelledby: "modal-heading"              # style guide §11.11.7
    describedby: "modal-body"               # When body text present

  destructive_examples:
    - heading: "Delete Draft?"
      body: "You cannot undo this action."
      primary: "Delete Draft"
      secondary: "Cancel"

    - heading: "Return to the First Screen?"
      body: "You'll lose any changes saved to this session."
      primary: "Return to First Screen"
      secondary: "Cancel"
```

---

## Navigation and location template
*WCAG 2.4.1, 2.4.2, 2.4.8, 3.2.3, 3.2.6*

```yaml
navigation:
  skip_link:
    text: "Skip to [destination name]"   # Descriptive — WCAG 2.4.1
    href: "#[region-id]"
    position: "first focusable element"
    visible_on_focus: true

  breadcrumb:
    aria_label: "You are here"
    items:
      - text: "[Page name]"
        href: "[/path]"              # Prior steps are links — WCAG 2.4.8
      - text: "[Current page]"
        aria_current: "page"
        # Current step is not a link

  step_indicator:
    text: "Step [n] of [m]: [Step name]"  # Both counts — WCAG 2.4.8
    aria_live: "polite"

  labels:
    consistent_across_pages: true    # WCAG 3.2.3
    consistent_across_breakpoints: true
    desktop: ["Home", "Products", "About", "Help"]
    mobile:  ["Home", "Products", "About", "Help"]
    # Identical — WCAG 3.2.3

  help:
    label: "Help"                    # Same label everywhere — WCAG 3.2.6
    position: "[top-right|footer]"
    consistent_across_pages: true
    keyboard_accessible: true
```

---

## Authentication template
*WCAG 3.3.8, 3.3.9, COGA P5, P8*

```yaml
authentication:
  primary_method:
    label: "Sign In With Passkey"
    type: "passkey"
    position: "first / most prominent"  # WCAG 3.3.9

  alternatives:
    - label: "Sign In With Magic Link"
      prominence: "equal"               # WCAG 3.3.9
    - label: "Sign In With Password"
      prominence: "equal"

  password_field:
    paste_allowed: true                 # WCAG 3.3.8
    autofill_allowed: true

  otp_step:
    instruction: "Enter the 6-digit code: [code]"  # Code inline — COGA P5
    # Not: "Enter the code from the email above"
    help:
      text: "Didn't receive a code? Resend or chat with support."
      link_text: "Chat with support"    # COGA P8

  setup_guidance:
    plain_language: true                # WCAG 3.3.9
    keyboard_accessible: true
```

---

## Plain language instruction template
*WCAG 3.1.5, COGA P1, P2, P4, P5, P9, P10, style guide §1, §2, §7*

```yaml
instruction:
  sentence_length: "≤ 20 words"              # COGA P1, style guide §2.2 (max 30)
  reading_level: "Grade 8 or below"          # WCAG 3.1.5

  verb_choice:
    use: "select"                            # style guide §7.1
    avoid: "click"
    use: "turn on / turn off"
    avoid: "enable / disable"

  structure:
    front_load: true                         # Action first — COGA P2, style guide §1.6
    good: "Select View to see your results."
    bad:  "To see your results, select View."

  multi_step:
    format: "numbered_list or bullets"       # COGA P4
    good:
      - "Enter your name"
      - "Enter your email"
      - "Select Submit"
    bad: "Enter your name, then your email, then select Submit."

  memory_free:
    repeat_inline: true                      # COGA P5
    good: "Track your order with number 49327."
    bad:  "Use the number above to track your order."

  icons:
    always_paired_with_label: true           # COGA P9
    good: "🔔 Notifications"
    bad:  "🔔"

  emphasis:
    no_all_caps: true                        # COGA P10
    no_color_only: true
    no_exclamation: true                     # style guide §1.7.5
    no_filler_words: true                    # style guide §1.7.1
    good: "Important notice"
    bad:  "IMPORTANT NOTICE"

  abbreviations:
    expand_first_use: true                   # WCAG 3.1.4
    good: "Web Content Accessibility Guidelines (WCAG)"
    bad:  "WCAG requirements"

---

## Accessibility checklist template

```yaml
accessibility_review:
  component: "[Component being reviewed]"

  checklist:
    perceivable:
      - alt_text_complete_with_period: "[yes|no|na]"   # style guide §6.1.4
      - captions_or_transcripts: "[yes|no|na]"
      - not_color_alone: "[yes|no]"
      - sensory_instructions_avoided: "[yes|no]"        # WCAG 1.3.3

    understandable:
      - plain_language: "[yes|no]"
      - sentences_under_25_words: "[yes|no]"
      - action_front_loaded: "[yes|no]"                 # COGA P2
      - steps_chunked: "[yes|no|na]"                    # COGA P4
      - info_repeated_inline: "[yes|no|na]"             # COGA P5
      - select_not_click: "[yes|no]"                    # style guide §7.1
      - turn_on_off_not_enable_disable: "[yes|no|na]"   # style guide §7.1
      - consistent_terms: "[yes|no]"
      - abbreviations_expanded: "[yes|no|na]"
      - no_exclamation_points: "[yes|no]"               # style guide §1.7.5

    operable:
      - keyboard_accessible: "[yes|no]"
      - focus_visible: "[yes|no]"
      - focus_managed_on_modals: "[yes|no|na]"
      - modals_dismissible: "[yes|no|na]"               # WCAG 2.2.4
      - skip_link_present: "[yes|no]"
      - page_title_unique: "[yes|no]"                   # WCAG 2.4.2

    robust:
      - valid_markup: "[yes|no]"
      - aria_correct: "[yes|no]"
      - status_announced: "[yes|no|na]"                 # WCAG 4.1.3
      - toast_pattern_followed: "[yes|no|na]"           # style guide §11.13
      - errors_associated: "[yes|no|na]"                # WCAG 3.3.1
      - tested_with_at: "[screen reader used]"

    style_guide:
      - buttons_title_case: "[yes|no]"                  # style guide §4.1.1
      - h1_title_case: "[yes|no]"                       # style guide §4.1.1
      - h2_h4_sentence_case: "[yes|no]"                 # style guide §4.1.2
      - validation_errors_no_period: "[yes|no|na]"      # style guide §4.4.2
      - alt_text_ends_with_period: "[yes|no|na]"        # style guide §6.1.4
      - body_text_ends_with_period: "[yes|no|na]"       # style guide §4.4.1

    cognitive:
      - errors_supportive: "[yes|no|na]"                # COGA P6
      - tone_non_critical: "[yes|no]"                   # COGA P7
      - help_on_blocking_steps: "[yes|no|na]"           # COGA P8
      - icons_labeled: "[yes|no]"                       # COGA P9
      - no_all_caps_or_color_only: "[yes|no]"           # COGA P10
      - confirmation_before_destructive: "[yes|no|na]"  # WCAG 3.3.6
      - paste_allowed_on_auth_fields: "[yes|no|na]"     # WCAG 3.3.8

  notes: "[Additional observations]"
```
