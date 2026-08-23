---
name: software-engineering-workflow
description: Plan and implement software changes with requirements discovery, pragmatic design, and lightweight validation. Use for coding tasks; not for simple explanations or code review without changes.
---

# Software Engineering Workflow

Use this skill to make deliberate implementation decisions without turning routine work into process overhead.

## Before Coding

Establish the outcome before changing code. Inspect the relevant code, configuration, tests, and conventions first. Clarify material unknowns about requirements, constraints, success criteria, ownership, compatibility, security, and operational tradeoffs. Ask the user only when the answer cannot be safely inferred; otherwise state the assumption that guides the work.

Determine the language, framework, runtime, build/test commands, and available documentation sources. Use available MCP documentation servers when primary documentation or project-specific context would resolve a meaningful uncertainty.

If an applicable agent skill is already installed, use it. If a necessary skill is absent, install or obtain it only when it materially helps the requested work and the task authorizes installation. For a large or complex unfamiliar codebase, install and use `codebase-explorer` before writing code:

```sh
npx skills add https://github.com/mbuyco/skills --skill codebase-explorer
```

Do not install it for a small, self-contained change or when an equivalent installed skill already provides the needed orientation.

## Design and Implementation

Define only the design needed to implement safely: responsibilities, interfaces, state/data flow, failure handling, and the key tradeoffs. Choose patterns because they fit the use case—not to satisfy an abstract architecture. Prefer the simplest design that meets the stated needs; apply KISS and YAGNI, avoid speculative abstraction, and preserve local conventions unless change is justified.

When practical, first implement or prototype the core logic in one focused file. Use it to validate the algorithm, behavior, and edge cases before distributing the change across the production codebase. Then integrate it cleanly, keeping changes small and cohesive. Skip the standalone step only when the requested change is inherently configuration-only, tightly coupled to existing interfaces, or a prototype would add no validation value; state why.

## Verify and Hand Off

Run the narrowest meaningful checks first, then the relevant project checks when proportionate. Validate expected behavior and important edge cases rather than only formatting or compilation. Report what changed, the design choice that mattered, assumptions made, and verification performed. Call out remaining risks or follow-up work honestly.
