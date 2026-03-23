# Examples: Writing Onboarding Steps

---

## Example 1: Setup wizard

**Input:**
- Onboarding type: setup-wizard
- Product: Project management tool
- Required steps: Name workspace, invite team, create first project
- User: Brand new signup

**Output:**
```yaml
onboarding_flow:
  type: "setup-wizard"
  total_steps: 4
  steps:
    - step: 1
      headline: "Welcome to TaskFlow"
      body: "Let's set up your workspace. This takes about 2 minutes."
      action:
        label: "Get Started"
        type: "next"
    - step: 2
      headline: "Name your workspace"
      body: "Choose a name your team will recognize."
      action:
        label: "Continue"
        type: "next"
    - step: 3
      headline: "Invite your team"
      body: "Collaboration works best with others. You can skip and add people later."
      action:
        label: "Continue"
        type: "next"
    - step: 4
      headline: "Your workspace is ready"
      body: "Create your first project to get started."
      action:
        label: "Create Project"
        type: "complete"
```

---

## Example 2: Feature tour

**Input:**
- Onboarding type: feature-tour
- Feature: New dashboard redesign
- User: Existing user seeing new UI
- Steps: Overview, key areas, new features

**Output:**
```yaml
onboarding_flow:
  type: "feature-tour"
  total_steps: 3
  steps:
    - step: 1
      headline: "Welcome to your new dashboard"
      body: "The dashboard has been redesigned to help you find things faster."
      action:
        label: "Take a Tour"
        type: "next"
    - step: 2
      headline: "Quick access to recent projects"
      body: "Your most recent projects now appear right at the top."
      action:
        label: "Next"
        type: "next"
    - step: 3
      headline: "New activity feed"
      body: "See updates from your team in real time."
      action:
        label: "Done"
        type: "complete"
```

---

## Example 3: Contextual tip

**Input:**
- Onboarding type: contextual-tip
- Context: User just created their first project
- Goal: Teach about templates

**Output:**
```yaml
onboarding_flow:
  type: "contextual-tip"
  total_steps: 1
  steps:
    - step: 1
      headline: "Tip: Start with a template"
      body: "Save time by starting from one of our pre-built project templates."
      action:
        label: "Browse Templates"
        type: "action"
```

---

## Edge case: Long required setup

**Input:**
- Onboarding type: setup-wizard
- Product: Enterprise security tool
- Steps: 6 required configuration steps
- User: IT admin

**Output:**
```yaml
onboarding_flow:
  type: "setup-wizard"
  total_steps: 6
  steps:
    - step: 1
      headline: "Set up SecureGuard"
      body: "Complete these 6 steps to configure your security policies. About 10 minutes."
      action:
        label: "Begin Setup"
        type: "next"
    - step: 2
      headline: "Connect your identity provider"
      body: "Link your SSO provider to manage user access."
      action:
        label: "Connect"
        type: "action"
    - step: 3
      headline: "Define access policies"
      body: "Set rules for who can access what."
      action:
        label: "Continue"
        type: "next"
    - step: 4
      headline: "Configure audit logging"
      body: "Choose what events to track for compliance."
      action:
        label: "Continue"
        type: "next"
    - step: 5
      headline: "Set up alerts"
      body: "Get notified about security events that matter."
      action:
        label: "Continue"
        type: "next"
    - step: 6
      headline: "Setup complete"
      body: "SecureGuard is now configured and protecting your organization."
      action:
        label: "Go to Dashboard"
        type: "complete"
```

Note: For 6+ steps, provide time estimate upfront and consider allowing save & resume.

---

## Edge case: Optional tour with skip

**Input:**
- Onboarding type: feature-tour
- Context: New user can skip but encouraged to learn
- User: Impatient power user type

**Output:**
```yaml
onboarding_flow:
  type: "feature-tour"
  total_steps: 3
  skip_option: true
  steps:
    - step: 1
      headline: "Quick tour of the basics"
      body: "Learn the key features in under a minute."
      action:
        label: "Start Tour"
        type: "next"
      secondary_action:
        label: "Skip"
        type: "complete"
```

Note: Skip option respects user autonomy while making the tour inviting.

---

## Example 6: Questions vs statements

Demonstrates when to use question framing vs statement framing in onboarding steps (style guide §13.8).

### Question framing — use when gathering information
```yaml
onboarding_flow:
  type: "setup-wizard"
  total_steps: 3
  steps:
    - step: 1
      headline: "How will you use TaskFlow?"
      body: "We'll tailor your setup based on how your team works."
      action:
        label: "Continue"
        type: "next"
    - step: 2
      headline: "What does your team work on?"
      body: "Select the types of projects you manage most often."
      action:
        label: "Continue"
        type: "next"
```

### Statement framing — use when giving clear instructions
```yaml
onboarding_flow:
  type: "setup-wizard"
  total_steps: 3
  steps:
    - step: 1
      headline: "Choose how you'll use TaskFlow"
      body: "Select the option that best describes how your team works."
      action:
        label: "Continue"
        type: "next"
    - step: 2
      headline: "Select your project types"
      body: "Choose the types of projects you manage most often."
      action:
        label: "Continue"
        type: "next"
```

**When to use each:**
- Questions feel more personal but can add friction — use when the user's answer meaningfully shapes the experience
- Statements are more direct and seamless — use when the step is instructional rather than conversational
