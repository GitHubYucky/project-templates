# GitFlow

## Overview

GitFlow is a branching strategy for projects that need structured release management.
It is suitable when development, release preparation, and hotfix work need to run in parallel.

## Branches

- `main`
  - Always reflects production-ready code.
- `develop`
  - Integration branch for the next release.
- `feature/*`
  - Used for individual feature development.
  - Branch from `develop`.
  - Merge back into `develop`.
- `release/*`
  - Used for release stabilization and final adjustments.
  - Branch from `develop`.
  - Merge into both `main` and `develop`.
- `hotfix/*`
  - Used for urgent fixes to production.
  - Branch from `main`.
  - Merge into both `main` and `develop`.

## Basic Flow

1. Create `feature/*` from `develop`.
2. Open a pull request and merge the feature into `develop`.
3. When preparing a release, create `release/*` from `develop`.
4. Perform stabilization, version updates, and release notes work on `release/*`.
5. Merge `release/*` into `main` and tag the release.
6. Merge the same `release/*` back into `develop`.
7. If a production incident occurs, create `hotfix/*` from `main`.
8. Merge the hotfix into both `main` and `develop`.

## Example

### Feature Development

1. Create `feature/login-page` from `develop`.
2. Implement the login page and open a pull request into `develop`.
3. After CI and review pass, merge into `develop`.

### Release Preparation

1. Create `release/1.4.0` from `develop`.
2. Update the version, changelog, and final release fixes.
3. Merge `release/1.4.0` into `main`.
4. Tag `v1.4.0` on `main`.
5. Merge `release/1.4.0` back into `develop`.

### Production Hotfix

1. Create `hotfix/1.4.1-fix-login-timeout` from `main`.
2. Fix the production issue and open a pull request.
3. Merge into `main` and tag `v1.4.1`.
4. Merge the same hotfix back into `develop`.

## Rules

- Protect `main` and `develop`.
- Use pull requests for all merges.
- Require CI to pass before merge.
- Keep feature branches short-lived.
- Do not develop new features directly on `main`.
- Do not leave release branches open longer than necessary.
- Tag all production releases on `main`.

## Recommended When

- The project has planned releases.
- Multiple versions or release trains must be managed carefully.
- Release QA and stabilization are explicit phases.
- Production hotfixes must be handled separately from ongoing development.

## Avoid When

- The team deploys continuously many times a day.
- The project is small and branch overhead becomes unnecessary.
- Long-lived branches create repeated merge conflicts for the team.

## Pull Request Guidance

- One feature or fix per branch.
- Keep branch names descriptive, such as `feature/auth-session`.
- Require review before merge.
- Prefer squash merge or merge commit based on team history needs.

## Release Guidance

- Create tags from `main`.
- Maintain a changelog or release note entry for each release.
- Record versioning rules clearly, such as SemVer if used by the project.
