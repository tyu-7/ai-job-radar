---
name: ai-job-radar
description: Find, verify, score, deduplicate, and track graduate or early-career job openings against a configurable candidate profile. Use for recurring job discovery and application prioritization; do not submit applications or invent unavailable job facts.
---

# AI Job Radar

Turn a candidate profile and live job postings into a verified, prioritized action list while preserving the user's application records.

## Inputs

- Candidate profile: target roles, graduation window, location order, preferred industries, hard exclusions, risk tolerance, and evidence-backed skills.
- Existing tracker, when available. Treat it as the source of truth for deduplication and user-maintained status.
- Optional run settings: freshness window, result limit, timezone, and output language.

If the profile is missing consequential information, ask no more than five questions. Use [candidate-profile.md](references/candidate-profile.md) when creating or validating a profile.

## Workflow

1. Read the candidate profile and existing tracker before searching.
2. Search current sources, prioritizing official career pages and direct job URLs. Use reputable job boards only as secondary sources.
3. Confirm graduation eligibility, role type, location, availability, and dates. Mark unavailable facts as `unverified`; never infer them.
4. Reject internships, expired roles, and openings that fail hard constraints unless the user explicitly asks to keep them as watchlist items.
5. Normalize URLs by removing only obvious analytics parameters. Preserve job IDs and other parameters required to identify the opening.
6. Deduplicate by normalized direct URL, then by normalized `company | role | location` fingerprint.
7. Score eligible openings with [scoring-rubric.md](references/scoring-rubric.md). Explain the strongest match and the main risk; do not let the title alone determine fit.
8. Produce the daily brief defined in [output-format.md](references/output-format.md).
9. If updating a tracker, follow [tracker-schema.md](references/tracker-schema.md). Never overwrite user-maintained status, application date, resume version, or notes.

## Reliability and Safety

- Separate verified facts from recommendations and inferences.
- Link to the job detail page rather than a search homepage whenever possible.
- Do not fabricate compensation, dates, duties, eligibility, or links.
- Do not apply, message recruiters, or change external systems without explicit authorization.
- Respect source access rules and avoid bypassing authentication or anti-bot controls.
- For scheduled runs, stop new discovery at the configured cutoff and always return a final brief, even when no suitable roles are found.
- If tracker writing fails, keep the original tracker unchanged and state that the brief was generated without saving updates.

## Output Quality Bar

A useful run is concise, auditable, and actionable: every recommended role has a working or clearly marked unverified source, an eligibility judgment, a transparent score, a deduplication result, and a next action.
