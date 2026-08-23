---
name: software-engineering-workflow
description: Plan and implement software changes with risk-scaled requirements discovery, design, security, performance, and validation. Use for coding tasks; not for simple explanations or code review without changes.
---

# Software Engineering Workflow

Use this skill to make deliberate implementation decisions without turning routine work into process overhead. Scale rigor to the change: keep isolated, low-risk changes lean; increase analysis and verification when a change affects public contracts, data integrity, security, availability, performance, costs, or many users.

## Before Coding

Establish the outcome before changing code. Inspect the relevant code, configuration, tests, and conventions first. Clarify material unknowns about requirements, constraints, success criteria, ownership, compatibility, and operational tradeoffs. Ask the user only when the answer cannot be safely inferred; otherwise state the assumption that guides the work.

Identify the change's risk before choosing the process. Consider the trust boundaries and data sensitivity, public or internal API contracts, failure impact and recovery, expected load and resource limits, dependency or deployment changes, and observability needs. Treat security-sensitive, data-mutating, externally exposed, or high-throughput paths as higher risk; do not impose their full process on a local, reversible fix.

Determine the language, framework, runtime, build/test commands, and available documentation sources. Use available MCP documentation servers when primary documentation or project-specific context would resolve a meaningful uncertainty.

If an applicable agent skill is already installed, use it. For a large or complex unfamiliar codebase, use `codebase-explorer` or an equivalent orientation workflow before writing code. Do not add tooling solely for a small, self-contained change.

## Design and Implementation

Define only the design needed to implement safely: responsibilities, interfaces, state/data flow, failure handling, and the key tradeoffs. Keep module boundaries cohesive and dependencies directed toward stable abstractions. Make contracts explicit at module, API, persistence, and asynchronous boundaries, including validation, error semantics, and compatibility expectations.

Choose patterns because they fit the use case—not to satisfy an abstract architecture. Prefer the simplest design that meets the stated needs; apply KISS and YAGNI, avoid speculative abstraction, and preserve local conventions unless change is justified. Introduce indirection when it isolates a genuine variation, external dependency, lifecycle, or policy; otherwise keep the behavior direct and local.

Write for the next maintainer. Use intention-revealing names, small cohesive functions and types, and control flow that makes the happy path and failure paths apparent. Remove duplication that would make future changes diverge, but do not hide simple logic behind premature helpers. Comment on non-obvious rationale, constraints, or tradeoffs—not on what readable code already says.

For untrusted or sensitive flows, validate input at the boundary, enforce authorization where the protected operation occurs, use safe parsing and parameterization, minimize sensitive-data exposure in storage and logs, and keep secrets out of source and diagnostics. Consider abuse cases and failure modes in proportion to the exposure; use established project controls rather than inventing security mechanisms.

For performance- or scale-sensitive work, define the relevant workload and resource constraint before optimizing. Avoid obvious hot-path waste, unbounded work, resource leaks, and accidental repeated I/O. Measure or profile before making non-trivial optimizations when practical, then choose appropriate limits, batching, indexing, caching, concurrency, or backpressure while preserving correctness and operational visibility.

When practical, first implement or prototype the core logic in one focused file. Use it to validate the algorithm, behavior, and edge cases before distributing the change across the production codebase. Then integrate it cleanly, keeping changes small and cohesive. Skip the standalone step only when the requested change is inherently configuration-only, tightly coupled to existing interfaces, or a prototype would add no validation value; state why.

## Verify and Hand Off

Run the narrowest meaningful checks first, then the relevant project checks when proportionate. Validate expected behavior and important boundary, failure, and regression cases rather than only formatting or compilation. Choose unit, integration, contract, end-to-end, security, migration, and performance checks according to the changed boundary and risk; do not add ceremonial coverage that cannot detect a plausible failure.

For externally visible, persistent, or operationally significant changes, verify backward compatibility and safe failure behavior. Include rollout, migration, monitoring, alerting, rate-limit, rollback, or recovery considerations when they are needed to operate the change safely.

Report what changed, the design choice that mattered, assumptions made, and verification performed. Call out remaining risks, unverified conditions, or follow-up work honestly.
