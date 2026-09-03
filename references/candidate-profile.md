# Candidate profile

Read this reference when creating, reviewing, or repairing a candidate profile.

## Required fields

- `graduation_window`: dates or cohort accepted by target graduate roles.
- `role_tiers`: ordered role families with include and exclude keywords.
- `location_order`: preferred cities or regions in ranked groups.
- `industry_order`: preferred industry or company categories.
- `hard_constraints`: conditions that make a role ineligible.
- `risk_preferences`: acceptable trade-offs such as company stage, hours, travel, or relocation.
- `evidence`: candidate skills and experiences that can be defended in an interview.

## Profile rules

1. Store preferences separately from evidence. Interest in a field is not proof of experience.
2. Use generalized evidence summaries; do not put confidential metrics or employer documents in a public profile.
3. Hard constraints are binary eligibility checks. Soft preferences affect ranking only.
4. Rank groups explicitly instead of relying on vague labels such as “good company” or “interesting role.”
5. Keep the public example fictional. Use a private, ignored file for a real candidate profile.

See `../assets/candidate-profile.example.yaml` for a safe example.
