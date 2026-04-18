# OpenCode Config

Personal OpenCode configuration bundle with custom agents, commands, skills, and context files.

## What is included

- `agent/`, `agents/`: agent and subagent definitions
- `command/`, `commands/`: reusable command prompts/workflows
- `context/`: project and core context knowledge
- `skills/`: custom OpenCode skills
- `tool/`: local tool integrations
- `opencode.json`: main OpenCode config

## Custom agents

This config includes role-focused subagents to speed up common engineering tasks:

- `code-reviewer`: security, performance, and maintainability reviews (read-only)
- `researcher`: compares libraries and technical approaches (read-only)
- `refactorer`: safe structural refactors with test-first expectations
- `explainer`: documentation and code explanation support
- `implementer`: feature delivery workflow (research -> plan -> implement -> test)

Agent definitions live in both:

- `agents/` (top-level aliases/entrypoints)
- `agent/subagents/` (category-organized subagent prompts)

Default agent is configured in `opencode.json` as `OpenAgent`.

## Skills

Current bundled skill:

- `skills/feature-development/SKILL.md`: end-to-end feature workflow guidance

Use skills when tasks benefit from structured process and standards.

## Commands and context

- `command/` and `commands/` include reusable slash-command prompts
- `context/core/` contains shared standards, workflows, and system guidance
- `context/project-intelligence/` stores project-specific architecture and decisions

If you plan to collaborate, keep project-specific context versioned in this repo and avoid storing secrets in context files.

## Requirements

- OpenCode CLI
- Bun (if you use local plugin tooling)

## Setup

Clone this repo into your OpenCode config directory:

```bash
git clone https://github.com/mayank-ladva/opencode-config.git ~/.config/opencode
```

If you use Context7 MCP, set your API key:

```bash
export CONTEXT7_API_KEY="your_api_key"
```

Then restart your OpenCode session.

## Notes

- `opencode.json` references `CONTEXT7_API_KEY` via environment variable.
- Do not commit secrets or private tokens into this repo.

## Update workflow

```bash
git add .
git commit -m "update opencode config"
git push
```

## Suggested maintenance

- Review new agent/skill prompts before commit for correctness
- Keep `opencode.json` permissions minimal (least privilege)
- Validate no secrets are introduced before pushing
