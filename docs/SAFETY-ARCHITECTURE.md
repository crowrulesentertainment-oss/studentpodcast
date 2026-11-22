# Student Hub Safety Architecture

**Status:** Design requirements — implementation and legal review required before real student use.

## 1. Safety boundary

The Student Hub must be a separate application and data environment from the general CrowRules Podcasting platform.

- Use the existing CrowRules Podcasting Supabase project (`cevylpnoexugwgygvtgu`) and keep Student Hub relational data in the dedicated `student_hub` PostgreSQL schema.
- Do not create Student Hub tables in `public` or reuse existing Podcasting tables for student records.
- The `student_hub` schema has been created but contains no tables. It is not exposed through the Data API, and `anon`, `authenticated`, and `service_role` currently have no schema `USAGE` privilege.
- Do not add broad schema/table grants or expose `student_hub` in Supabase API settings until the complete access model and RLS policies have been reviewed.
- This schema boundary is logical isolation only. The project still shares Supabase Auth (`auth.users` and provider configuration), Storage service, compute, backups, and project-level settings with CrowRules Podcasting. Do not describe it as a separate tenant or equivalent to a separate project.
- If school requirements demand isolated authentication, independent provider settings, separate backups, or a stronger tenant boundary, move the Student Hub to a separate Supabase project before onboarding students.
- Do not expose service-role keys or other secrets in browser code, GitHub Pages, or this repository.
- Main-platform integration must be limited to approved educational content and explicitly designed services.
- Do not share student identity, school records, submissions, recordings, grades, or private project metadata with the general platform.

## 2. Shared Supabase services and identity

- Student Hub sign-in would use the same Supabase Auth project and `auth.users` pool unless the architecture is changed to a separate project.
- Do not automatically grant student users access to the general CrowRules Podcasting application. Authorization must be based on explicit Student Hub enrollment and school membership records, not merely a valid Supabase session.
- Do not use user-editable `user_metadata` for roles or authorization. Use trusted server-managed membership records and carefully controlled authorization claims where needed.
- Review existing OAuth providers before any student login is enabled. General creator sign-in providers must not automatically become student sign-in methods.
- Any future media storage must use a dedicated private Student Hub bucket with restrictive Storage policies, separate from general Podcasting media.

## 3. Roles and least privilege

Planned roles (not yet implemented):

| Role | Intended access |
|---|---|
| Student | Own approved class activities and own private projects |
| Teacher | Students and projects in assigned classes |
| School administrator | Authorized school-level administration |
| CrowRules platform administrator | Limited operational access under documented authorization |
| Guardian | Only the access and consent functions approved by the school model and applicable law |

Every request must be authorized by trusted server-side logic and database policies. Hiding a page, button, route, or menu item is not authorization.

## 4. School isolation

- Every school-owned record must be associated with a school identifier.
- Class and project access must be checked against the authenticated user's active school membership.
- Teachers must not be able to access classes outside their assignments.
- Students must not be able to enumerate other students or schools.
- Cross-school access tests are release blockers.
- Administrative access must be narrow, logged, reviewed, and revocable.

## 5. Student content and publishing

Default project visibility: **private**.

Planned workflow:
1. Student creates or submits a private project.
2. Authorized teacher reviews the work.
3. A school-authorized representative approves publication where applicable.
4. Required parent/guardian and participant permissions are verified.
5. Copyright, privacy, identifying details, and media rights are checked.
6. An authorized publishing service releases only the approved version.

Public publishing must remain disabled until the workflow, consent evidence, permissions, audit trail, and takedown process are implemented and tested. Students must not be able to self-approve public publication.

## 6. Communication and interaction

For the initial release:
- No public student directory.
- No open direct messaging.
- No unrestricted comments or live chat.
- No student-to-student contact discovery.
- No location sharing.
- No public student profiles.

Any future collaboration tools require educator oversight, abuse reporting, moderation, and documented response procedures.

## 7. Data minimization

Collect only the minimum information necessary for an approved educational purpose. Define:
- Data owner and school responsibilities.
- Purpose and lawful basis for each data field.
- Retention period and deletion process.
- Access and correction process.
- Backup lifecycle and deletion limitations.
- Incident response and notification responsibilities.
- Third-party subprocessors and data flows.

Do not sell student information, use it for targeted advertising or behavioral profiling, or use student recordings/submissions to train AI models.

## 8. Development and testing

Until approval:
- Use fictional students, fictional schools, and synthetic content only.
- Do not invite real students to the development site.
- Do not collect real student names, email addresses, birth dates, grades, recordings, or parent details.
- Test authentication, role boundaries, school isolation, storage access, exports, deletion, and audit logs.
- Review all third-party services before enabling them.

## 9. Compliance review

Before a school pilot, obtain qualified review of the actual service model, school agreements, consent flows, privacy notice, data processing terms, retention rules, and incident response plan. Evaluate applicable requirements including FERPA, COPPA, Washington student privacy laws, and school/district policies.

This document is a product-design checklist, not legal advice or a certification of compliance.
