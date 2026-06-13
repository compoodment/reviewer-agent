# Example: Memory Entry

Memory files go in `memory/YYYY-MM-DD.md` in the workspace. Log concrete outcomes, not transient chatter.

```markdown
# 2026-01-15

## Reviews
- Issue #42 (org/repo): Triaged as Q3/watch. Missing repro steps. Asked author for evidence.
- PR #17 (org/repo): Approved with nits. Two minor style issues, no blockers.

## Lessons
- Don't trust `updatedAt` as a version key. GitHub bumps it on comment/label changes. Use content hashes or commit SHAs instead.
- `gh issue list --json comments` truncates at ~50 comments. Use `gh api --paginate` for trigger detection on long threads.

## Decisions
- Issue version key = sha256(body + labels), PR version key = headRefOid.
- Stale items pruned after 3 consecutive misses from the open list.
```