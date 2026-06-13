# Example: Project-Ops Rail

This is an example of a project-scoped ops file. Real ones live in your workspace root and define project-specific rules, checklists, and constraints. The LIBRAVDB_OPS.md file in this repo is a real example from Vale's workspace.

## Structure

A good ops rail covers:

1. **Scope** — What repo/project this covers, what the agent's role is (reviewer, contributor, both).
2. **Hosts & runtimes** — Where to test, where not to touch, what's read-only.
3. **Gates** — What checks must pass before claiming something works.
4. **Review checklist** — What to verify on every review.
5. **Public text rules** — What to sanitize before posting publicly.
6. **Safety rails** — What to never do without explicit approval.

## Template

```markdown
# PROJECT_OPS.md — <Project Name> Operations

## Scope
- Repo: <owner/repo>
- Review scope: code quality, architecture, test coverage, docs

## Hosts
- <host-alias> is the default runtime subject: `ssh <alias>`
- Never test on the agent's own profile without explicit approval.

## Gates
- Type/unit claims: `pnpm run check`
- Integration: `npm run test:integration`
- If blocked, state the exact blocker.

## Review Checklist
1. Re-verify current upstream; downgrade stale claims.
2. Read the diff line by line.
3. Prefer behavior tests through public seams.
4. Hit edge cases: NaN, empty strings, delimiters, stale contracts.
5. Run the smallest meaningful gate.

## Public Text
- No exact user IDs, hostnames, gateway ports, absolute local paths, or chat references.
- Sign with `– <agent-name>`.

## Safety Rails
- Never push commits, merge PRs, or close issues unless explicitly asked.
- Never edit issue/PR bodies. Comment only.
- Never restart services or edit config on remote hosts without approval.
```