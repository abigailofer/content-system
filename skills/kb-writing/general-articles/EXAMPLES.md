# Examples: General Articles

---

## How to read this example

The input block shows the original article as provided. The output block shows the full rewrite, followed by the Notes on Rewrite section. Annotations in square brackets explain specific decisions made during the rewrite.

---

## Example: Rewriting an article on ARIA live regions

**Input (original article):**

> **ARIA Live Regions**
>
> ARIA live regions are an important accessibility feature that developers must implement correctly. The aria-live attribute tells screen readers to watch a region of the page and announce changes when they occur. There are different values you can use: "off" means no announcements, "polite" means the screen reader will wait until the user is idle before announcing, and "assertive" means it will interrupt whatever the screen reader is currently saying to announce the change immediately. You must be very careful with assertive because it will interrupt the user. Developers need to use polite in most situations. The aria-atomic attribute controls whether the entire region or just the changed part gets announced. If you set aria-atomic to true, the whole region will be announced. If you set it to false, only the changed part will be announced. Developers must also use aria-relevant to control what types of changes trigger announcements. It can be set to "additions", "removals", "text", or "all".

---

**Output:**

# Understanding ARIA Live Regions

## What are live regions?

### Keeping users informed about dynamic content

When content on a page updates without a full page reload — like a status message, a form error, or a live score — assistive technology users might miss the change entirely. ARIA live regions solve this by telling assistive technology to watch a part of the page and announce updates as they happen.

You add a live region by setting the `aria-live` attribute on any container element. Once set, assistive technology monitors that element and announces changes to users who can't see the visual update.

## Choosing the right announcement type

### When to use `aria-live="polite"`

For most situations, `aria-live="polite"` is the right choice. With this setting, assistive technology waits until the user finishes their current task — like reading a sentence or navigating a menu — before announcing the update. This avoids interrupting users mid-action.

```html
<div aria-live="polite" id="status-message">
  Your changes have been saved.
</div>
```

This approach works well for status messages, search result counts, and form submission confirmations.

### When to use `aria-live="assertive"`

Use `aria-live="assertive"` only for time-sensitive or critical updates. This setting interrupts whatever assistive technology is currently announcing, which can disorient users if overused. A good example is an error that blocks a user from completing a form.

```html
<div aria-live="assertive" id="error-message">
  Your session is about to expire. Save your work now.
</div>
```

Reserve assertive announcements for situations where a delay would genuinely cause a problem.

### When to use `aria-live="off"`

Setting `aria-live="off"` disables announcements for that region entirely. This is useful when you want to control a container with JavaScript but do not want every change announced automatically.

## Controlling what gets announced

### Using `aria-atomic`

The `aria-atomic` attribute controls how much of the live region gets announced when a change occurs.

- `aria-atomic="true"` — announces the entire region, even if only part of it changed. Use this for short, self-contained messages where the full context matters
- `aria-atomic="false"` — announces only the changed portion. Useful for regions where updates are frequent and only the new content is meaningful

```html
<div aria-live="polite" aria-atomic="true" id="notification">
  3 new messages
</div>
```

### Using `aria-relevant`

The `aria-relevant` attribute controls which types of changes trigger an announcement. It accepts these values:

- `additions` — announces when new content is added to the region
- `removals` — announces when content is removed
- `text` — announces when text content changes
- `all` — announces any change

> **Note:** The default value is `additions text`, which covers most use cases. Only set `aria-relevant` explicitly if you need to change this behavior.

---

## Notes on Rewrite

### Contradictions with accessibility best practices

No factual contradictions identified. The original's description of `aria-live` values and `aria-atomic` behavior is accurate.

### Content suggested for removal

No content flagged for removal. All original information was retained and redistributed across the rewritten structure.

### Major structural changes

- **Added an H1 title** — the original used a bold heading rather than a proper H1.
- **Broke the original single paragraph into sections** — the original covered all concepts in one dense block. Splitting into H2 sections (choosing announcement type, controlling what gets announced) makes the article easier to scan.
- **Added paragraph titles (H3)** — each concept now has its own H3 heading so readers can navigate directly to the value they need.
- **Converted inline list of `aria-live` values** — the original described all three values in a single sentence. Separate H3 subsections with code examples make each value easier to compare and understand.
- **Added code examples** — the original had none. Examples were added for `aria-live="polite"`, `aria-live="assertive"`, and `aria-atomic="true"` to show practical implementation.
- **Softened directive tone** — phrases like "you must be very careful" and "developers must" were rewritten as guidance explaining the benefit or risk, per the tone guidelines.
- **Added a Note callout** for `aria-relevant` — the default value information is important context but would have broken the flow of the bullet list.
