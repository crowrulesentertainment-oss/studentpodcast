# CrowRules Podcasting Ecosystem Integration

## Goal

Connect the Student Podcast Hub to the broader CrowRules Podcasting ecosystem without merging student identities, records, permissions, or private content into the general platform.

## Proposed relationship

- CrowRules Podcasting remains the general creator/listener platform.
- CrowRules Academy remains the general learning resource.
- Student Podcast Hub is a separate school-focused application.
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

- Do not connect the Student Hub to the existing production Podcasting database.
- Do not reuse general creator/listener roles as student permissions.
- Do not pass student identifiers, email addresses, school membership, grades, submissions, or recordings to the general platform.
- Do not embed general-platform features that expose public community, messaging, discovery, or creator functionality to student accounts.
- Do not place secrets or privileged API keys in static website code.

## Future integration pattern

If a technical integration is later approved, prefer a narrow server-to-server interface that exposes only reviewed educational content. Use explicit allowlists, short-lived credentials, logging, rate limits, and a documented data contract. A separate identity boundary is preferred; shared sign-in must not imply shared authorization.

## Review gate

Every integration must have:
1. A documented educational purpose.
2. A data-flow diagram and field-level inventory.
3. School and privacy approval where required.
4. Security review and negative tests.
5. A way to disable the integration without disrupting student access to private work.
