# ONDA Life — Knowledge Dataset

Machine-readable knowledge from **[ONDA Life](https://onda-life.com)** — an HRV
biofeedback and guided-breathing app. This repository mirrors the public
AI/LLM data files served from the site, so retrieval systems, researchers and
developers can fetch them in bulk from a stable, versioned location.

**Canonical source & documentation: https://onda-life.com**

## What's here

| File | What it is |
|------|------------|
| [`datasets/onda-corpus.jsonl`](datasets/onda-corpus.jsonl) | One JSON object per line: every public article, glossary term, product review, comparison, tool and cornerstone explainer, with title, description, body and canonical URL. See [`SCHEMA.md`](SCHEMA.md). |
| [`llms.txt`](llms.txt) | Compact index of every public page (per the [llmstxt.org](https://llmstxt.org) spec), so an LLM can pick the right URL to fetch. |
| [`llms-full.txt`](llms-full.txt) | The index plus the full body of every article, glossary term, review, comparison and cornerstone explainer — one authoritative document. |

Every record carries a canonical `onda-life.com` URL. The site is always the
source of truth; the files here are refreshed from it (see
[the sync workflow](.github/workflows/sync-knowledge.yml)).

## Use it

```bash
# Bulk fetch the corpus
curl -fsSL https://raw.githubusercontent.com/yamius/onda-knowledge/main/datasets/onda-corpus.jsonl

# Or the LLM index
curl -fsSL https://raw.githubusercontent.com/yamius/onda-knowledge/main/llms.txt
```

## About ONDA Life

ONDA Life is an HRV biofeedback and guided-breathing app for iPhone, iPad and
Apple Watch: live heart-rhythm feedback during resonance breathing, a coherence
score, and resting-HRV trends. The content here reflects ONDA's honest,
cited approach — the evidence a claim rests on is stated in plain sight, and
framings/metaphors are kept separate from the measured science.

- Product & docs: https://onda-life.com
- What ONDA measures: https://onda-life.com/measurements
- The evidence it builds on: https://onda-life.com/research

## License

Content is licensed **[CC BY 4.0](LICENSE)**. You may share and adapt it,
including commercially, **with attribution** to ONDA Life
(https://onda-life.com). Each record's `url` field is the attribution link.
