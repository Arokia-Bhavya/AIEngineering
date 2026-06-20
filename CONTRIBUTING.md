# Contributing Guide

Thank you for considering contributing to this project! We welcome contributions of any kind, whether it’s bug reports, documentation improvements, or code changes. Please follow the guidelines below to make the contribution process smooth for everyone.

---

## Table of Contents

1. [Code Style](#code-style)
2. [Branch Naming](#branch-naming)
3. [Commit Message Conventions](#commit-message-conventions)
4. [Pull Request Review Process](#pull-request-review-process)
5. [Getting Help](#getting-help)
6. [License](#license)

---

## Code Style

- **Language**: Follow the idiomatic style of the project's primary language(s).  
- **Linting**: Run the provided linter before committing.  
  ```bash
  npm run lint   # JavaScript/TypeScript projects
  flake8 .       # Python projects
  ```
- **Formatting**: Use the configured formatter (e.g., Prettier, Black).  
  ```bash
  npm run format   # JavaScript/TypeScript
  black .          # Python
  ```
- **Type Checking** (if applicable): Ensure the code passes static type checks.  
  ```bash
  npm run type-check   # TypeScript
  mypy .               # Python
  ```
- **Tests**: Add or update unit/integration tests for any new functionality. All tests must pass locally and on CI.

---

## Branch Naming

Use short, descriptive branch names that convey the purpose of the work. Prefix the branch name with one of the following categories:

| Prefix      | When to Use                                 |
|-------------|---------------------------------------------|
| `feature/`  | Adding a new feature or enhancement.       |
| `bugfix/`   | Fixing a bug.                               |
| `hotfix/`   | Critical fixes that need to go to production immediately. |
| `docs/`     | Documentation changes only.                |
| `chore/`    | Maintenance tasks (e.g., CI config, dependencies). |

**Examples**:
```
feature/add-authentication
bugfix/fix-login-crash
docs/update-readme
```

---

## Commit Message Conventions

We follow the **Conventional Commits** specification. The format is:

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

- **type** – one of `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, `build`, `ci`, `revert`.
- **scope** – optional, a short identifier of the area affected (e.g., `auth`, `ui`).
- **description** – concise summary (max 72 characters).
- **body** – (optional) longer explanation of the change.
- **footer** – (optional) references to issues or breaking changes.

**Examples**:
```
feat(auth): add JWT token generation

Implement token creation using jsonwebtoken and add unit tests.

Closes #42
```
```
fix(ui): correct button alignment on mobile

The button was mis‑aligned due to a missing flex property.
```

---

## Pull Request Review Process

1. **Create a PR** from your feature/bugfix branch into the `main` (or designated) branch.
2. **Title**: Use a clear, concise title that follows the commit message style (without the scope prefix).
3. **Description**: Include:
   - A brief summary of what the PR does.
   - Reference any related issues (e.g., `Fixes #123`).
   - Any additional context needed for reviewers.
4. **Automated Checks**: CI will run linting, tests, and type checks automatically. Ensure they all pass.
5. **Reviewers**: Assign at least one reviewer. Reviewers should:
   - Verify the code follows the style guidelines.
   - Ensure tests cover new/changed functionality.
   - Check that documentation is updated if needed.
6. **Approval**: A PR can be merged after at least one approval and all required checks pass.
7. **Merging**: Use **Squash and merge** to keep a clean history. The commit message will be generated from the PR title and description.

---

## Getting Help

- **Open an issue**: If you encounter a problem or have a question, start by opening an issue.
- **Slack/Discord**: Join our community chat (link in the README) for real‑time assistance.
- **Code of Conduct**: Please read the `CODE_OF_CONDUCT.md` file for expected behavior.

---

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see `LICENSE`).
