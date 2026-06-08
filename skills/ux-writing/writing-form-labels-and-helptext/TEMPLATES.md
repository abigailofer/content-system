# Templates: Writing Form Labels and Help Text

---

## Default form field structure
```md
**[Label]** (optional indicator if applicable)
[Input field with placeholder]
[Help text below field.]
```

## Structured output format
```yaml
form_field:
  label: "<what to enter - sentence case, no period, max 40 chars>"
  required: <true|false>
  input_type: "<text|email|password|tel|url|number|date|select|textarea>"
  placeholder: "<format hint - sentence case, no period, max 40 chars, optional>"
  help_text: "<constraints or context - sentence case, ends with period, max 100 chars, optional>"
  validation:
    - rule: "<validation rule>"
      error: "<error message - sentence case, no period, max 80 chars>"
```

---

## Variations by input type

### Text input
```yaml
form_field:
  label: "Full name"
  required: true
  input_type: "text"
  placeholder: null
  help_text: null
```

### Email input
```yaml
form_field:
  label: "Email address"
  required: true
  input_type: "email"
  placeholder: "name@company.com"
  help_text: null
  validation:
    - rule: "valid_email"
      error: "Enter a valid email address"
```

### Password input
```yaml
form_field:
  label: "Password"
  required: true
  input_type: "password"
  placeholder: null
  help_text: "At least 8 characters with a number and symbol."
  validation:
    - rule: "min_length_8"
      error: "Password must be at least 8 characters"
    - rule: "has_number"
      error: "Password must include at least one number"
    - rule: "has_symbol"
      error: "Password must include at least one symbol"
```

### Select/dropdown
```yaml
form_field:
  label: "Country"
  # Label: singular, lowercase — style guide §11.6.1
  required: true
  input_type: "select"
  placeholder: "Select country"
  # Placeholder pattern: Select {property} — style guide §11.6.2
  help_text: null
  options: ["United States", "Canada", "..."]
```

### Optional field
```yaml
form_field:
  label: "Phone number"
  required: false
  input_type: "tel"
  placeholder: "(555) 555-5555"
  help_text: "We'll only use this for account recovery."
  optional_indicator: "(optional)"
```

### Textarea
```yaml
form_field:
  label: "Bio"
  required: false
  input_type: "textarea"
  placeholder: "Example: Accessibility advocate with 5 years of experience"
  # Placeholder pattern for description fields: Example: {realistic value} — style guide §11.7.5
  help_text: "Max 280 characters."
  optional_indicator: "(optional)"
  max_length: 280
  show_character_count: true
```

---

## Placeholder patterns
Follow these approved patterns (style guide §11.7.5):

| Field type | Pattern | Example |
|-----------|---------|---------|
| Text field | `Example: {realistic value}` | `Example: Project name` |
| Description/textarea | `Example: {realistic value}` | `Example: Groups issues by business unit` |
| Email | Use example format | `name@example.com` |
| Select/dropdown | `Select {property}` | `Select country` |
| Search | `Search {item}` | `Search campaigns` |

---

## Allowed variations
- Required fields are marked with a red asterisk (*); optional fields have no indicator
- Use inline validation errors below the field
- Group related fields (e.g., first name + last name on same row)
- Omit placeholder if help text already covers format
