# Log

Chronological, append-only record of wiki operations. Each entry starts with a consistent
prefix so the log stays greppable:

```
grep "^## \[" log.md | tail -5
```

Entry format: `## [YYYY-MM-DD] <ingest|query|lint> | <title>`

---

## [2026-06-15] setup | Vault initialized
- Created three-layer architecture: `raw/` (immutable sources), `wiki/` (LLM-owned), `CLAUDE.md` (schema).
- Seeded `overview.md`, `index.md`, `log.md`. Set attachment folder to `raw/assets/`.
- Wiki is empty; awaiting first source.
