# Contributing to GITutor

Thank you for contributing to **GITutor: AI-Powered Adaptive Programming Micro-Tutor**.

This document defines the team's Git workflow, branch conventions, commit format, and pull request process. All team members are expected to follow these guidelines to maintain a clean and traceable repository.

---

## Table of Contents

- [General Rules](#general-rules)
- [Branch Naming Convention](#branch-naming-convention)
- [Commit Message Format](#commit-message-format)
- [Pull Request Process](#pull-request-process)
- [Development Workflow](#development-workflow)
- [What Not to Do](#what-not-to-do)

---

## General Rules

- The `main` branch must always remain **stable and deployable**.
- **Do not develop features directly on `main`.**
- Every feature or fix must have a corresponding **GitHub Issue** before a branch is created.
- Commits must be **descriptive and meaningful** — avoid messages like `fix`, `update`, or `stuff`.
- All pull requests must **reference the corresponding GitHub Issue**.
- At least **one other team member** must review and approve a Pull Request before it is merged.
- Changes must be **tested and verified** before a task is marked Done in ClickUp.

---

## Branch Naming Convention

### Feature Branches

Use the following format for new features:

```
feature/<issue-number>-<short-name>
```

**Example:**

```
feature/12-user-login
feature/5-curriculum-roadmap
```

### Fix Branches

Use the following format for bug fixes:

```
fix/<issue-number>-<short-name>
```

**Example:**

```
fix/15-login-validation
fix/8-progress-not-saving
```

### Documentation / Chore Branches

Use the following format for documentation updates or maintenance tasks:

```
docs/<short-name>
chore/<short-name>
```

**Example:**

```
docs/update-requirements
chore/initialize-repository
```

---

## Commit Message Format

Commits should follow this structure:

```
<type>(<scope>): <short description>
```

### Type Values

| Type | When to Use |
|---|---|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation changes only |
| `chore` | Maintenance tasks (setup, configs, etc.) |
| `test` | Adding or updating tests |
| `refactor` | Code restructuring without feature/fix changes |
| `style` | Formatting changes only (no logic change) |

### Scope Values (aligned to feature groups)

| Scope | Feature Group |
|---|---|
| `auth` | Authentication & User Management |
| `curr` | Curriculum & Learning |
| `github` | GitHub Integration |
| `prog` | Progress & Performance |
| `adapt` | Assessment & Recommendations |
| `ai` | AI Micro-Tutor |
| `docs` | Documentation |

### Examples

```
feat(auth): implement login form
feat(curr): add curriculum roadmap scaffold
feat(github): connect exercise to GitHub repository
fix(curr): correct lesson progress tracking
fix(auth): handle invalid credential error
docs: update project requirements
chore: initialize repository structure
test(prog): add progress dashboard unit tests
```

---

## Pull Request Process

1. **Open a GitHub Issue** for the feature or fix before starting work.
2. **Create a branch** following the naming convention above.
3. Complete your work and **write descriptive commits**.
4. **Open a Pull Request** that:
   - References the GitHub Issue (e.g., `Closes #12`)
   - Has a clear title and description
   - Lists what was changed and why
5. **Request a review** from at least one other team member.
6. Address review feedback if any.
7. The reviewer **approves** the PR after verifying the changes.
8. The PR is **merged** into `main` only after approval and verification.
9. **Update the ClickUp task** status to Done.

---

## Development Workflow

Each task follows this traceability chain:

```
ClickUp Task
    → GitHub Issue
    → Feature/Fix Branch
    → Commit
    → Pull Request
    → Peer Review
    → Testing/Verification
    → Done
```

### Example Trace

| Step | Example |
|---|---|
| ClickUp Card | `CURR-01 — Interactive Curriculum Roadmap` |
| GitHub Issue | `#5` |
| Branch | `feature/5-curriculum-roadmap` |
| Commit | `feat(curr): implement curriculum roadmap scaffold` |
| Pull Request | References `#5` — reviewed by team member |
| Verification | Acceptance criteria checked and tested |
| Done | ClickUp task marked Done |

---

## What Not to Do

- ❌ Do not commit directly to `main`.
- ❌ Do not force push (`git push --force`).
- ❌ Do not commit `.env` files or files containing real secrets, API keys, passwords, or tokens.
- ❌ Do not merge your own Pull Request without another team member's review.
- ❌ Do not mark a task Done in ClickUp without review and verification evidence.
- ❌ Do not create branches without a corresponding GitHub Issue.
