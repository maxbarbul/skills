---
name: twelve-factor
description: Applies Twelve-Factor App rules to architecture and implementation decisions for services and web apps. Use when designing new apps/services, reviewing deployment/runtime model, setting config/dependency/logging/process strategy, or when user mentions 12factor, twelve-factor, cloud-native app design, SaaS architecture, stateless processes, env config, or build-release-run.
---

# Twelve-Factor App Skill

## Quick start

Use this skill when user asks to implement, refactor, or architect an app/service with cloud portability and operability.

Twelve-factor target:
- Use declarative setup automation to reduce onboarding and setup cost.
- Keep a clean OS contract for maximum runtime portability.
- Design for cloud deployment and reduced ops coupling.
- Minimize dev/prod divergence to support continuous deployment.
- Scale without major tooling, architecture, or workflow rewrites.
- Apply across any language stack and backing-service mix.

Checklist:
- Identify app boundary and deploy targets using [rules/codebase.md](rules/codebase.md).
- Validate dependency declaration and isolation via [rules/dependencies.md](rules/dependencies.md).
- Move deploy-varying config to env vars using [rules/config.md](rules/config.md).
- Model external systems as attached resources per [rules/backing-services.md](rules/backing-services.md).
- Enforce build, release, run separation from [rules/build-release-run.md](rules/build-release-run.md).
- Verify runtime process behavior with [rules/processes.md](rules/processes.md), [rules/concurrency.md](rules/concurrency.md), and [rules/disposability.md](rules/disposability.md).
- Ensure service exposure and operability using [rules/port-binding.md](rules/port-binding.md), [rules/logs.md](rules/logs.md), [rules/admin-processes.md](rules/admin-processes.md), and [rules/dev-prod-parity.md](rules/dev-prod-parity.md).

## Workflows

### 1. Architecture review workflow

- Determine if request is app-wide architecture or narrow implementation.
- For app-wide architecture, assess all factor rule files in [rules](rules).
- Produce pass/fail findings by factor with concrete code or infra actions.
- Prioritize violations that block deploy portability, stateless scaling, or safe operations.

### 2. Implementation workflow

- Map requested change to impacted factors before coding.
- Apply only relevant factor rules and avoid unrelated rewrites.
- Keep runtime behavior deterministic across dev/staging/prod using [rules/dev-prod-parity.md](rules/dev-prod-parity.md).
- For migrations, scripts, and consoles, enforce one-off process rules from [rules/admin-processes.md](rules/admin-processes.md).

### 3. Delivery checklist workflow

- Config: no secrets or deploy-specific values in code ([rules/config.md](rules/config.md)).
- Processes: stateless/share-nothing, persistence moved to backing services ([rules/processes.md](rules/processes.md)).
- Logs: app writes event stream to stdout/stderr only ([rules/logs.md](rules/logs.md)).
- Releases: immutable release units with rollback path ([rules/build-release-run.md](rules/build-release-run.md)).
- Shutdown/startup: fast boot and graceful termination ([rules/disposability.md](rules/disposability.md)).
