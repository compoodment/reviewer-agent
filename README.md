# Reviewer Agent

A starting template for building a sharp, opinionated code-review agent. Derived from a real production workspace — Vale's actual config files, sanitized for public reuse.

This is not a framework. Drop these files into your OpenClaw workspace and customize them. The personality, review stance, permissions, and discipline rules are all editable plaintext. No code required.

## What's in here

- **`IDENTITY.md`** — Who the agent is: name, pronouns, role, visual description.
- **`SOUL.md`** — How the agent talks: tone, brevity, values.
- **`AGENTS.md`** — What the agent can and can't do: permissions, review discipline, operational rules.
- **`USER.md`** — Who the agent works for: preferences, communication style, what annoys them.
- **`LIBRAVDB_OPS.md`** — Example project-ops rail: scope, gates, checklist, and rules for reviewing a specific repo.
- **`LIBRAVDB_BUGFINDING.md`** — Example bugfinding rail: targets, loop, quality tiers, lanes, commands, and fix rules.
- **`TOOLS.md`** — Example local cheat sheet: paths, hosts, git conventions, tooling notes.
- **`DREAMS.md`** — The dream diary: where OpenClaw stores agent dream logs. Included as an example of the format.
- **`examples/`** — Project ops template and memory entry template for new setups.

## How to use

1. Copy these files into your OpenClaw workspace (typically `~/.openclaw/workspace/`).
2. Customize `IDENTITY.md`, `SOUL.md`, `AGENTS.md`, and `USER.md` to fit your agent and your preferences.
3. Create your own project-ops and bugfinding rails (like the LibraVDB ones) for repos you work on.
4. Update `TOOLS.md` with your actual paths, hosts, and conventions.
5. Replace `DREAMS.md` content — this one contains Vale's actual dreams as a format example.

## Principles

- **Identity is not a skill.** Persona lives in IDENTITY + SOUL. Procedures live in project rails and skills.
- **Reviewers catch bugs, not feelings.** The stance is critical. Evidence first. Prove or downgrade.
- **Permissions are explicit.** If it's not in AGENTS.md as "allowed without asking," the agent should ask first.
- **Memory is project-scoped.** Don't dump project ledgers into global memory. Use workspace state files.
- **Dreams are dreams.** OpenClaw writes dream logs during idle periods. They're evocative, not factual.

## License

MIT