# Commit Messages

## Overview

Commit messages should make the intent of a change easy to understand from history alone.
They are used for code review, release notes, debugging, and rollback decisions.

## Basic Rules

- Write commit messages in imperative mood.
- Keep the subject line short and specific.
- Make one logical change per commit.
- Do not mix unrelated refactors, fixes, and features in a single commit.
- Prefer clarity over abbreviations.
- Use English or Japanese consistently within the same repository.
- Avoid vague subjects such as `fix`, `update`, or `changes`.

## Recommended Format

Use the following structure when possible.

```text
<type>: <subject>

<body>
```

## Types

- `feat`
  - New feature or user-visible behavior.
- `fix`
  - Bug fix or regression fix.
- `refactor`
  - Internal code change without behavior change.
- `docs`
  - Documentation update only.
- `test`
  - Test addition or test maintenance.
- `build`
  - Build, dependency, or tooling change.
- `ci`
  - CI workflow or automation change.
- `chore`
  - Repository maintenance that does not fit other types.

## Subject Line Rules

- Aim for roughly 50 characters or fewer.
- Start with the main action.
- Do not end the subject with a period.
- Describe what changed, not the implementation detail alone.

## Body Rules

- Add a body when the reason is not obvious from the subject.
- Explain why the change was needed.
- Mention important constraints, tradeoffs, or migration impact.
- Wrap lines if the team has a line-length rule.

## Good Examples

```text
feat: add GitHub Flow decision guide
```

```text
fix: prevent null access in profile response parser
```

```text
docs: add examples to GitFlow and GitHub Flow guides
```

```text
ci: run lint and test on pull requests
```

```text
refactor: split repository setup logic by environment
```

## Bad Examples

```text
fix
```

```text
update files
```

```text
misc changes
```

```text
feat: stuff for release maybe
```

## Commit Granularity

- Create separate commits for feature work, formatting, and dependency updates.
- Keep generated files in the same commit only when they are a direct result of the source change.
- Prefer several small coherent commits over one large ambiguous commit.

## Revert Rule

When reverting a commit, use an explicit message format.

```text
revert: <original subject>
```

Include the reason in the body if the revert is not self-explanatory.

## Team Rule Template

Teams may adopt the following minimum rule set.

1. All commits must have a clear subject.
2. All commits should use a `type: subject` format.
3. Squash merge is allowed only if the final commit message is rewritten clearly.
4. Merge commits should be reserved for cases where branch history must be preserved.
5. WIP commits must not remain in the default branch history.

## Recommended When Using Pull Requests

- Clean up noisy local commits before merge.
- Preserve meaningful intermediate commits only when they help future investigation.
- Rewrite the final merge commit message so it matches repository rules.
