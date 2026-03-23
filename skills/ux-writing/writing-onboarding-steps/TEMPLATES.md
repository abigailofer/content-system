# Templates: Writing Onboarding Steps

---

## Default onboarding step structure
```md
**Step [n] of [total]**
## [Headline - what to do, sentence case, no period]
[Body - why or how, sentence case, ends with period.]
[Action button - title case, no period]
```

## Structured output format
```yaml
onboarding_flow:
  type: "<setup-wizard|feature-tour|contextual-tip>"
  total_steps: <number>
  steps:
    - step: 1
      headline: "<what to do - sentence case, no period, max 50 chars>"
      body: "<why or how - sentence case, ends with period, max 150 chars>"
      action:
        label: "<button text - title case, no period, max 25 chars>"
        type: "<next|complete|action>"
```

---

## Variations by onboarding type

### Setup wizard (required configuration)
```yaml
steps:
  - step: 1
    headline: "Welcome to [Product]"
    body: "Let's get you set up. This takes about 2 minutes."
    action:
      label: "Get Started"
      type: "next"
  - step: 2
    headline: "Add your workspace name"
    body: "This is how your team will identify your workspace."
    action:
      label: "Continue"
      type: "next"
```

### Feature tour (optional education)
```yaml
steps:
  - step: 1
    headline: "This is your dashboard"
    body: "See all your projects and recent activity at a glance."
    action:
      label: "Next"
      type: "next"
```

### Contextual tip (in-place education)
```yaml
steps:
  - step: 1
    headline: "Tip: Use keyboard shortcuts"
    body: "Press ⌘K to open the command palette."
    action:
      label: "Got It"
      type: "complete"
```

---

## Progress indicator patterns
- "Step 1 of 5"
- Progress bar (visual, no text)
- "Almost done" for final step

---

## Allowed variations
- Welcome step can be more expressive
- Final step should celebrate completion without exclamation points
- Skip option for non-required tours: "Skip Tour"
- Time estimate on first step for longer wizards
