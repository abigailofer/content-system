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

### First-run (new user, no content yet)
```md
## Get started with [feature]
[Brief value prop or first step.]
**Action:** Create [Item]
```

### No results (search/filter returned nothing)
```md
## No results for "[query]"
Try different keywords or remove filters.
**Action:** Clear Filters
```

### No results (with view all option)
```md
## No results for "[query]"
Try different keywords or remove filters.
**Action:** View All [Items]
```

### User-cleared (user deleted all items)
```md
## No [items] yet
[Items] you create will appear here.
**Action:** Create [Item]
```

### Error-caused (empty due to load failure)
```md
## Couldn't load [items]
Check your connection and try again.
**Action:** Refresh Page
```

### Error-caused (with back to home option)
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
- No-results can offer "View All [Items]" to reset filters
- Error-caused follows error message patterns (see writing-error-messages)
- Use "select" not "click" in support text (style guide §7.1)
