---
name: implement
description: Implements features from ticket or GitHub issue descriptions using a deterministic delivery harness, clean code practices, and strong test coverage. Use when user asks to implement a feature from an issue/ticket, references acceptance criteria, wants code + tests + validation gates, or requests a done definition with test/lint/typecheck/build checks and 12factor alignment.
---

# Implement Skill

## Quick start

Use this skill when the user provides a ticket/issue and expects end-to-end implementation with quality gates.

Minimal flow:
- Extract scope and acceptance criteria from the ticket.
- Implement in small slices using pure functions where practical.
- Add or update tests that prove expected behavior and edge cases.
- Run done gates: tests, linter, typecheck, build.
- Fix easy warnings and regressions before marking complete.

Done means all required gates pass with no errors.

## Workflows

### 1. Ticket-to-plan workflow

- Parse the issue into: objective, constraints, acceptance criteria, non-goals.
- Identify touched modules and risk areas.
- Define a small implementation sequence that keeps behavior stable.
- Translate acceptance criteria into executable tests first when possible.

### 2. Implementation workflow

- Prefer small, composable units and pure functions for domain logic.
- Isolate side effects (I/O, network, DB, time, randomness) behind boundaries.
- Keep naming intent-revealing and functions focused.
- Avoid broad refactors unless required by acceptance criteria.
- Add succinct comments only where intent is not obvious from code.

### 3. Quality harness workflow

- Run and pass all project gates before completion:
	- tests
	- lint
	- typecheck
	- build
- Treat gate failures as blocking.
- Fix easy-to-fix warnings in changed areas where safe.
- Ensure tests cover happy path, edge cases, and regression scenarios tied to the issue.

### 4. 12factor alignment workflow

- Apply relevant Twelve-Factor rules from [../12factor/SKILL.md](../12factor/SKILL.md).
- Enforce config in environment, not hardcoded deploy values.
- Keep services stateless where applicable; push state to backing services.
- Preserve build/release/run separation and consistent dev-prod behavior.

## Delivery checklist

- [ ] Acceptance criteria implemented exactly.
- [ ] Clean code structure preserved or improved.
- [ ] Pure functions used for core logic where practical.
- [ ] Tests added/updated with meaningful assertions.
- [ ] tests pass.
- [ ] lint passes.
- [ ] typecheck passes.
- [ ] build passes.
- [ ] Easy warnings in changed code resolved or documented.
- [ ] 12factor implications reviewed for touched components.
- [ ] Do NOT push until all checklist items above are complete and all gates pass.

## Output format

When reporting completion:
- List implemented acceptance criteria.
- List files changed and why.
- Summarize tests added/updated.
- Report gate results for tests/lint/typecheck/build.
- Note any non-blocking warnings intentionally deferred.
