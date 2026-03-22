# Examples: Writing Empty States

---

## Example 1: First-run state

**Input:**
- Empty state type: first-run
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

## Example 2: No results (search)

**Input:**
- Empty state type: no-results
- Context: User searched for "quarterly report" in documents
- Query: "quarterly report"
- Filters active: PDF only

**Output:**
```yaml
empty_state:
  type: "no-results"
  headline: "No results for \"quarterly report\""
  support: "Try different keywords or remove the PDF filter."
  action:
    label: "Clear Filters"
    type: "search"
```

---

## Example 3: User-cleared state

**Input:**
- Empty state type: user-cleared
- Feature: Notifications
- Context: User marked all notifications as read / cleared inbox
- Primary action: None needed, but can navigate

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

## Example 4: Error-caused empty state

**Input:**
- Empty state type: error-caused
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

## Edge case: Empty state with no possible action

**Input:**
- Empty state type: user-cleared
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

## Edge case: No results with query suggestions

**Input:**
- Empty state type: no-results
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

## Example 6: No results with view all option

**Input:**
- Empty state type: no-results
- Context: User filtered reports by "Q4" with date range applied, no matches
- Filters active: Date range + keyword
- View all available: Yes

**Output:**
```yaml
empty_state:
  type: "no-results"
  headline: "No results for \"Q4\""
  support: "Try adjusting the date range or removing filters."
  action:
    label: "View All Reports"
    type: "navigate"
```

Note: "View All [Items]" is preferred over "Clear Filters" when resetting to the full list is more useful than incrementally removing filters.
