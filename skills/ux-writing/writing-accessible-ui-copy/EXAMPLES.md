# Examples: Writing Accessible UI Copy

Practical examples demonstrating accessible content patterns across common UI scenarios.

---

## Table of contents
- [Example 1: Image alt text](#example-1-image-alt-text)
- [Example 2: Button labels](#example-2-button-labels)
- [Example 3: Link text](#example-3-link-text)
- [Example 4: Form accessibility](#example-4-form-accessibility)
- [Example 5: Status announcements](#example-5-status-announcements)
- [Example 6: Data visualization](#example-6-data-visualization)
- [Example 7: Error messages](#example-7-error-messages)
- [Example 8: Navigation and location](#example-8-navigation-and-location)
- [Example 9: Modals and interruptions](#example-9-modals-and-interruptions)
- [Example 10: Authentication](#example-10-authentication)
- [Example 11: Plain language and cognitive load](#example-11-plain-language-and-cognitive-load)
- [Anti-patterns](#anti-patterns)

---

## Example 1: Image alt text

### Scenario
Product page with hero image, decorative background, product photo, and chart.

### Before (inaccessible)
```yaml
hero_image:
  alt: "hero-banner-summer-2025.jpg"
  # Problem: Filename, not description

background:
  alt: "abstract blue pattern"
  # Problem: Describes decorative image unnecessarily

product_photo:
  alt: "laptop"
  # Problem: Too vague, no context

chart:
  alt: "chart showing data"
  # Problem: Doesn't convey the information
```

### After (accessible)
```yaml
hero_image:
  type: "informative"
  alt: "Person using laptop on outdoor patio, summer collection."

background:
  type: "decorative"
  alt: ""
  aria_hidden: true

product_photo:
  type: "informative"
  alt: "ProBook 15 laptop, silver, shown open at 45-degree angle."

chart:
  type: "complex"
  alt: "Bar chart: Customer satisfaction increased 23% year over year."
  aria_describedby: "chart-description"
```

### Why it works
- Informative images describe what matters in context
- Decorative images don't distract screen reader users
- Product images identify the specific product
- Charts summarize the key insight, with data available
- Alt text ends with a period (style guide §6.1.4)
- Meets WCAG 1.1.1 Non-text Content

---

## Example 2: Button labels

### Scenario
Document editor with multiple save options and actions.

### Before (inaccessible)
```yaml
buttons:
  - label: "Save"
  - label: "Save"       # Duplicate!
  - label: "Submit"
  - label: "Click to delete"
  - label: "X"
  - label: "Proceed"    # COGA P3: unfamiliar pattern
  - label: "Go forth"   # COGA P3: unclear verb
```

### After (accessible)
```yaml
buttons:
  - label: "Save Draft"
    action: "Saves current document as draft"

  - label: "Save and Publish"
    action: "Saves and makes document public"

  - label: "Submit for Review"
    action: "Sends to approver"

  - label: "Delete Document"
    action: "Permanently removes document"
    aria_describedby: "delete-warning"

  - label: "Close Dialog"
    aria_label: "Close Dialog"

  - label: "Continue"
    # COGA P3: familiar, expected verb

  - label: "Next"
    # COGA P3: conventional navigation label
```

### Why it works
- Each button is unique and specific (WCAG 2.4.6, 4.1.2)
- Action + object pattern makes purpose clear (style guide §11.4.2)
- Title case throughout (style guide §4.1.1)
- Labels use conventional, familiar verbs (COGA P3)
- No duplicate ambiguous labels (WCAG 3.2.4)

---

## Example 3: Link text

### Scenario
Pricing page with multiple "Learn more" opportunities.

### Before (inaccessible)
```yaml
links:
  - text: "Click here"
    destination: "/pricing"

  - text: "Learn more"
    destination: "/features/analytics"

  - text: "Learn more"
    destination: "/features/reporting"

  - text: "here"
    context: "Download the PDF here"
```

### After (accessible)
```yaml
links:
  - text: "View pricing plans"
    destination: "/pricing"

  - text: "Explore analytics features"
    destination: "/features/analytics"

  - text: "See reporting capabilities"
    destination: "/features/reporting"

  - text: "Download the 2025 report (PDF, 2.4 MB)"
    destination: "/reports/2025-annual.pdf"
    # Discloses format and size — WCAG 2.4.4, 2.4.9
```

### Screen reader links list test
When a screen reader user pulls up a list of all links on the page:

**Before:**
- Click here
- Learn more
- Learn more
- here

**After:**
- View pricing plans
- Explore analytics features
- See reporting capabilities
- Download the 2025 report (PDF, 2.4 MB)

### Why it works
- Each link is meaningful without surrounding context (WCAG 2.4.9)
- No "click here" — use "select" for actions (style guide §7.1)
- File format and size disclosed for downloads (WCAG 2.4.4)
- No duplicates that confuse navigation
- Destinations are clear (WCAG 2.4.6)

---

## Example 4: Form accessibility

### Scenario
Contact form with name, email, and message fields.

### Before (inaccessible)
```html
<!-- Placeholder as label (disappears on focus) -->
<input type="text" placeholder="Your name">

<!-- Label not associated -->
<label>Email</label>
<input type="email" placeholder="Enter email">

<!-- Error not associated with field -->
<input type="text" id="phone">
<span class="error" style="color: red;">Invalid phone number</span>

<!-- Optional field not marked -->
<label for="company">Company</label>
<input type="text" id="company">
```

### After (accessible)
```yaml
form:
  fields:
    - name: "full_name"
      label:
        text: "Full name"
        for: "full_name"
      input:
        id: "full_name"
        type: "text"
        required: true
        aria_required: true

    - name: "email"
      label:
        text: "Email address"
        for: "email"
      input:
        id: "email"
        type: "email"
        required: true
        aria_describedby: "email-help"
      help_text:
        id: "email-help"
        text: "We'll send confirmation to this address."
        # Format guidance before submission — WCAG 3.3.2

    - name: "phone"
      label:
        text: "Phone number (optional)"
        for: "phone"
      input:
        id: "phone"
        type: "tel"
        aria_describedby: "phone-error"
        aria_invalid: true
      error:
        id: "phone-error"
        role: "alert"
        text: "Enter a valid phone number (e.g., 555-123-4567)"
        # No period on validation errors — style guide §4.4.2
        # States what's wrong and how to fix it — WCAG 3.3.1, COGA P6

    - name: "company"
      label:
        text: "Company (optional)"
        for: "company"
      input:
        id: "company"
        type: "text"
```

### Why it works
- Visible labels always present, not just placeholder (WCAG 3.3.2)
- Labels programmatically associated with inputs (WCAG 2.4.6)
- Help text connected via aria-describedby
- Optional fields clearly marked (WCAG 3.3.2)
- Validation errors have no trailing period (style guide §4.4.2)
- Errors identify field and suggest format (WCAG 3.3.1, COGA P6)
- Required fields indicated accessibly (WCAG 4.1.2)

---

## Example 5: Status announcements

### Scenario
E-commerce cart with add/remove actions and checkout flow.

### Before (inaccessible)
```yaml
add_to_cart:
  animation: "Item flies into cart icon"
  # No announcement for screen readers

remove_item:
  visual: "Item fades out"
  # No confirmation

checkout_error:
  display: "Red banner at top of page"
  # Color only, no programmatic announcement — WCAG 1.4.1
```

### After (accessible)
```yaml
add_to_cart:
  visual: "Item animation + cart badge update"
  announcement:
    text: "Wireless headphones added to cart. Cart total: 3 items."
    aria_live: "polite"
    # WCAG 4.1.3: specific, references the affected element

remove_item:
  visual: "Item removed from list"
  announcement:
    text: "Wireless headphones removed. Cart total: 2 items."
    aria_live: "polite"

checkout_error:
  visual: "Red banner with error icon + text label"
  # Icon + text, not color alone — WCAG 1.4.1
  announcement:
    text: "Payment didn't go through. Check your card details and try again."
    aria_live: "assertive"
    role: "alert"
    # WCAG 4.1.3: neutral tone — COGA P7

form_submission:
  visual: "Success checkmark"
  announcement:
    text: "Order confirmed. Confirmation number: 12345."
    aria_live: "polite"
    # WCAG 4.1.3: specific, references the outcome
```

### Why it works
- Status changes announced to screen readers (WCAG 4.1.3)
- Toast pattern follows `{action} + {object}` structure (style guide §11.13)
- Polite announcements for routine updates; assertive for critical errors
- Content is specific and references the affected element (WCAG 4.1.3)
- Error uses neutral, blame-free language (COGA P7)
- Color supplemented with icon and text (WCAG 1.4.1)

---

## Example 6: Data visualization

### Scenario
Dashboard with sales performance chart.

### Before (inaccessible)
```yaml
chart:
  alt: "Sales chart"
  # No data accessible to screen readers
  # Color-coded without labels — WCAG 1.4.1
```

### After (accessible)
```yaml
chart:
  alt: "Bar chart showing Q4 2025 sales by region. Northeast leads at $2.4M."
  aria_describedby: "chart-details"

  long_description:
    id: "chart-details"
    content: |
      Q4 2025 Regional Sales:
      - Northeast: $2.4 million (highest)
      - West: $1.9 million
      - Southeast: $1.7 million
      - Midwest: $1.2 million
      Total Q4 sales: $7.2 million, up 15% from Q3.

  data_table:
    caption: "Q4 2025 Sales by Region"
    available: true
    location: "Below chart, expandable"

  design:
    patterns: true
    # Not color alone — WCAG 1.4.1
    labels: "On each bar"
    # Text labels supplement color
    legend: "Pattern + color key"
```

### Why it works
- Alt text gives key insight, not just "chart"; ends with a period (WCAG 1.1.1, style guide §11.3)
- Full data available in text form (WCAG 1.1.1)
- Data table as alternative for detailed exploration
- Visual design uses patterns and labels, not color alone (WCAG 1.4.1)

---

## Example 7: Error messages

### Scenario
Checkout form with card validation errors.

### Before (inaccessible)
```yaml
errors:
  - "Error."
  - "Invalid."
  - "Try again later."
  - "Something went wrong."
  - "You entered the wrong code."   # Blaming — COGA P7
  - "Your payment was rejected."    # Blaming — COGA P7
```

### After (accessible)
```yaml
errors:
  - field: "card_number"
    text: "Enter a valid 16-digit card number"
    # No period on validation errors — style guide §4.4.2
    aria_invalid: true
    aria_describedby: "card-error"
    # States what's wrong and how to fix — WCAG 3.3.1, COGA P6

  - field: "expiry"
    text: "Expiry date must be in MM/YY format (e.g., 09/27)"
    # No period on validation errors — style guide §4.4.2

  - field: "cvv"
    text: "CVV is the 3-digit code on the back of your card"
    # No period on validation errors — style guide §4.4.2

  - type: "payment_failure"
    text: "Payment didn't go through. Try another card or contact your bank."
    # System error — period used — style guide §12.3
    role: "alert"
    aria_live: "assertive"
    help_link:
      text: "Contact support"
      href: "/support"
    # Neutral tone + help link — COGA P7, P8

  - type: "session_expired"
    text: "Your session timed out. Sign in again to continue."
    # System error — period used — style guide §12.3
    help_link:
      text: "Sign in"
      href: "/login"
    # Direct help link on blocking step — COGA P8
```

### Why it works
- Validation errors have no trailing period (style guide §4.4.2, §12.2.1)
- System errors end with a period (style guide §4.4.1)
- Each error explains what went wrong and how to fix it (WCAG 3.3.1, COGA P6)
- Errors are programmatically associated with their fields (WCAG 3.3.1)
- Tone is neutral, task-focused, not blaming (COGA P7)
- Blocking errors include direct help links (COGA P8)

---

## Example 8: Navigation and location

### Scenario
Multi-step checkout wizard and site-wide navigation.

### Before (inaccessible)
```yaml
breadcrumb:
  items: ["Home", "Shop", "Cart", "Checkout"]
  current: "Checkout"
  # No step counter, no indication of progress

page_title:
  text: "Checkout"
  # Generic, not unique enough — WCAG 2.4.2

nav:
  mobile_labels: ["Home", "Products", "About", "Help"]
  desktop_labels: ["Home", "Our Products", "About Us", "Support"]
  # Inconsistent labels — WCAG 3.2.3
```

### After (accessible)
```yaml
breadcrumb:
  aria_label: "You are here"
  items:
    - text: "Home"
      href: "/"
    - text: "Shop"
      href: "/shop"
    - text: "Cart"
      href: "/cart"
    - text: "Checkout"
      aria_current: "page"
  # Previous steps are interactive links — WCAG 2.4.8

step_indicator:
  text: "Step 3 of 4: Payment"
  aria_live: "polite"
  # Shows current + total — WCAG 2.4.8

page_title:
  text: "Checkout – Step 3: Payment | Acme Store"
  # Unique, front-loaded — WCAG 2.4.2

skip_link:
  text: "Skip to checkout form"
  href: "#checkout-form"
  # Descriptive destination — WCAG 2.4.1

nav:
  mobile_labels: ["Home", "Products", "About", "Help"]
  desktop_labels: ["Home", "Products", "About", "Help"]
  # Consistent across breakpoints — WCAG 3.2.3, 3.2.4
```

### Why it works
- Breadcrumb shows location with interactive prior steps (WCAG 2.4.8)
- Step counter includes current and total (WCAG 2.4.8)
- Page title is unique and front-loaded (WCAG 2.4.2)
- Skip link describes its destination (WCAG 2.4.1)
- Navigation labels are consistent across views (WCAG 3.2.3)

---

## Example 9: Modals and interruptions

### Scenario
Promotional modal appears mid-task; user deletes an account.

### Before (inaccessible)
```yaml
promo_modal:
  trigger: "After 30 seconds on page"
  dismiss: null
  # No way to dismiss — WCAG 2.2.4
  focus: "Not managed"

delete_action:
  button: "Delete"
  confirmation: null
  undo: null
  # No confirmation or undo — WCAG 3.3.6
```

### After (accessible)
```yaml
promo_modal:
  trigger: "After 30 seconds on page"
  dismiss:
    label: "No thanks, continue shopping"
    keyboard_accessible: true
    # Clear label, keyboard operable — WCAG 2.2.4
  snooze:
    label: "Remind me later"
    # Postpone option — WCAG 2.2.4
  focus:
    on_open: "First focusable element in modal"
    on_close: "Element that triggered modal"
    # Focus restored after dismissal — WCAG 2.2.4

delete_action:
  button:
    label: "Delete Account"
    # Title case, verb + noun — style guide §11.4.1
  confirmation_dialog:
    heading: "Delete Account?"
    # Title format: action + question mark — style guide §11.11.2
    body: "This permanently removes your account and its data. You cannot undo this action."
    confirm_label: "Delete Account"
    # Primary CTA matches title action — style guide §11.11.2
    cancel_label: "Cancel"
    # WCAG 3.3.6: confirmation before destructive action
  success_announcement:
    text: "Account deleted."
    aria_live: "polite"
```

### Why it works
- Modal can be dismissed or snoozed (WCAG 2.2.4)
- Dismiss controls are keyboard accessible and clearly labeled (WCAG 2.2.4)
- Focus is managed correctly on open and close (WCAG 2.2.4)
- Confirmation modal title uses action + question mark format (style guide §11.11.2)
- Primary CTA matches the title action (style guide §11.11.2)
- Destructive action requires confirmation (WCAG 3.3.6)

---

## Example 10: Authentication

### Scenario
Sign-in flow for a financial application.

### Before (inaccessible)
```yaml
login:
  method: "Password only"
  password_field:
    paste_blocked: true   # WCAG 3.3.8
  otp:
    instruction: "Enter the code from the email above."
    # Requires memory — WCAG 3.3.8
  alternatives: null
  # No cognitive-free option — WCAG 3.3.9
```

### After (accessible)
```yaml
login:
  primary_method:
    label: "Sign In With Passkey"
    type: "passkey"
    # Cognitive-free option is primary — WCAG 3.3.9

  alternative_methods:
    - label: "Sign In With Magic Link"
      type: "magic_link"
    - label: "Sign In With Password"
      type: "password"
      field:
        paste_allowed: true
        autofill_allowed: true
        # Paste and autofill not blocked — WCAG 3.3.8

  otp_step:
    instruction: "Enter the 6-digit code: 482910"
    # Code repeated inline, no memory required — COGA P5, WCAG 3.3.8
    help_link:
      text: "Didn't receive a code? Resend or chat with support."
      # Direct help on blocking step — COGA P8

  setup_guidance:
    text: "Set Up Passkey Sign-In"
    plain_language: true
    # Accessible setup instructions — WCAG 3.3.9
```

### Why it works
- Cognitive-free option (passkey) is the primary method (WCAG 3.3.9)
- Password field allows paste and autofill (WCAG 3.3.8)
- OTP code is repeated inline so users don't have to remember it (COGA P5)
- Help link provided on blocking step (COGA P8)
- Setup guidance is plain language (WCAG 3.3.9)

---

## Example 11: Plain language and cognitive load

### Scenario
Onboarding instructions and in-app guidance copy.

### Before (inaccessible)
```yaml
onboarding:
  step1: "Commence installation procedure prior to utilization."
  step2: "Subsequent to authentication, commence access."
  step3: "To see your results, click View."  # Purpose buried — COGA P2
  step4: "Fill out your name then your email and then click Submit."  # Wall of text — COGA P4
  error: "You entered the wrong code."  # Blaming — COGA P7
  icon_button: "🔔"  # Icon only — COGA P9
  emphasis: "IMPORTANT NOTICE"  # All caps — COGA P10
  status: "The operation was successful."  # Passive, vague
```

### After (accessible)
```yaml
onboarding:
  step1: "Start installation before you use the app."
  # Plain words, short sentence — COGA P1

  step2: "After you sign in, start."
  # Plain words — COGA P1

  step3: "Select View to see your results."
  # Action first — COGA P2; "select" not "click" — style guide §7.1

  step4:
    intro: "To create your account:"
    steps:
      - "Enter your name"
      - "Enter your email"
      - "Select Submit"
    # Chunked into steps — COGA P4; "select" not "click" — style guide §7.1

  error: "The code didn't match. Try again."
  # Neutral, task-focused — COGA P7

  icon_button:
    icon: "🔔"
    label: "🔔 Notifications"
    # Icon paired with text label — COGA P9

  emphasis: "Important notice"
  # Sentence case, not all caps — COGA P10

  status: "Settings saved."
  # Specific, active voice — WCAG 4.1.3
```

### Why it works
- Common words and short sentences (COGA P1)
- Action or outcome stated first (COGA P2)
- "Select" used instead of "click" (style guide §7.1)
- Multi-step instructions chunked into a numbered list (COGA P4)
- Errors are neutral and task-focused (COGA P7)
- Icons paired with text labels (COGA P9)
- No all-caps or color-only emphasis (COGA P10)

---

## Anti-patterns

### Don't do this

| Pattern | Problem | Fix |
|---------|---------|-----|
| `alt="image"` | Meaningless | Describe what matters |
| `alt="IMG_2847.jpg"` | Filename, not content | Write description |
| Alt text with no trailing period | Incomplete style | End alt text with a period |
| Placeholder as label | Disappears, accessibility fail | Use visible label |
| "Click here" | Meaningless out of context; wrong verb | Use "select" and describe destination |
| "Read more" x 5 | Indistinguishable | Make each unique |
| Color-only error | Invisible to colorblind | Add icon + text |
| `<div onclick>` | Not keyboard accessible | Use `<button>` |
| Heading for styling | Breaks navigation | Use CSS for styling |
| ALL CAPS | Harder to read, screen reader issues | Sentence case |
| "See image above" | Assumes visual context | Describe directly |
| "Proceed" / "Go forth" | Unfamiliar button labels | Use "Continue" / "Next" |
| "You entered the wrong code" | Blaming language | "The code didn't match. Try again." |
| Icon-only buttons | No text for cognitive or AT users | Pair icon with label |
| "Enter the amount you set earlier" | Requires memory | Repeat the value inline |
| "To see results, select View" | Purpose buried at end | "Select View to see results" |
| "Fill out name, email, then submit" | Wall of instructions | Number or bullet the steps |
| "Error." | Vague, no guidance | State the problem and the fix |
| "Click the green button" | Sensory-only instruction; wrong verb | "Select the Start button" |
| Paste blocked on password field | Forces manual transcription | Allow paste and autofill |
| No confirmation before delete | Irreversible without warning | Add confirmation dialog + undo |
| Navigation labels differ mobile/desktop | Inconsistent identification | Use identical labels everywhere |
| Period on validation error | Contradicts style guide | Remove period from validation errors |
| "enable" / "disable" | Avoided terms | Use "turn on" / "turn off" |

### Test questions
Before shipping, verify:

1. **Links list test**: Do all links make sense in a list without context?
2. **Headings test**: Does heading navigation tell the page story?
3. **Tab test**: Can you complete the task with keyboard only?
4. **Grayscale test**: Is all information still clear without color?
5. **Screen reader test**: Is the experience equivalent, not just compliant?
6. **Plain language test**: Could someone read each sentence aloud in under 5 seconds?
7. **Memory test**: Does any step require the user to remember something from earlier?
8. **Blame test**: Does any error message say "you" in an accusatory way?
9. **Icon test**: Does every icon have a visible text label alongside it?
10. **Links list test (WCAG 2.4.9)**: Would a screen reader links list be unambiguous?
11. **Verb test**: Does all copy use "select" instead of "click"?
12. **Period test**: Do validation errors omit a trailing period? Do alt texts and body text include one?
