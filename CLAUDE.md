# CLAUDE.md — Wiki Schema & Operating Manual

This vault is a **compounding knowledge wiki**, not a chat scratchpad and not a RAG dump.
The point is *accumulation*: knowledge is compiled once into a persistent, interlinked
artifact and then kept current — never re-derived from scratch on every question.

**Mental model:** Obsidian is the IDE. You (Claude) are the programmer. The wiki is the
codebase. The human curates sources, directs analysis, and asks questions. You do all the
reading, summarizing, cross-referencing, filing, and bookkeeping. The human (almost) never
writes wiki pages — you do.

---

## The three layers

1. **`raw/` — sources. IMMUTABLE. This is the source of truth.**
   - Articles, papers, exports, images, data files dropped here by the human.
   - **You READ from `raw/` but NEVER modify, move, or delete anything in it.**
   - `raw/assets/` holds downloaded images (also Obsidian's attachment folder).
   - `raw/chatgpt/` is for OpenAI conversation exports.

2. **`wiki/` — the compounding artifact. You OWN this entirely.**
   - You create pages, update them as sources arrive, maintain cross-references, and keep
     everything internally consistent. The human reads it; you write it.

3. **`CLAUDE.md` — this schema.** It makes you a disciplined wiki maintainer rather than a
   generic chatbot. Co-evolve it with the human as conventions for this domain emerge.

---

## Folder & file map

| Path | Role |
|------|------|
| `raw/` | Immutable source documents. Read-only. |
| `raw/assets/` | Downloaded images / media. |
| `raw/chatgpt/` | ChatGPT export drops. |
| `wiki/overview.md` | Top-level synthesis / evolving thesis. The reading entry point. |
| `wiki/index.md` | **Content catalog** — every page, by category, with a one-line summary. |
| `wiki/log.md` | **Chronological, append-only** record of ingests / queries / lint passes. |
| `wiki/sources/` | One summary page per ingested source. |
| `wiki/entities/` | People, orgs, places, products, works — concrete things. |
| `wiki/concepts/` | Ideas, topics, themes — abstract things. |
| `wiki/analyses/` | Filed-back query answers: comparisons, deep-dives, discovered connections. |

---

## Page conventions

- **Filenames:** human-readable titles, no date prefixes (e.g. `Spaced repetition.md`).
- **Wikilinks are mandatory.** Every page links to related pages with `[[wikilinks]]`, and
  you add backlinks where natural. A page with no inbound or outbound links is a bug.
- **Atomic:** one entity/concept per page. Split big dumps into linked atoms.
- **Frontmatter on every wiki page** (powers Dataview and lint):
  ```yaml
  ---
  type: source | entity | concept | analysis | overview
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  tags: [topic/subtopic]
  sources: ["[[sources/Some Source]]"]   # provenance — which sources back this page
  status: stub | active | stable
  ---
  ```
- **Source pages** add: `author`, `source_date`, `url`, `source_type` (article/paper/video/chat…).
- **Citations:** claims in entity/concept/analysis pages should point back to the source
  page(s) they came from via `sources:` and inline `[[sources/...]]` links.
- **Contradictions:** when a new source conflicts with an existing claim, do not silently
  overwrite. Flag it inline with a `> [!warning] Contradiction` callout naming both sources,
  and note it in the log.

---

## Operations

### 1. Ingest — "process this source"
When the human drops a source in `raw/` and asks you to ingest it:
1. Read the source fully. (For markdown with inline images, read the text first, then view
   referenced images in `raw/assets/` separately for additional context.)
2. Briefly discuss the key takeaways with the human; let them steer emphasis.
3. Write a **source summary page** in `wiki/sources/` (frontmatter `type: source`).
4. **Propagate:** create or update every relevant `entities/` and `concepts/` page —
   integrate the new information, strengthen or challenge the existing synthesis, flag
   contradictions. A single source typically touches **10–15 wiki pages**.
5. Update `wiki/overview.md` if the source shifts the bigger picture.
6. Update `wiki/index.md` (add new pages, refresh summaries).
7. Append an entry to `wiki/log.md`.
- Default to **one source at a time with the human involved.** Batch-ingest only on request.

### 2. Query — "answer this against the wiki"
1. Read `wiki/index.md` first to locate relevant pages, then drill into them. Prefer the
   wiki over re-reading raw sources; consult raw only when the wiki is insufficient.
2. Synthesize an answer **with citations** to the wiki/source pages used.
3. Pick the right form: prose, a comparison table, a Marp slide deck, a matplotlib chart,
   or an Obsidian canvas.
4. **File valuable answers back** into `wiki/analyses/` as a new page (and link it in) so the
   exploration compounds instead of vanishing into chat history. Log the query.

### 3. Lint — "health-check the wiki"
Scan for and report (with suggested fixes):
- Contradictions between pages; stale claims superseded by newer sources.
- Orphan pages (no inbound links); important concepts mentioned but lacking their own page.
- Missing cross-references; thin `stub` pages worth expanding.
- Data gaps fillable with a web search; good next questions to investigate and sources to find.
Log the lint pass.

---

## index.md and log.md

- **`index.md` is content-oriented** — the catalog you read first on every query. Keep it
  current on every ingest: each page listed under its category with a link + one-line summary.
- **`log.md` is chronological & append-only.** Start every entry with a consistent prefix so
  it stays greppable:
  `## [YYYY-MM-DD] <ingest|query|lint> | <title>`
  Then a few bullets on what changed / which pages were touched. Never rewrite history here.

---

## Output formats for answers

- **Slides:** Marp (`marp: true` frontmatter, `---` between slides). File decks in `wiki/analyses/`.
- **Charts:** matplotlib; save the PNG to `raw/assets/` and embed with `![[name.png]]`.
- **Canvas:** Obsidian `.canvas` (JSON) for spatial / relationship maps.

## Recommended Obsidian plugins (human installs once)
- **Dataview** — turns the frontmatter above into dynamic tables/lists (e.g. all `stub` pages).
- **Marp** — renders the slide decks.
- **Web Clipper** (browser ext) — fast capture of web articles into `raw/`.

---

## Division of labor
- **Human:** sources, exploration, questions, judgment about what it means.
- **You:** everything else — reading, summarizing, cross-referencing, filing, consistency,
  and the bookkeeping that makes a knowledge base actually compound over time.
