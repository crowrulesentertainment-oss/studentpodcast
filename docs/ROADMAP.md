# Student Podcast Hub Roadmap

The project will advance through gated phases. A later phase must not begin with real student data until the preceding safety, school, and technical requirements have been reviewed.

## Phase 0 — Public concept site (current)

- [x] Establish repository and project identity.
- [x] Publish an informational landing page.
- [x] State clearly that student registration is not open.
- [x] Document initial safety principles.
- [ ] Review content and branding.
- [ ] Enable GitHub Pages after checking repository visibility and publication settings.

## Phase 1 — Partnership and product design

- [ ] Confirm school audience: middle school/junior high and high school.
- [ ] Define pilot model and participating-school responsibilities.
- [ ] Map student, teacher, school administrator, guardian, and platform operations.
- [ ] Define age-appropriate learning pathways.
- [ ] Draft school agreement, privacy notice, consent materials, retention schedule, and incident response.
- [ ] Obtain legal/privacy review and school approval.

**Gate:** No real student information before this phase is approved.

## Phase 2 — Secure technical foundation

- [x] Create the `student_hub` schema in the existing CrowRules Podcasting Supabase project (`cevylpnoexugwgygvtgu`).
- [x] Keep the new schema unexposed and revoke schema access from `anon`, `authenticated`, and `service_role` pending security design.
- [ ] Audit shared Auth/provider implications and decide whether the shared identity boundary is acceptable for the school pilot.
- [ ] Define minimal data model and data classification.
- [ ] Implement authentication with school-approved account provisioning.
- [ ] Implement server-side authorization and restrictive RLS.
- [ ] Implement school and class isolation.
- [ ] Add private storage policies and audit events.
- [ ] Add account lifecycle, access revocation, export, and deletion workflows.
- [ ] Conduct independent security review and negative-access testing.

**Gate:** No real student enrollment before isolation and access-control tests pass. If a school requires separate Auth, storage, backups, or stronger tenant isolation, create a separate Supabase project before pilot.

## Phase 3 — Educator-led learning tools

- [ ] Teacher and school administrator workspaces.
- [ ] Student learning dashboard with minimal profile data.
- [ ] Academy lessons and guided beginner activities.
- [ ] Class assignments and private submissions.
- [ ] Teacher feedback and progress tracking.
- [ ] Accessibility and age-appropriate usability testing.

## Phase 4 — Private production studio

- [ ] Private audio recording and upload.
- [ ] Private video workflows only if specifically approved.
- [ ] Recording consent and participant permissions.
- [ ] Storage limits, scanning, retention, and deletion.
- [ ] Teacher review and moderation tools.
- [ ] No public sharing by default.

## Phase 5 — Controlled publishing (optional)

- [ ] Document school approval authority.
- [ ] Verify required guardian/participant permissions.
- [ ] Review privacy, copyright, music, and third-party rights.
- [ ] Create an approval record and immutable publication audit trail.
- [ ] Publish only approved derivatives to an approved destination.
- [ ] Provide correction, removal, and takedown procedures.

## Phase 6 — Pilot and measured expansion

- [ ] Start with a small school-approved pilot.
- [ ] Use synthetic data in pre-pilot testing.
- [ ] Train educators and designated administrators.
- [ ] Test incident response and account termination.
- [ ] Gather school feedback without unnecessary student tracking.
- [ ] Resolve findings before onboarding another school.

## Out of scope for the initial release

- Student self-registration.
- Public student profiles or directories.
- Open messaging, comments, or live chat.
- Public student podcast feeds.
- Advertising or monetization based on student activity.
- AI training on student content.
- Shared student accounts or data with the general CrowRules Podcasting platform.
