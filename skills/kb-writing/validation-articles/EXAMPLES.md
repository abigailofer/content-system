# Examples: Validation Articles

---

## How to read these examples

Each example shows a complete validation article output. The input block lists the variables passed to the skill. The output block is the finished article.

Examples cover two entry types:
- **Example 1** — a WCAG success criterion entry (all sections, including WCAG Patterns)
- **Example 2** — a best-practice entry (WCAG Patterns section omitted; "should" in rule; adjusted FAQ)

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

Input fields need a visible, persistent label so users always know what information to enter. Placeholder text disappears once a user starts typing, which means the field's purpose is no longer communicated — to the user or to assistive technology.

When a field relies on placeholder text alone, users who return to the field after entering data have no way to confirm what the field asked for. People with cognitive disabilities are especially affected by this.

### Pass Patterns

A visible `<label>` element is associated with the input using a matching `for` and `id` attribute pair. The placeholder is optional and supplements — not replaces — the label.

```html
<label for="email">Email address</label>
<input type="email" id="email" placeholder="name@example.com">
```

A visible label is also provided when using `aria-labelledby` to associate a separate element as the accessible name.

```html
<p id="email-label">Email address</p>
<input type="email" aria-labelledby="email-label" placeholder="name@example.com">
```

### Fail Patterns

No `<label>` element is present. The input relies entirely on placeholder text, which is not exposed as an accessible name by assistive technology.

```html
<input type="email" placeholder="Email address">
```

The `<label>` element is present in the HTML but is visually hidden using CSS in a way that removes it from the accessibility tree, leaving assistive technology with no accessible name.

```html
<label for="email" style="display: none;">Email address</label>
<input type="email" id="email" placeholder="Email address">
```

### WCAG Patterns

#### Sufficient techniques

[H44: Using label elements to associate text labels with form controls](https://www.w3.org/WAI/WCAG21/Techniques/html/H44)

[ARIA14: Using aria-label to provide an invisible label where a visible label cannot be used](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA14)

[ARIA16: Using aria-labelledby to provide a name for user interface controls](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA16)

#### Advisory techniques

[G167: Using an adjacent button to label the purpose of a field](https://www.w3.org/WAI/WCAG21/Techniques/general/G167)

#### Failure techniques

[F65: Failure of Success Criterion 1.1.1 due to omitting the alt attribute or text alternative on img elements, area elements, and input elements of type "image"](https://www.w3.org/WAI/WCAG21/Techniques/failures/F65)

### Try it Yourself

#### Using a screen reader

**Steps to follow**

1. Open a screen reader.
2. Navigate to a form that uses placeholder text as the only label.
3. Move focus to the input field using the screen reader.

**Expected result**

The screen reader reads the field's accessible name, indicating its purpose.

**Actual result**

The screen reader reads only the placeholder text, or announces the field with no name at all.

#### Using a keyboard

**Steps to follow**

1. Navigate to the input field using the Tab key.
2. Type something into the field.
3. Navigate away from the field, then Tab back to it.

**Expected result**

The field still communicates its purpose after you return to it.

**Actual result**

The placeholder text is no longer visible, and there is no persistent label to identify the field.

#### Inspecting the browser's accessibility tree

**Steps to follow**

1. Open your browser's developer tools.
2. Go to the Accessibility panel.
3. Select the input field and inspect its accessible name.

**Expected result**

The input has an accessible name that describes its purpose.

**Actual result**

The accessible name is empty, or it matches the placeholder text rather than a proper label.

### FAQ

**Why is this issue marked as `critical`?**

This issue is critical because people who use assistive technology — particularly screen reader users — have no reliable way to determine the purpose of an unlabeled field. Without an accessible name, a screen reader may announce only the input type, such as "edit text," giving no indication of what information to enter. This affects form completion across all assistive technology and browser combinations.

**How does this issue relate to SC 1.3.1 Info and Relationships?**

SC 1.3.1 requires that information, structure, and relationships conveyed through presentation can also be determined programmatically. A label that exists only as placeholder text cannot be determined programmatically once a user has interacted with the field. An explicit `<label>` element or an `aria-label` / `aria-labelledby` association is required to meet this criterion.

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

Relying on `title` to convey important information is not reliable. If content is meaningful, it belongs in the visible text, in an accessible name, or in a `<label>` element — not only in a `title` attribute.

### Pass Patterns

The `title` attribute is absent. The input's purpose is communicated through an explicit `<label>` element.

```html
<label for="search">Search</label>
<input type="text" id="search">
```

### Fail Patterns

The `title` attribute duplicates the visible button text. This creates a redundant tooltip that some screen readers announce in addition to the button's accessible name.

```html
<button title="Submit form">Submit form</button>
```

### Try it Yourself

#### Inspecting the browser's accessibility tree

**Steps to follow**

1. Open your browser's developer tools.
2. Go to the Accessibility panel.
3. Select the element with a `title` attribute and inspect its accessible name and description.

**Expected result**

The element's accessible name and description are distinct and each conveys unique information.

**Actual result**

The accessible name and description contain identical text, indicating the `title` attribute is redundant.

### FAQ

**Why is this issue marked as `needs review`?**

This issue is marked as needs review because the impact varies by browser and assistive technology configuration. In some environments, a redundant `title` attribute causes a screen reader to announce the same information twice, which can disorient users. In others, it has no effect. The inconsistency in support makes it a pattern worth flagging for manual review.

**Why is this validation considered a best practice?**

The `title` attribute has inconsistent support across assistive technology and browsers, so it is not a reliable way to convey information. Removing redundant `title` attributes reduces the risk of double-announcement and keeps the accessibility tree clean. While no WCAG success criterion directly prohibits a redundant `title`, consistent accessible-name practices improve the experience for assistive technology users across all environments.
