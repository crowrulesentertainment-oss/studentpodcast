# CrowRules Podcasting Ecosystem Integration

## Goal

Connect the Student Podcast Hub to the broader CrowRules Podcasting ecosystem without merging student identities, records, permissions, or private content into the general platform.

## Proposed relationship

- CrowRules Podcasting remains the general creator/listener platform.
- CrowRules Academy remains the general learning resource.
- Student Podcast Hub is a separate school-focused application using the `student_hub` schema inside the existing CrowRules Podcasting Supabase project.
- Selected Academy lessons may be copied, adapted, or delivered through an approved read-only content integration.
- Student assignments, grades, teacher feedback, identities, and recordings remain in the Student Hub environment.

## Allowed initial connection

The current static landing page links to the public CrowRules Podcasting website. This is navigation only; it does not transfer student data or authenticate users across systems.

General Podcasting resources proposed for educator review:
- Main platform: https://crowrulesentertainment-oss.github.io/podcasting/
- Beginners Guide: https://crowrulesentertainment-oss.github.io/podcasting/beginners-guide/
- Academy: https://crowrulesentertainment-oss.github.io/podcasting/academy/

Before using a resource with students, review it for age suitability, advertising/tracking, embedded third-party content, external links, account requirements, and data collection.

## Integration restrictions

- Keep Student Hub relational tables in `student_hub`; do not use the general platform's `public` tables for student records.
- Treat the shared Supabase project as a shared infrastructure boundary: Auth, Storage, compute, backups, and project settings are not independently isolated by PostgreSQL schema.
- Do not reuse general creator/listener roles as student permissions.
- Do not pass student identifiers, email addresses, school membership, grades, submissions, or recordings to the general platform.
- Do not embed general-platform features that expose public community, messaging, discovery, or creator functionality to student accounts.
- Do not place secrets or privileged API keys in static website code.

## Future integration pattern

If a technical integration is later approved, prefer a narrow server-to-server interface that exposes only reviewed educational content. Use explicit allowlists, short-lived credentials, logging, rate limits, and a documented data contract. A separate identity boundary is preferred. Under the current shared-project decision, Auth is shared; shared sign-in must not imply shared authorization. If independent Auth is required by a school, use a separate Supabase project.

## Review gate

Every integration must have:
1. A documented educational purpose.
2. A data-flow diagram and field-level inventory.
3. School and privacy approval where required.
4. Security review and negative tests.
5. A way to disable the integration without disrupting student access to private work.
