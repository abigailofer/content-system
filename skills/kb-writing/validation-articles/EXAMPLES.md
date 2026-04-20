# Examples: Validation Articles

---

## How to read these examples

Each example shows a complete validation article output. The input block lists the variables passed to the skill. The output block is the finished article.

Examples cover two entry types:
- **Example 1** — a WCAG success criterion entry (all sections, including Related WCAG Techniques)
- **Example 2** — a best-practice entry (Related WCAG Techniques section omitted; "should" in rule; adjusted FAQ)

---

## Example 1: WCAG success criterion entry

**Input:**
- `validation_name`: `placeholder-as-label`
- `wcag_sc`: `1.3.1 Info and Relationships`
- `severity`: `critical`
- `wcag_techniques_url`: `https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships`

**Output:**

---

## placeholder-as-label

**Placeholder text must not be used as a substitute for a label.**

Input fields need a visible, persistent label so users always know what information to enter. Placeholder text disappears once a user starts typing, which means the field's purpose is no longer communicated to the user or to assistive technology.

When a field relies on placeholder text alone, users who return to the field after entering data have no way to confirm what the field asked for. People with cognitive disabilities are especially affected by this.

### Pass Patterns

An input has a visible `<label>` element associated using a matching `for` and `id` attribute pair.

```html
<label for="email">Email address</label>
<input type="email" id="email" placeholder="name@example.com">
```

An input uses `aria-labelledby` to associate a separate element as its accessible name.

```html
<p id="email-label">Email address</p>
<input type="email" aria-labelledby="email-label" placeholder="name@example.com">
```

### Fail Patterns

An input relies entirely on placeholder text with no `<label>` element.

```html
<input type="email" placeholder="Email address">
```

CSS hides the `<label>` element from the accessibility tree, leaving the input without an accessible name.

```html
<label for="email" style="display: none;">Email address</label>
<input type="email" id="email" placeholder="Email address">
```

### Related WCAG Techniques

#### Sufficient techniques

[H44: Using label elements to associate text labels with form controls](https://www.w3.org/WAI/WCAG21/Techniques/html/H44)

[ARIA14: Using aria-label to provide an invisible label where a visible label cannot be used](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA14)

[ARIA16: Using aria-labelledby to provide a name for user interface controls](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA16)

#### Advisory techniques

[G167: Using an adjacent button to label the purpose of a field](https://www.w3.org/WAI/WCAG21/Techniques/general/G167)

#### Failure techniques

[F68: Failure of Success Criterion 1.3.1 and 4.1.2 due to the association of label and user interface controls not being programmatically determinable](https://www.w3.org/WAI/WCAG21/Techniques/failures/F68)

### Try It Yourself

#### Using a screen reader

**Steps to follow:**
1. Open a screen reader.
2. Navigate to a form that uses placeholder text as the only label.
3. Move focus to the input field using the screen reader.

**Expected results:** The screen reader reads the field's accessible name, indicating its purpose.

**Actual results:** The screen reader reads only the placeholder text, or announces the field with no name at all.

#### Using a keyboard

**Steps to follow:**
1. Navigate to the input field using the Tab key.
2. Type something into the field.
3. Navigate away from the field, then Tab back to it.

**Expected results:** The field still communicates its purpose after you return to it.

**Actual results:** The placeholder text is no longer visible, and there is no persistent label to identify the field.

#### Inspecting the browser's accessibility tree

**Steps to follow:**
1. Open your browser's developer tools.
2. Go to the Accessibility panel.
3. Select the input field and inspect its accessible name.

**Expected results:** The input has an accessible name that describes its purpose.

**Actual results:** The accessible name is empty, or it matches the placeholder text rather than a proper label.

### FAQ

**Why is this issue marked as critical?**

This issue is critical because people who use assistive technology, such as screen reader users, have no reliable way to determine the purpose of an unlabeled field. Without an accessible name, a screen reader may announce only the input type, such as "edit text," giving no indication of what information to enter. This affects form completion across all assistive technology and browser combinations.

**How does this issue relate to SC 1.3.1 Info and Relationships?**

SC 1.3.1 requires that information, structure, and relationships conveyed through presentation can also be determined programmatically. A label that exists only as placeholder text cannot be determined programmatically once a user has interacted with the field. You need an explicit `<label>` element, an `aria-label` attribute, or an `aria-labelledby` attribute to meet this criterion.

---

## Example 2: Best-practice entry

**Input:**
- `validation_name`: `redundant-title-attribute`
- `wcag_sc`: `"best practice"`
- `severity`: `needs review`
- `wcag_techniques_url`: (none)

**Output:**

---

## redundant-title-attribute

**The `title` attribute should not duplicate information already available through visible text or an accessible name.**

The `title` attribute is not consistently exposed across assistive technology and browsers. When it repeats text that is already visible or already provided as an accessible name, it adds no value for most users. In some configurations, it can create a confusing double-announcement for screen reader users.

Relying on `title` to convey important information is not reliable. If content is meaningful, it belongs in the visible text, in an accessible name, or in a `<label>` element, not only in a `title` attribute.

### Pass Patterns

An input uses an explicit `<label>` element without relying on the `title` attribute.

```html
<label for="search">Search</label>
<input type="text" id="search">
```

### Fail Patterns

A button's `title` attribute contains the same text as its visible label.

```html
<button title="Submit form">Submit form</button>
```

### Try It Yourself

#### Inspecting the browser's accessibility tree

**Steps to follow:**
1. Open your browser's developer tools.
2. Go to the Accessibility panel.
3. Select the element with a `title` attribute and inspect its accessible name and description.

**Expected results:** The element's accessible name and description are distinct and each conveys unique information.

**Actual results:** The accessible name and description contain identical text, indicating the `title` attribute is redundant.

### FAQ

**Why is this issue marked as needs review?**

This issue is marked as needs review because the impact varies by browser and assistive technology configuration. In some environments, a redundant `title` attribute causes a screen reader to announce the same information twice, which can disorient users. In others, it has no effect. The inconsistency in support makes it a pattern worth flagging for manual review.

**Why is this rule considered a best practice?**

The `title` attribute has inconsistent support across assistive technology and browsers, so it is not a reliable way to convey information. Removing redundant `title` attributes reduces the risk of double-announcement and keeps the accessibility tree clean. While no WCAG success criterion directly prohibits a redundant `title`, consistent accessible-name practices improve the experience for assistive technology users across all environments.
