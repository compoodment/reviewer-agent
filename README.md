# Reviewer Agent

A starting template for building a sharp, opinionated code-review agent. Derived from a real production workspace — Vale's actual config files, sanitized for public reuse.

This is not a framework. Drop these files into your OpenClaw workspace and customize them. The personality, review stance, permissions, and discipline rules are all editable plaintext. No code required.

## What's in here

- **`IDENTITY.md`** — Who the agent is: name, pronouns, vibe, visual description, role.
- **`SOUL.md`** — How the agent talks: tone, brevity, core truths.
- **`AGENTS.md`** — What the agent can and can't do: permissions, review discipline, operational rules.
- **`LIBRAVDB_OPS.md`** — Example project-ops rail: scope, hosts, gates, review checklist, public text rules, safety rails.
- **`LIBRAVDB_BUGFINDING.md`** — Example bugfinding rail: targets, loop, quality tiers (Q1–Q5), lanes, commands, and fix/review rules.
- **`examples/`** — Templates for project ops, bugfinding rails, and memory entries.

## How to use

1. Copy these files into your OpenClaw workspace (typically `~/.openclaw/workspace/`).
2. Customize `IDENTITY.md`, `SOUL.md`, and `AGENTS.md` to fit your agent's personality and permissions.
3. Create your own `USER.md` describing who you are, what you care about, and what annoys you.
4. Create your own `TOOLS.md` with your paths, hosts, git conventions, and tooling notes.
5. Create project-ops and bugfinding rails (like the LibraVDB ones) for repos you work on.
6. Add a `DREAMS.md` — OpenClaw writes dream logs during idle periods; the file just needs the header.

## Principles

- **Identity is not a skill.** Persona lives in IDENTITY + SOUL. Procedures live in project rails and skills.
- **Reviewers catch bugs, not feelings.** The stance is critical. Evidence first. Prove or downgrade.
- **Permissions are explicit.** If it's not in AGENTS.md as "allowed without asking," the agent should ask first.
- **Memory is project-scoped.** Don't dump project ledgers into global memory. Use workspace state files.

## License

MIT