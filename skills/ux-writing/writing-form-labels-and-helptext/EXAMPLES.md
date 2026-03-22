# Examples: Writing Form Labels and Help Text

---

## Example 1: Simple text field

**Input:**
- Purpose: Collect user's full name
- Required: Yes
- Constraints: None

**Output:**
```yaml
form_field:
  label: "Full name"
  required: true
  input_type: "text"
  placeholder: null
  help_text: null
  validation:
    - rule: "required"
      error: "Enter your name"
```

---

## Example 2: Email with validation

**Input:**
- Purpose: Account email address
- Required: Yes
- Constraints: Must be valid email format

**Output:**
```yaml
form_field:
  label: "Email address"
  required: true
  input_type: "email"
  placeholder: "name@example.com"
  help_text: null
  validation:
    - rule: "required"
      error: "Enter your email address"
    - rule: "valid_email"
      error: "Enter a valid email address"
```

---

## Example 3: Password with requirements

**Input:**
- Purpose: Set account password
- Required: Yes
- Constraints: Min 8 chars, must include number

**Output:**
```yaml
form_field:
  label: "Password"
  required: true
  input_type: "password"
  placeholder: null
  help_text: "At least 8 characters with one number."
  validation:
    - rule: "required"
      error: "Enter a password"
    - rule: "min_length_8"
      error: "Password must be at least 8 characters"
    - rule: "has_number"
      error: "Password must include at least one number"
```

---

## Example 4: Optional phone number

**Input:**
- Purpose: Phone for account recovery
- Required: No
- Constraints: None, but format hint helpful

**Output:**
```yaml
form_field:
  label: "Phone number"
  required: false
  input_type: "tel"
  placeholder: "(555) 555-5555"
  help_text: "We'll only use this for account recovery."
  validation: null
```

---

## Example 5: Dropdown select

**Input:**
- Purpose: Select user's country
- Required: Yes
- Options: List of countries

**Output:**
```yaml
form_field:
  label: "Country"
  required: true
  input_type: "select"
  placeholder: "Select country"
  help_text: null
  options: ["United States", "Canada", "United Kingdom", "..."]
  validation:
    - rule: "required"
      error: "Select your country"
```

---

## Edge case: Credit card number

**Input:**
- Purpose: Payment card number
- Required: Yes
- Constraints: 16 digits, formatted

**Output:**
```yaml
form_field:
  label: "Card number"
  required: true
  input_type: "text"
  placeholder: "1234 5678 9012 3456"
  help_text: null
  inputmode: "numeric"
  validation:
    - rule: "required"
      error: "Enter your card number"
    - rule: "valid_card"
      error: "Enter a valid card number"
```

---

## Edge case: Textarea with character limit

**Input:**
- Purpose: Bio or description
- Required: No
- Constraints: Max 280 characters

**Output:**
```yaml
form_field:
  label: "Bio"
  required: false
  input_type: "textarea"
  placeholder: "Describe yourself"
  help_text: "Max 280 characters."
  max_length: 280
  show_character_count: true
  validation:
    - rule: "max_length_280"
      error: "Bio can't be longer than 280 characters"
```

---

## Example 6: Placeholder patterns reference

Approved placeholder patterns by field type (style guide §11.7.5):

| Field type | Pattern | Example |
|-----------|---------|---------|
| Text field | `Enter {name}` | `Enter project name` |
| Text field | `Enter {name}` | `Enter email address` |
| Description/textarea | `Describe the {collection}` | `Describe the test scenario` |
| Email | Example format | `name@example.com` |
| Select/dropdown | `Select {property}` | `Select country` |
| Select/dropdown | `Select {property}` | `Select severity` |
| Search | `Search {item}` | `Search campaigns` |
| Search | `Search {item}` | `Search issues` |

**Rules:**
- Never use an article in the pattern ("Select a country" ❌ → "Select country" ✅)
- Never repeat the label as the placeholder ("Email" on an Email field ❌)
- Never use fake data that looks real ("John Smith" ❌ → "Enter full name" ✅)
- Never use a placeholder as a substitute for a label
