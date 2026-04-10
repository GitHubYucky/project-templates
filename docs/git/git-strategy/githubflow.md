# GitHub Flow

## Overview

GitHub Flow is a lightweight branching strategy centered on a single stable main branch.
It is suitable for projects that favor short-lived branches and frequent integration.

## Branches

- `main`
  - Always kept in a deployable or releasable state.
- `feature/*` or topic branches
  - Used for all changes, including features, fixes, refactors, and docs updates.
  - Branch from `main`.
  - Merge back into `main`.

## Basic Flow

1. Create a short-lived branch from `main`.
2. Make a focused change.
3. Push the branch and open a pull request early.
4. Run CI and complete review.
5. Merge into `main` once checks pass.
6. Deploy from `main` if the project supports continuous delivery.

## Example

### Feature Work

1. Create `feature/add-search-filter` from `main`.
2. Implement the filter and open a draft pull request.
3. Rebase on the latest `main` if needed.
4. Merge into `main` after review and CI pass.

### Bug Fix

1. Create `fix/null-check-on-profile-api` from `main`.
2. Add the fix and a regression test.
3. Merge into `main`.
4. Deploy from `main` if the project uses continuous delivery.

### Incomplete Work With Feature Flag

1. Create `feature/new-billing-screen` from `main`.
2. Merge the code behind a disabled feature flag.
3. Enable the flag only after validation is complete.

## Rules

- Protect `main`.
- Use pull requests for all changes.
- Require CI to pass before merge.
- Keep branches small and short-lived.
- Rebase or merge from `main` frequently to reduce drift.
- Do not keep long-running integration branches.

## Recommended When

- The team wants simple branching rules.
- The project ships continuously or very frequently.
- The team is small to medium-sized.
- The cost of release branches outweighs their benefit.

## Avoid When

- Releases require long stabilization periods.
- Multiple supported release lines must be maintained in parallel.
- The organization requires explicit release branches and strict staged handoff.

## Pull Request Guidance

- Keep each pull request narrowly scoped.
- Open draft pull requests early for visibility.
- Require at least one review if the team uses review gates.
- Prefer squash merge when you want a clean history.

## Deployment Guidance

- Treat `main` as the source of truth for production-ready code.
- If deployment is automated, only merge code that can be safely released.
- Use feature flags when incomplete work must be merged without being exposed.

## Release Guidance

- Use tags on `main` for formal releases.
- Maintain release notes if the project distributes versions externally.
