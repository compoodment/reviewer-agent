# LIBRAVDB_BUGFINDING.md - Bugfinding Rail

Use with `LIBRAVDB_OPS.md` for LibraVDB bugfinding, fixes, and PR/issue review.

## Targets

- Repo: `xDarkicex/openclaw-memory-libravdb`
- Main checkout: `/home/computment/openclaw-memory-libravdb`
- Extra checkout: `state/repos/openclaw-memory-libravdb-issue171`
- Runtime proof: Dicky first (`ssh dicky`), Nyx only for fallback/comparison.
- Never test on Vale's laptop profile or recreate the retired local Libra profile.

## Loop

1. Pick one lane and name the behavior/trigger.
2. Read the smallest responsible path.
3. Prove with repro, failing test, trace, source citation, or Dicky/Nyx output.
4. Grade quality, search duplicates, then file an issue or PR.
5. Chat gets only the receipt: link, quality, blockers.

No proof means hypothesis. No upstream action means unfinished.

## Quality

```text
Quality: Q?/5
Name:
Evidence:
Repro:
Impact:
Fix confidence:
Risk:
```

- `Q5 proven`: current upstream, exact trigger, deterministic repro/failing test, clear impact, narrow fix, duplicate search done.
- `Q4 sharp`: current upstream, strong proof, clear impact, likely fix, one uncertainty named.
- `Q3 promising`: plausible with partial proof; needs runtime/test confirmation.
- `Q2 smoke`: smell or stale report; hunt only.
- `Q1 noise`: vibes; do not file, patch, or request changes.

Meaning:

- Every new/changed PR and issue gets a visible Vale outcome.
- Quality is the verdict, not the posting threshold.
- `Q4+` means actionable upstream work: request changes, file/fix, or propose a concrete next step.
- `Q1-Q3` still gets posted as triage/review, with proof gaps and next evidence named.
- Security claim: `Q5` plus actor, access, gain, and concrete impact.
- Exact `@vale review`: always post a visible latest-head review outcome, even if no actionable findings remain.

Downgrade stale upstream, retired local-state dependence, Dicky/Nyx contradiction, hand-wavy impact, or overbroad fixes.

## Lanes

- Lifecycle: readiness, daemon death, CLI/gateway drift, startup/shutdown races, stale sockets/pids, plugin/daemon version skew, install/update lifecycle blur.
- Retrieval/ranking: empty results, duplicate IDs, tie ordering, scope leaks, recency/relevance mistakes, compaction context assembly, unvalidated rank changes.
- Boundaries: `NaN`, `Infinity`, negative/zero/huge numbers, empty strings/arrays, malformed embeddings, CRLF, delimiters, corrupt state, missing dirs, permission errors.
- Contracts/config: docs/schema/code drift, stale generated contracts, accepted-but-ignored config, default mismatch, CLI/runtime mismatch.
- Security: threat-model first; separate exposure, privilege escalation, data leak, DoS, and ugly-but-local failure.

## Commands

Read-only Dicky checks:

```bash
ssh dicky 'bash -lc "openclaw memory status --deep"'
ssh dicky 'bash -lc "openclaw plugins list --json"'
ssh dicky 'bash -lc "openclaw --version || true"'
ssh dicky 'bash -lc "journalctl --user -u libravdbd --no-pager -n 120 2>/dev/null || true"'
```

Local orientation:

```bash
cd /home/computment/openclaw-memory-libravdb
git status --short --branch
git fetch --all --prune
rg "TODO|FIXME|throw new Error|catch \\(|setTimeout|spawn|libravdbd|markdown|compact|rank|score|NaN|Infinity" src test scripts docs
```

Read source, not generated `dist/`, unless checking packaging/publish behavior.

## Gates

- Type/unit/review claims: `pnpm run check`
- Plugin packaging/runtime: `pnpm run plugin:ci`
- Daemon/host flow: `npm run test:integration`
- Daemon binary: `bash scripts/build-daemon.sh`

If blocked, state the exact blocker.

## Fix/Review Rules

- Reproduce first unless current tests/types already prove it.
- Patch the narrowest responsible layer.
- Do not hide errors behind success-looking fallbacks.
- Keep plugin lifecycle and daemon lifecycle separate.
- Prefer behavior tests through public seams.
- Update docs for visible behavior/config changes.
- Re-read the diff before publishing.

Smells: source-grep tests, docs-only runtime claims, broad `catch`, hardcoded delimiter offsets, unbounded retry/queue, ignored config, untested compatibility, daemon bootstrap hidden in package install.

## Public Text

Include quality score, evidence/proof gaps, actionability, verification limits, and `– Vale`. For bug reports, also include sanitized environment, repro, observed, expected, and scope/layer.

Never include exact user IDs, hostnames, gateway ports, absolute local paths, chat references, or speculative severity.

Stop or downgrade if stale, duplicate, mere misconfiguration, no concrete impact, or blocked by unapproved writes/restarts.