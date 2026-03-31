# Examples: Writing Empty States

---

## Example 1a: First-run — with CTA

**Input:**
- Empty state type: first-run (1a)
- Feature: Projects
- Target user: New user who just signed up
- Primary action: Create project

**Output:**
```yaml
empty_state:
  type: "first-run"
  headline: "Create your first project"
  support: "Projects help you organize your work and collaborate with your team."
  action:
    label: "New Project"
    type: "create"
```

---

## Example 1b: First-run — no CTA

**Input:**
- Empty state type: first-run (1b)
- Feature: App scans
- Target user: New user who has not yet run a scan
- Primary action: None — user must start a scan elsewhere in the product

**Output:**
```yaml
empty_state:
  type: "first-run"
  headline: "You haven't created any app scans yet"
  support: "To create an app navigation map, start a new scan and select Scan App."
  action:
    label: null
    type: null
```

Note: No CTA is shown because the user cannot act directly from this screen. Support text guides them to the relevant action elsewhere in the product.

---

## Example 2a: No results — search or filter returned nothing

**Input:**
- Empty state type: no-results (2a)
- Context: User searched for "quarterly report" in documents
- Query: "quarterly report"
- Filters active: PDF only

**Output (clear filters approach):**
```yaml
empty_state:
  type: "no-results"
  headline: "No results for \"quarterly report\""
  support: "Try different keywords or remove the PDF filter."
  action:
    label: "Clear Filters"
    type: "search"
```

**Output (view all approach):**
```yaml
empty_state:
  type: "no-results"
  headline: "No results for \"Q4\""
  support: "Try adjusting the date range or removing filters."
  action:
    label: "View All Reports"
    type: "navigate"
```

Note: Use "View All [Items]" when resetting to the full list is more useful than incrementally removing filters. Use "Clear Filters" when the user may want to adjust filters rather than abandon the search entirely.

---

## Example 2b: No results — possible typo

**Input:**
- Empty state type: no-results (2b)
- Context: User searched for "acounting" (typo)
- Suggestion available: "accounting"

**Output:**
```yaml
empty_state:
  type: "no-results"
  headline: "No results for \"acounting\""
  support: "Did you mean \"accounting\"?"
  action:
    label: "Search \"Accounting\""
    type: "search"
```

---

## Example 3a: User-cleared — user can create more

**Input:**
- Empty state type: user-cleared (3a)
- Feature: Notifications
- Context: User marked all notifications as read / cleared inbox

**Output:**
```yaml
empty_state:
  type: "user-cleared"
  headline: "All caught up"
  support: "New notifications will appear here."
  action:
    label: null
    type: null
```

---

## Example 3b: User-cleared — user cannot add content

**Input:**
- Empty state type: user-cleared (3b)
- Feature: Shared with me (files others share with you)
- Context: No one has shared files with this user
- Primary action: None — user cannot create content here

**Output:**
```yaml
empty_state:
  type: "user-cleared"
  headline: "No shared files yet"
  support: "Files others share with you will appear here."
  action:
    label: null
    type: null
```

Note: When user cannot take action, omit action button. Support text sets expectation.

---

## Example 4a: Error — retry available

**Input:**
- Empty state type: error-caused (4a)
- Feature: Activity feed
- Context: API call failed, cannot load items
- Primary action: Retry

**Output:**
```yaml
empty_state:
  type: "error-caused"
  headline: "Couldn't load activity"
  support: "Check your connection and try again."
  action:
    label: "Refresh Page"
    type: "navigate"
```

---

## Example 4b: Error — back to home is better recovery

**Input:**
- Empty state type: error-caused (4b)
- Feature: Report detail page
- Context: Page failed to load and retry is unlikely to help
- Primary action: Back to Home

**Output:**
```yaml
empty_state:
  type: "error-caused"
  headline: "Couldn't load this report"
  support: "Try refreshing the page or go back to home."
  action:
    label: "Back to Home"
    type: "navigate"
```
