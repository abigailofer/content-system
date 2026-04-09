# Examples: Writing Error Messages

---

## Example 1: Validation error

**Input:**
- Error type: validation
- Context: User submitted email field with invalid format
- Field: Email address

**Output:**
```yaml
error:
  title: "Enter a valid email address"
  body: null
  action:
    label: null
    type: null
```

Inline display: "Enter a valid email address" (below field, no action button)

---

## Example 2: Network error

**Input:**
- Error type: network
- Context: API call failed due to connectivity
- User action: Saving a document

**Output:**
```yaml
error:
  title: "Couldn't save your changes"
  body: "Check your internet connection and try again."
  action:
    label: "Retry"
    type: "retry"
```

---

## Example 3: Permission error

**Input:**
- Error type: permission
- Context: User tried to access admin settings without admin role
- User action: Selecting "Admin Settings" link

**Output:**
```yaml
error:
  title: "You don't have access to admin settings"
  body: "Contact your workspace admin to request access."
  action:
    label: "Request Access"
    type: "navigate"
```

---

## Example 4: System error (unknown cause)

**Input:**
- Error type: system
- Context: Unexpected server error, cause unknown
- User action: Loading dashboard

**Output:**
```yaml
error:
  title: "Couldn't load your dashboard"
  body: "We're working on it. Try again in a few minutes."
  action:
    label: "Try Again"
    type: "retry"
```

---

## Example 5: Not found error

**Input:**
- Error type: not-found
- Context: User navigated to a deleted project via old link
- Item: Project

**Output:**
```yaml
error:
  title: "Project not found"
  body: "This project may have been deleted or moved."
  action:
    label: "Go to Projects"
    type: "navigate"
```

---

## Edge case: Error with no recovery action

**Input:**
- Error type: system
- Context: Account suspended by admin
- User action: Logging in

**Output:**
```yaml
error:
  title: "Your account has been suspended"
  body: "Contact your organization's admin for help."
  action:
    label: "Dismiss"
    type: "dismiss"
```

Note: When no in-app recovery exists, direct to human support.

---

## Example 6: Validation error patterns

The following are approved out-of-the-box validation error messages. All are inline, sentence case, no trailing period.

### Missing information

| Context | Message |
|---------|---------|
| Text field | `Enter your email address` |
| Text field | `Enter a collection name` |
| Radio buttons | `Select a budget` |
| Checkboxes | `Select at least 1 industry` |

### Selection limits

| Context | Message |
|---------|---------|
| Too many selected | `Select up to 7 industries` |
| Too many entered | `Enter up to 5 tags` |

### Character limits

| Context | Message |
|---------|---------|
| Exceeded max | `{Name} can't be longer than 40 characters` |
| Below min | `{Name} must be at least 5 characters` |

### Invalid input

| Context | Message |
|---------|---------|
| Numbers or special characters | `{Name} can't contain numbers or special characters` |
| Special characters only | `{Name} can't contain special characters` |
| Spaces not supported | `{Name} can't contain spaces` |
| Allowed characters | `{Key display name} can include letters (A-Z, a-z), numbers (0-9), spaces, hyphens ( - ), and underscores ( _ )` |
| Domain not found | `Couldn't find your Jira domain. Please check it's written correctly.` |

### Incorrect format

| Context | Message |
|---------|---------|
| Postal code | `{Postal code} must be 5 digits` |
| Phone number | `Enter a 10-digit number` |

### File errors

| Context | Message |
|---------|---------|
| File type (longer) | `This file type isn't supported. Use PNG, JPG, or GIF` |
| File type (shorter) | `File type must be CSV` |
| File size (generic) | `Maximum file size is 1 MB` |
| File size (email) | `Maximum email size is 1 MB. Remove elements such as products or images, then try saving again.` |

### Not supported

| Context | Message |
|---------|---------|
| Country code | `We don't support that {country code}. Use your {email} instead.` |

### Already exists

| Context | Message |
|---------|---------|
| Duplicate name | `{Name} already exists` |

### Dependency gating

| Context | Message |
|---------|---------|
| Prerequisite action required | `You need to {required initial action} before you can {attempted action}` |
| File contains errors | See Example: CSV upload with errors below |

---

## Example: CSV upload with errors

**Input:**
- Error type: validation
- Context: User uploaded a CSV file that contains errors
- User action: Uploading a file
- Reversibility: Recoverable — user can fix and re-upload

**Output:**
```yaml
error:
  title: "Your file has errors"
  body: "Your file couldn't be uploaded. Download the annotated file, fix the errors, then upload it again."
  action:
    label: "Download Annotated File"
    type: "download"
```
