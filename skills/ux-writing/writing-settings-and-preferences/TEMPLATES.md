# Templates: Writing Settings and Preferences

---

## Default setting structure
```md
**[Label]**
[Description of what happens.]
[Control: toggle/select/input]
```

## Structured output format
```yaml
setting:
  category: "<account|notifications|privacy|appearance|integrations|advanced>"
  label: "<what it controls - sentence case, no period, max 40 chars>"
  description: "<what happens - sentence case, ends with period, max 120 chars, optional>"
  type: "<toggle|select|input|action>"
  default: "<default value>"
  options: ["<option1>", "<option2>"]  # for select type only
```

---

## Variations by setting type

### Toggle (on/off)
```yaml
setting:
  label: "Email notifications"
  # Label describes the ON state — style guide §11.5.1
  description: "Receive email updates about activity in your projects."
  type: "toggle"
  default: true
```

### Select (choose from options)
```yaml
setting:
  label: "Theme"
  description: "Choose how the app looks."
  type: "select"
  default: "System"
  options: ["Light", "Dark", "System"]
```

### Input (text entry)
```yaml
setting:
  label: "Display name"
  description: "This is how your name appears to others."
  type: "input"
  default: null
  placeholder: "Enter your name"
  # Placeholder pattern: Enter {name} — style guide §11.7.5
```

### Action (button that does something)
```yaml
setting:
  label: "Export data"
  description: "Download a copy of all your data."
  type: "action"
  action_label: "Export Data"
  # Action label: title case, verb + noun
```

### Destructive action
```yaml
setting:
  label: "Delete account"
  description: "Permanently delete your account and all your data. You cannot undo this action."
  type: "action"
  action_label: "Delete Account"
  style: "destructive"
  requires_confirmation: true
  # Confirmation modal follows writing-confirmation-dialogs pattern
```

---

## Section header patterns
- "Account" — profile, email, password
- "Notifications" — email, push, in-app
- "Privacy" — visibility, data sharing
- "Appearance" — theme, density, language
- "Integrations" — connected apps, APIs
- "Advanced" — developer options, experimental

---

## Allowed variations
- Omit description if label is completely self-explanatory
- Add helper text below input fields for format requirements
- For complex settings with documentation, use descriptive link text — never "Learn more"
  - Good: "Learn about API rate limits"
  - Bad: "Learn more"
