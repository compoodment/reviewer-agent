# TOOLS.md — Local Cheat Sheet

Environment-specific notes for the agent's setup. Replace with your own paths, hosts, and conventions.

## Paths
- OpenClaw install: `~/.npm-global`
- Workspace: `~/.openclaw/workspace`
- Routine backups: `state/backups/<target-name>/`

## Hosts
- Dicky is a **remote VPS** running its own OpenClaw instance. Config changes happen on Dicky itself via `ssh dicky`.
- Nyx is a Mac Mini running Ubuntu, used as fallback/comparison host via `ssh nyx`.
- **Never create a local profile, workspace, or config for Dicky on this machine.** Dicky's OpenClaw lives on the VPS only.

## Git
- Default identity: `your-name <your-email>`
- Active upstream: `org/repo` (review, audit, test, contribute)
- Use `gh` for GitHub issue/PR state; use an explicitly chosen checkout for builds, tests, diffs, and reproductions.

## Conventions
- **Never `sudo npm install -g`.** User-local prefix at `~/.npm-global`.
- Read-only commands are fine. System-changing commands need explicit approval.
- Backup before editing meaningful files. No ad hoc `.bak-*` files beside live files.
- Do not treat `state/repos/` as disposable backups; it can contain live work checkouts.

## Coding Tools
- Scope: review, audit, test, and contribution for upstream repos
- No `--full-auto` for upstream work

## Memory Search
- Agent uses `memory-core` with local Ollama embeddings.
- Embedding model: `nomic-embed-text`; model store: `~/.ollama/models`.
- Verify with: `systemctl --user status ollama-cuda.service` and a `memory_search` result showing `provider: "ollama"`.

## Web / Exec
- `web_fetch` is available; safe to use for fact-finding and verification during reviews.
- Current exec posture: `security=full`, `ask=off`.