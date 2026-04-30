# Writing Permission and Access Messages

---
name: writing-permission-and-access-messages
description: Write clear permission requests and access messages for UI. Use when requesting permissions, explaining access requirements, showing access denied states, or guiding users through permission flows.
---

## Quick start
Collect or infer:
- Permission type (location, camera, notifications, data access, role-based)
- Current state (requesting, granted, denied, expired)
- Why the permission is needed
- Impact of granting or denying

Then produce output using [TEMPLATES.md](TEMPLATES.md). Validate with [RUBRIC.md](RUBRIC.md).

---

## Workflow
1. Identify permission type and current state
2. Write the headline (what access is needed) — sentence case, no period
3. Write the explanation (why and what user gets) — sentence case, ends with period
4. Specify available actions — title case, no period
5. Run the rubric check. Revise until it passes.

---

## Degrees of freedom
- **Low**: Must explain why permission is needed
- **Medium**: Explanation detail varies by permission sensitivity
- **Allowed variation**: Pre-request prompts optional but recommended for sensitive permissions

---

## Constraints

| Element | Case | Period | Max length | Other |
|---------|------|--------|------------|-------|
| Headline (H2) | Sentence case | No | 60 chars | States what access is needed |
| Explanation | Sentence case | Yes | 150 chars | Must include user benefit |
| Allow label | Title case | No | 20 chars | Specific to the action |
| Deny label | Title case | No | 20 chars | Always present; never forced |

### Tone rules
- Always lead with user benefit, not app need
- Avoid "please" unless the user is being asked to do something genuinely effortful (style guide §1.7.2)
- Never use "click" — use "select" (style guide §7.1)
- Use "turn on / turn off" not "enable / disable" (style guide §7.1)
- Never request unnecessary permissions
- Use "Not Now" instead of "Don't Allow" for softer decline

### Support contact copy
- Button: "Contact Support" (title case, no brand name)
- Inline text: "Contact Evinced Support"
- Never: "Contact us", "Get help", "Support"
- Use a pre-request prompt before triggering the system dialog
- Link to privacy policy for data-sensitive permissions
- For re-authentication flows, allow paste and autofill on password fields (WCAG 3.3.8)
- Offer cognitive-free authentication alternatives where possible (WCAG 3.3.9)

---

## References
- Templates: [TEMPLATES.md](TEMPLATES.md)
- Rubric: [RUBRIC.md](RUBRIC.md)
- Examples: [EXAMPLES.md](EXAMPLES.md)
- Glossary: [../../../shared/glossary.md](../../../shared/glossary.md)
- Words to use: [../../../shared/words-to-use.md](../../../shared/words-to-use.md)
- Words to avoid: [../../../shared/words-to-avoid.md](../../../shared/words-to-avoid.md)
