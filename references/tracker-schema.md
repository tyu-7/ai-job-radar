# Tracker schema

Read this reference before creating or updating a job tracker.

## AI-maintained fields

| Field | Purpose |
| --- | --- |
| `dedupe_key` | Normalized direct URL or fallback fingerprint |
| `first_seen` / `last_verified` | Discovery and latest verification dates |
| `priority` / `match_score` | Result of the current rubric |
| `company` / `role` / `business` / `location` | Structured job identity |
| `cohort` / `published_at` / `deadline` | Recruiting eligibility and timing |
| `source_url` / `source_type` | Audit trail |
| `match_reason` / `main_risk` | Decision explanation |
| `jd_keywords` / `likely_questions` | Resume and interview preparation inputs |
| `last_change` / `updated_at` | Change log |

## User-maintained fields

Never overwrite these fields during an automated run:

- `status`
- `applied_at`
- `resume_version`
- `user_notes`

## Deduplication

1. Normalize the job detail URL. Remove obvious analytics parameters such as campaign tags, but preserve job IDs, referral codes required to resolve the role, and meaningful query parameters.
2. Compare normalized URLs.
3. If no reliable direct URL exists, compare a case- and whitespace-normalized `company | role | location` fingerprint.
4. When an existing role changes, update the same row and describe the change. Do not add a new row merely because the JD wording changed.

## Status values

Recommended user statuses: `To review`, `Plan to apply`, `Applied`, `Assessment`, `Interview`, `Offer`, `Rejected`, `Paused`, and `Closed`.

The included workbook uses fictional sample rows and can be cleared before private use.
