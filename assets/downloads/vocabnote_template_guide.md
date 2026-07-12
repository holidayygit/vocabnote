# Vocabnote データ生成ガイド

このファイルをAIに添付し、作りたい単語帳を頼んでください。
例: 「TOEIC頻出単語をこのフォーマットでまとめて」
英語の単語→日本語の意味なら word_language: en / term_language: ja です。

## Example
```json
{
  "app": "vocabnote",
  "schemaVersion": 7,
  "exportedAt": "2026-01-01T00:00:00Z",
  "tagColors": { "TOEIC": "#3b82f6" },
  "tagLanguages": { "TOEIC": { "word_language": "en", "term_language": "ja" } },
  "cards": [
    { "term": "acquire", "tag": "TOEIC", "meaning_term": "獲得する" },
    { "term": "implement", "tag": "TOEIC", "meaning_term": "実施する" }
  ]
}
```

## Rules
- Output JSON only — no explanation, no extra text.
- `app` = "vocabnote", `schemaVersion` = 7, `exportedAt` = any ISO8601 date.
- For every deck: add one entry to `tagColors` and `tagLanguages`. Always set the color to `#3b82f6` (Vocabnote default blue).
- Each card needs only `term`, `tag`, `meaning_term`. Every `tag` must exist in `tagColors`.
- Do NOT add `sync_id`, `sort_order`, `memorized_at`, `reviewed_at`, `review_count`.

## Fields
| Field | Required | Description |
|---|---|---|
| `term` | yes | Word / phrase to learn |
| `tag` | yes | Deck name (must match a `tagColors` key) |
| `meaning_term` | yes | Translation / meaning |
| `meaning_word` | no | Note in the word's language (usually omit) |
| `ipa` | no | Pronunciation (usually omit) |
| `word_language` / `term_language` | no | Set per deck in `tagLanguages` (default `en` / `ja`) |

Language codes: `en` `ja` `es` `fr` `de` `it` `pt` `id` `zh-Hans` `zh-Hant` `ko`
