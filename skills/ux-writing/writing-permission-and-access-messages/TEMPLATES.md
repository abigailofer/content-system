# Templates: Writing Permission and Access Messages

---

## Default permission request structure
```md
## [Headline - what access, sentence case, no period]
[Explanation - why needed and benefit, sentence case, ends with period.]
[Deny action] | [Allow action]
```

## Structured output format
```yaml
permission_message:
  type: "<system|data|role|feature>"
  state: "<requesting|denied|expired|insufficient>"
  headline: "<what access - sentence case, no period, max 60 chars>"
  explanation: "<why and benefit - sentence case, ends with period, max 150 chars>"
  allow:
    label: "<grant action - title case, no period, max 20 chars>"
  deny:
    label: "<decline action - title case, no period, max 20 chars>"
```

---

## Variations by message state

### Permission request (before system prompt)
```yaml
permission_message:
  type: "system"
  state: "requesting"
  headline: "Allow location access?"
  explanation: "We use your location to show nearby stores and calculate delivery times."
  allow:
    label: "Allow"
  deny:
    label: "Not Now"
```

### Permission denied (user previously declined)
```yaml
permission_message:
  type: "system"
  state: "denied"
  headline: "Location access needed"
  explanation: "To use this feature, allow location access in your device settings."
  allow:
    label: "Open Settings"
  deny:
    label: "Cancel"
```

### Insufficient role access
```yaml
permission_message:
  type: "role"
  state: "insufficient"
  headline: "Admin access required"
  explanation: "Only workspace admins can change billing settings."
  allow:
    label: "Request Access"
  deny:
    label: "Cancel"
```

### Feature access (paywall or plan limit)
```yaml
permission_message:
  type: "feature"
  state: "insufficient"
  headline: "Upgrade to use this feature"
  explanation: "Advanced analytics is available on Pro and Enterprise plans."
  allow:
    label: "View Plans"
  deny:
    label: "Maybe Later"
```

---

## Pre-request pattern (recommended for sensitive permissions)
Show a custom prompt before triggering the system permission dialog:
```yaml
pre_request:
  headline: "See stores near you"
  explanation: "Allow location access to find stores and get accurate delivery times."
  allow:
    label: "Continue"
  deny:
    label: "Not Now"
```

---

## Allowed variations
- Use "Not Now" instead of "Don't Allow" for softer decline
- Include illustration showing feature that needs permission
- Link to privacy policy for data-sensitive permissions
