# Templates: Writing Empty States

---

## Default empty state structure
```md
## [Headline]
[Support text explaining the state or next step]
**Action:** [Button Label]
```

## Structured output format
```yaml
empty_state:
  type: "<first-run|no-results|user-cleared|error-caused>"
  headline: "<acknowledge state - sentence case, no period, max 50 chars>"
  support: "<explain or guide - sentence case, ends with period, max 120 chars, optional>"
  action:
    label: "<button text - title case, no period, max 25 chars>"
    type: "<create|search|import|navigate>"
```

---

## Variations by empty state type

### First-run 1a — with CTA (user can act directly)
```md
## Get started with [feature]
[Brief value prop or first step.]
**Action:** Create [Item]
```

### First-run 1b — no CTA (user must act elsewhere or wait)
```md
## You haven't [done action] yet
[Instructions for how to get started elsewhere in the product, or note that content will appear here.]
```
Note: Omit action entirely. Support text either guides the user to take action elsewhere in the product, or sets the expectation that content will appear here once something happens.

### No results 2a — search or filter returned nothing
```md
## No results for "[query]"
Try different keywords or remove filters.
**Action:** Clear Filters
```
Note: "View All [Items]" is an alternative to "Clear Filters" when resetting to the full list is more useful than incrementally removing filters. See EXAMPLES.md for both approaches.

### No results 2b — possible typo, corrected query available
```md
## No results for "[query]"
Did you mean "[corrected query]"?
**Action:** Search "[Corrected Query]"
```

### User-cleared 3a — user can create more (with CTA)
```md
## No [items] yet
[Items] you create will appear here.
**Action:** Create [Item]
```

### User-cleared 3b — user cannot add content themselves (no CTA)
```md
## No [items] yet
[Items] will appear here once [trigger event].
```

### Error-caused 4a — retry available
```md
## Couldn't load [items]
Check your connection and try again.
**Action:** Refresh Page
```

### Error-caused 4b — back to home is better recovery
```md
## Couldn't load [items]
Try refreshing the page or go back to home.
**Action:** Back to Home
```

---

## Allowed variations
- Omit support text if headline + action are sufficient
- First-run can include illustration reference (implementation handles asset)
- No-results can suggest related queries if available
- Error-caused follows error message patterns (see writing-error-messages)
- Use "select" not "click" in support text (style guide §7.1)
