# Issue Templates

## Bug Report

```markdown
## Description
[Clear, concise description of the bug]

## Steps to Reproduce
1. [First step]
2. [Second step]
3. [...]

## Expected Behaviour
[What should happen]

## Actual Behaviour
[What actually happens]

## Environment
- OS: [e.g., macOS 14.0, Ubuntu 22.04]
- Version: [app/package version]
- Browser: [if applicable]

## Additional Context
[Screenshots, logs, or other relevant information]
```

**Example:**

```markdown
## Description
Login form submits twice when clicking the submit button, causing duplicate API requests.

## Steps to Reproduce
1. Navigate to /login
2. Enter valid credentials
3. Click "Sign In" button once

## Expected Behaviour
Single API request to /api/auth/login, user redirected to dashboard.

## Actual Behaviour
Two API requests to /api/auth/login within 100ms. Second request sometimes fails with 429 rate limit error.

## Environment
- OS: macOS 14.2
- Version: v2.3.1
- Browser: Chrome 120

## Additional Context
Console shows the click handler firing twice. May be related to React 18 strict mode or event bubbling.
```

---

## Feature Request

```markdown
## Summary
[One-line description of the feature]

## User Story
As a [type of user], I want [goal] so that [benefit].

## Acceptance Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Tasks
- [ ] [Implementation task 1]
- [ ] [Implementation task 2]
- [ ] [Implementation task 3]

## Additional Context
[Mockups, references, or related issues]
```

**Example:**

```markdown
## Summary
Add dark mode toggle to settings page

## User Story
As a user, I want to switch between light and dark themes so that I can reduce eye strain when working at night.

## Acceptance Criteria
- [ ] Toggle switch appears in Settings > Appearance
- [ ] Theme persists across sessions (stored in localStorage)
- [ ] System preference detection on first visit
- [ ] Smooth transition animation between themes
- [ ] All components render correctly in both themes

## Tasks
- [ ] Create ThemeContext and useTheme hook
- [ ] Add CSS variables for color tokens
- [ ] Implement toggle component in settings
- [ ] Update all components to use theme tokens
- [ ] Add theme persistence logic
- [ ] Write tests for theme switching

## Additional Context
Design mockups: [link]
Related: #142 (color contrast issues)
```

---

## Epic

```markdown
## Overview
[High-level description of the epic and its business value]

## Goals
- [Goal 1]
- [Goal 2]

## Success Criteria
- [ ] [Measurable outcome 1]
- [ ] [Measurable outcome 2]

## Child Issues
This epic will be broken into the following issues:

1. **[Issue title 1]** - [Brief description]
2. **[Issue title 2]** - [Brief description]
3. **[Issue title 3]** - [Brief description]

## Out of Scope
- [What this epic explicitly does NOT include]

## Dependencies
- [External dependencies or blockers]
```

**Example:**

```markdown
## Overview
Implement a complete user authentication system supporting email/password login, OAuth providers, and session management. This enables secure user accounts and personalised experiences.

## Goals
- Secure, standards-compliant authentication
- Support multiple login methods
- Seamless user experience across devices

## Success Criteria
- [ ] Users can register, login, and logout
- [ ] OAuth working with Google and GitHub
- [ ] Sessions persist across browser restarts
- [ ] Password reset flow functional
- [ ] 95%+ test coverage on auth flows

## Child Issues
This epic will be broken into the following issues:

1. **Set up auth database schema** - User table, sessions, OAuth tokens
2. **Implement email/password auth** - Registration, login, password hashing
3. **Add OAuth providers** - Google and GitHub integration
4. **Build password reset flow** - Email verification, reset tokens
5. **Create auth UI components** - Login form, registration form, OAuth buttons
6. **Add session management** - Refresh tokens, logout, device tracking

## Out of Scope
- Two-factor authentication (future epic)
- SSO/SAML for enterprise (future epic)
- Social login beyond Google/GitHub

## Dependencies
- Email service configured (SendGrid)
- OAuth app credentials from Google/GitHub
```
