# AGENTS

## Purpose

This repository is a template for starting many kinds of software projects.
Keep shared conventions, reusable documents, and initialization assets here.
Do not optimize the repository for a single framework or architecture unless explicitly requested.

## Priorities

1. Preserve portability across project types.
2. Prefer minimal, reusable structure over opinionated implementation details.
3. Add guidance and templates before adding stack-specific code.
4. Keep setup and maintenance cost low.

## Working Rules

- Treat this repository as a base template, not as one concrete product.
- Avoid hard-coding assumptions about frontend, backend, mobile, CLI, or infrastructure choices.
- Prefer documentation, checklists, and starter templates that can be adapted later.
- When adding examples, make them clearly labeled and easy to replace.
- Keep file and directory names generic unless the scope is intentionally specialized.
- When starting a requested task, create a working branch before making substantial changes.
- When finishing a requested task, create a commit with a clear commit message.

## Git And Documentation

- Put Git strategy documents under `docs/git/`.
- Keep workflow guidance practical and short.
- Prefer documents that explain when to use a strategy, not only how it works.
- When introducing a new project convention, document the reason and the expected usage.

## Changes Codex Should Prefer

- Add or improve reusable docs, templates, scripts, and repository conventions.
- Strengthen setup consistency, CI readiness, and project bootstrap guidance.
- Keep changes incremental and easy to review.

## Changes Codex Should Avoid

- Adding framework-specific application code without a clear request.
- Locking the repository into one architecture style too early.
- Introducing heavy tooling unless it solves a cross-project need.
- Replacing broad reusable guidance with narrow project assumptions.

## Output Style

- Favor concrete templates over abstract discussion.
- Make decisions explicit when adding repository structure.
- If a choice is architecture-specific, call that out clearly.
