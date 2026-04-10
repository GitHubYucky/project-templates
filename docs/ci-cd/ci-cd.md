# CI/CD

## Overview

CI/CD should provide a repeatable path from change creation to safe delivery.
This repository should keep CI/CD guidance generic enough to work across different project types and deployment models.

## CI Goals

- Validate every change automatically.
- Detect failures early in pull requests.
- Keep the default branch in a releasable state.
- Reduce manual verification work.

## CD Goals

- Deliver artifacts or deployments through a consistent process.
- Separate build, verification, and release responsibilities clearly.
- Reduce manual release errors.
- Make rollback and recovery possible.

## Minimum CI Pipeline

All projects created from this template should define at least these stages.

1. Install dependencies
2. Lint or static validation
3. Run tests
4. Build or package verification

If a project does not have one of these concerns yet, document the omission explicitly.

## Recommended CI Rules

- Run CI on every pull request.
- Run CI on pushes to the default branch.
- Fail fast on broken lint, test, or build steps.
- Keep CI runtime practical so contributors do not bypass it.
- Cache dependencies only when the cache strategy is stable and understandable.
- Make required checks branch protection rules where possible.

## Minimum CD Pipeline

CD should be designed around the actual release model of the project.
Use the smallest safe setup that matches the product.

Typical stages are:

1. Build artifact or release bundle
2. Run final verification
3. Publish artifact or deploy
4. Confirm release result

## Environment Strategy

Use environment separation when the project has deployment targets.

- `dev`
  - For internal validation and early integration.
- `staging`
  - For release candidate verification.
- `production`
  - For the live release target.

Not every project needs all environments, but the meaning of each environment must be documented.

## Secrets And Configuration

- Never hard-code secrets in workflows.
- Store secrets in the CI platform's secret manager.
- Keep non-secret configuration versioned in the repository when possible.
- Document required variables in an example file or setup guide.
- Rotate credentials when ownership or exposure risk changes.

## Branch And Release Integration

- CI should gate merges into protected branches.
- CD behavior should depend on branch or tag policy.
- Use tags for formal releases when the project version matters.
- Do not deploy from ad hoc local state.

## Examples

### Pull Request CI

- Trigger on pull requests to `main`
- Install dependencies
- Run lint
- Run test
- Run build

### Tag-Based Release

- Trigger on tag push such as `v1.2.0`
- Build release artifact
- Publish package or image
- Create release notes

### Default Branch Deployment

- Trigger on merge to `main`
- Run full CI
- Deploy automatically to a non-production environment
- Promote to production through an approval step if needed

## When To Keep It Simple

Prefer a small pipeline when:

- The project is new and still changing rapidly
- The team is small
- Release frequency is low
- The cost of workflow maintenance is higher than the current risk

## When To Expand It

Add more stages or controls when:

- Releases affect customers directly
- Rollback is expensive
- Security or compliance requirements exist
- Multiple deploy targets must be coordinated
- Large teams need stronger merge protection

## Template Rule

Projects based on this repository should start with:

- One CI workflow for pull requests and default branch validation
- One CD workflow only if the release path is already defined
- Clear documentation of triggers, required secrets, and release conditions
