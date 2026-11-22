# Student Hub Safety Architecture

**Status:** Design requirements — implementation and legal review required before real student use.

## 1. Safety boundary

The Student Hub must be a separate application and data environment from the general CrowRules Podcasting platform.

- Create a dedicated Supabase project for future Student Hub data.
- Do not add student records to the existing CrowRules Podcasting Supabase project.
- Do not expose service-role keys or other secrets in browser code, GitHub Pages, or this repository.
- Main-platform integration must be limited to approved educational content and explicitly designed services.
- Do not share student identity, school records, submissions, recordings, grades, or private project metadata with the general platform.

## 2. Roles and least privilege

Planned roles (not yet implemented):

| Role | Intended access |
|---|---|
| Student | Own approved class activities and own private projects |
| Teacher | Students and projects in assigned classes |
| School administrator | Authorized school-level administration |
| CrowRules platform administrator | Limited operational access under documented authorization |
| Guardian | Only the access and consent functions approved by the school model and applicable law |

Every request must be authorized by trusted server-side logic and database policies. Hiding a page, button, route, or menu item is not authorization.

## 3. School isolation

- Every school-owned record must be associated with a school identifier.
- Class and project access must be checked against the authenticated user's active school membership.
- Teachers must not be able to access classes outside their assignments.
- Students must not be able to enumerate other students or schools.
- Cross-school access tests are release blockers.
- Administrative access must be narrow, logged, reviewed, and revocable.

## 4. Student content and publishing

Default project visibility: **private**.

Planned workflow:
1. Student creates or submits a private project.
2. Authorized teacher reviews the work.
3. A school-authorized representative approves publication where applicable.
4. Required parent/guardian and participant permissions are verified.
5. Copyright, privacy, identifying details, and media rights are checked.
6. An authorized publishing service releases only the approved version.

Public publishing must remain disabled until the workflow, consent evidence, permissions, audit trail, and takedown process are implemented and tested. Students must not be able to self-approve public publication.

## 5. Communication and interaction

For the initial release:
- No public student directory.
- No open direct messaging.
- No unrestricted comments or live chat.
- No student-to-student contact discovery.
- No location sharing.
- No public student profiles.

Any future collaboration tools require educator oversight, abuse reporting, moderation, and documented response procedures.

## 6. Data minimization

Collect only the minimum information necessary for an approved educational purpose. Define:
- Data owner and school responsibilities.
- Purpose and lawful basis for each data field.
- Retention period and deletion process.
- Access and correction process.
- Backup lifecycle and deletion limitations.
- Incident response and notification responsibilities.
- Third-party subprocessors and data flows.

Do not sell student information, use it for targeted advertising or behavioral profiling, or use student recordings/submissions to train AI models.

## 7. Development and testing

Until approval:
- Use fictional students, fictional schools, and synthetic content only.
- Do not invite real students to the development site.
- Do not collect real student names, email addresses, birth dates, grades, recordings, or parent details.
- Test authentication, role boundaries, school isolation, storage access, exports, deletion, and audit logs.
- Review all third-party services before enabling them.

## 8. Compliance review

Before a school pilot, obtain qualified review of the actual service model, school agreements, consent flows, privacy notice, data processing terms, retention rules, and incident response plan. Evaluate applicable requirements including FERPA, COPPA, Washington student privacy laws, and school/district policies.

This document is a product-design checklist, not legal advice or a certification of compliance.
