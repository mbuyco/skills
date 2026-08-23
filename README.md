<div align="center">
  <img src="assets/logo.png" alt="Custom Agent Skills Logo"/>
</div>

# Custom Agent Skills

A collection of custom agent skills crafted for coding agent CLI tools. Each skill provides specialized instructions and workflows for specific tasks.

## Skills Included

| Skill | Description |
|-------|-------------|
| [codebase-explorer](./skills/codebase-explorer) | Explore unfamiliar codebases and report modules, data flow, and gotchas |
| [software-engineering-workflow](./skills/software-engineering-workflow) | Plan and implement software changes with requirements discovery, pragmatic design, and lightweight validation |

## Installation

Skills are automatically available when placed in:
- `skills/` (project-local, shared across supported agent harnesses)
- `~/.config/opencode/skills/` (OpenCode global)
- `.opencode/skills/` (OpenCode project-specific)

## Usage

Invoke a skill by name when you need its specialized capabilities:

```
/skill codebase-explorer
```

Or let your agent harness auto-select the appropriate skill based on your task description.

## Supported Agent Harnesses

| Tool | Notes |
|------|-------|
| OpenCode | Native skill support via `.opencode/skills/` and `~/.config/opencode/skills/` |
| Claude Code | Can reference `skills/` from project instructions or custom commands |
| Codex CLI | Can load `skills/` via `AGENTS.md` or project configuration |


Each skill contains:
- `SKILL.md` — Instructions and workflow guidance
- Optional: `agents/`, `scripts/`, `references/`, `templates/` directories

---

*Compatible with OpenCode, Claude Code, and Codex CLI.*
