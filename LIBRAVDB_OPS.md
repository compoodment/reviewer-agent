# LIBRAVDB_OPS.md - LibraVDB Rail

Use with `LIBRAVDB_BUGFINDING.md`.

- Vale stays on `memory-core`; never use Vale's laptop profile as a LibraVDB test subject.
- Retired local `Libra` profile stays retired. Do not recreate a local Libra profile, gateway, or `libravdbd` without explicit approval.
- Dicky is the default runtime subject: `ssh dicky`.
- Nyx is fallback/comparison only: `ssh nyx`.

Before claiming host behavior:

```bash
ssh dicky 'bash -lc "openclaw memory status --deep"'
ssh dicky 'bash -lc "openclaw plugins list --json"'
ssh nyx 'bash -lc "openclaw memory status --deep"'
ssh nyx 'bash -lc "openclaw plugins list --json"'
```

Do not restart gateways, edit config, install packages, or mutate Dicky/Nyx without explicit approval.

GitHub on `xDarkicex/openclaw-memory-libravdb`:

- Sign issues, PRs, comments, and reviews with `– Vale`.
- PR titles use Conventional Commits; PR bodies use `## Summary` and `## Verification`/`## Testing`.
- Sanitize public text: no exact user IDs, hostnames, gateway ports, absolute local paths, or chat references.

## Gates

- Upstream gates: `pnpm check`, `npm run test:integration`
- Integration may need `bash scripts/build-daemon.sh`.
- Retrieval/ranking/compaction/config changes need behavior tests and focused docs/design updates.
- Keep plugin and daemon lifecycles separate.
- Do not add install-time daemon bootstrap without documenting security/distribution tradeoffs.

## Review Checklist

1. Re-verify current upstream; downgrade stale claims.
2. Map ordering, daemon/plugin compatibility, generated contracts, and cross-repo dependencies.
3. Read the diff line by line.
4. Prefer behavior tests through public seams.
5. Hit CRLF, delimiters, `NaN`/infinite inputs, empty results, stale contracts.
6. Run the smallest meaningful gate, then required upstream gates.