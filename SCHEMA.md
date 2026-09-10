# `datasets/onda-corpus.jsonl` — schema

[JSON Lines](https://jsonlines.org): one JSON object per line, UTF-8, no
enclosing array. Records are grouped by `type` (articles, glossary, reviews,
comparisons, tools, cornerstones) and sorted by `id` within each group, so a
diff between two builds shows exactly what changed.

## Fields

| Field | Type | Always present | Meaning |
|-------|------|----------------|---------|
| `id` | string | yes | Stable slug, unique within a `type`. |
| `type` | string | yes | `article` \| `glossary` \| `review` \| `comparison` \| `tool` \| `cornerstone`. |
| `language` | string | yes | `en` (English is the source of truth; localized pages live on the site). |
| `url` | string | yes | Canonical page URL on onda-life.com. **Use this as the attribution link.** |
| `title` | string | yes | Human title / headline. |
| `description` | string | yes | One–two sentence summary. |
| `body` | string | yes | Full text. Articles/glossary/reviews/comparisons carry their markdown body; tools and cornerstones carry a composed summary + Q&A. |
| `wordCount` | number | yes | Word count of `body`. |
| `author` | object | yes | `{ name, url }` — the editorial author. |
| `category` | string | no | Editorial category (articles, glossary, reviews, comparisons, tools). |
| `keywords` | string[] | no | Topic keywords (cornerstones: the schema.org `about` terms). |
| `datePublished` | string | no | ISO date (articles, reviews, comparisons). |
| `dateModified` | string | no | ISO date (articles, reviews, comparisons). |
| `relatedSlugs` | string[] | no | Related record ids (articles, reviews). |

## Example

```json
{"id":"apple-watch-hrv-biofeedback","type":"cornerstone","language":"en","url":"https://onda-life.com/apple-watch-hrv-biofeedback","title":"HRV Biofeedback on Apple Watch: How It Works","description":"…","wordCount":312,"author":{"name":"Yakiv","url":"https://www.linkedin.com/in/yamius"},"body":"…"}
```

## Notes

- No personal data: records are ONDA's own editorial content (articles,
  glossary, first-party product reviews, tools, explainers).
- The file is refreshed from the live site — see
  [`.github/workflows/sync-knowledge.yml`](.github/workflows/sync-knowledge.yml).
- A gzipped sibling (`onda-corpus.jsonl.gz`) is served on the site at
  `https://onda-life.com/datasets/onda-corpus.jsonl.gz`.
