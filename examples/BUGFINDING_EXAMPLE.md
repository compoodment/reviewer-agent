# Example: Bugfinding Rail

This is an example of a bugfinding rail — a structured approach to finding, grading, and reporting bugs. The LIBRAVDB_BUGFINDING.md file in this repo is a real example from Vale's workspace.

## Structure

A good bugfinding rail covers:

1. **Targets** — What repo, what checkout paths, where to test.
2. **Loop** — The step-by-step process for finding and proving bugs.
3. **Quality tiers** — A grading system that separates proven bugs from smells and vibes.
4. **Lanes** — Categories of bugs to hunt for (lifecycle, boundaries, contracts, security).
5. **Commands** — Read-only checks that prove claims without mutating anything.
6. **Fix/Review rules** — What to do after you find something.
7. **Public text rules** — What to sanitize before filing publicly.

## Quality Tier Template

```text
Quality: Q?/5
Name:
Evidence:
Repro:
Impact:
Fix confidence:
Risk:
```

- **Q5 proven**: Current upstream, exact trigger, deterministic repro, clear impact, narrow fix, duplicate search done.
- **Q4 sharp**: Current upstream, strong proof, clear impact, likely fix, one uncertainty named.
- **Q3 promising**: Plausible with partial proof; needs runtime/test confirmation.
- **Q2 smoke**: Smell or stale report; hunt only.
- **Q1 noise**: Vibes; do not file, patch, or request changes.

## Key Discipline

- No proof means hypothesis. No upstream action means unfinished.
- Quality is the verdict, not the posting threshold. Post Q1-Q3 with proof gaps named.
- Security claims need actor, access, gain, and concrete impact — not just "this could be bad."
- Downgrade stale upstream, retired local-state dependence, hand-wavy impact, or overbroad fixes.