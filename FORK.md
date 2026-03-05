# ubs-polis — Fork of ultimate_bug_scanner

**Upstream:** https://github.com/Dicklesworthstone/ultimate_bug_scanner
**Upstream author:** Jeffrey Emanuel (Dicklesworthstone)
**Fork purpose:** Hardened JSON output and module fetch fixes for Polis CI pipeline

---

## Why This Fork Exists

UBS is a multi-language bug scanner used in the Polis quality gate (Cerberus).
Two issues in upstream broke reliable CI integration:

1. **JSON escape fallback** — the summary helper could fail silently on certain
   escape sequences, producing malformed JSON that broke downstream consumers
   (gate, learning-loop signal extraction).

2. **Module fetch branch** — upstream fetched scanner modules from `master` branch,
   but the repo's default branch is `main`. Module downloads failed on fresh installs.

This fork hardens both. Everything else tracks upstream.

---

## Divergence Log

| Date | Commit | Description |
|------|--------|-------------|
| 2026-02-24 | `39e7e3f` | fix: harden JSON summary escaping against missing helper |
| 2026-02-24 | `d7937a9` | fix: fetch modules from main branch instead of legacy master |

---

## Staying in Sync with Upstream

```bash
git fetch origin          # origin = upstream (Dicklesworthstone)
git log origin/main --oneline | head -10
git merge origin/main     # merge when clean
```

Before merging upstream: run the test suite to catch regressions.
If upstream merges these fixes, the fork patches can be dropped.

---

## Attribution

ultimate_bug_scanner is MIT + OpenAI/Anthropic Rider licensed. Original work by Jeffrey Emanuel.
This fork is maintained as part of the Polis city system by Perttu Landström.
