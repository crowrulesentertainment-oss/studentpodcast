# CrowRules Student Podcast Hub

**One company. One universe.**  
A school-focused podcasting and media-education initiative from CrowRules Entertainment.

The Student Podcast Hub is being developed for middle-school/junior-high and high-school learning environments. It is intended to support podcasting education, classroom projects, clubs, audio/video production skills, and teacher-guided portfolios.

## Current status

**Foundation / planning release — not open for student enrollment.**

This repository currently contains a public information-site scaffold and planning documentation. It does not provide student accounts, collect student information, accept recordings, or publish student work.

## Safety-first architecture

- Separate application and data environment from the main CrowRules Podcasting platform.
- Separate Supabase project for any future student data. Do not reuse the production Podcasting project.
- No student-facing authentication or data collection until school agreements, privacy review, authorization, and security testing are complete.
- Private-by-default student work; public publishing disabled unless a future approved workflow is implemented.
- School-scoped access for teachers and administrators.
- No advertising, sale of student data, behavioral profiling, or model training on student work.

## Planned learning environments

- Middle School / Junior High
- High School
- Teacher workspace
- School administration workspace
- Podcasting Academy and guided lessons
- Clubs, categories, assignments, and project portfolios
- Private production studio
- Teacher-reviewed publishing workflow (future phase)

## Repository map

- `index.html` — public information landing page
- `assets/css/site.css` — responsive visual system
- `docs/SAFETY-ARCHITECTURE.md` — safety and access principles
- `docs/ROADMAP.md` — phased development plan
- `docs/ECOSYSTEM-INTEGRATION.md` — controlled connection to CrowRules Podcasting

## Development principles

1. Build the privacy and authorization model before student features.
2. Use fictional test accounts and synthetic data during development.
3. Never place Supabase service-role keys, secrets, or private credentials in GitHub Pages.
4. Enforce permissions on trusted server-side services and database policies—not only in browser code.
5. Do not treat a static website or hidden navigation as an access-control boundary.
6. Obtain school/legal review before handling real student records, accounts, or recordings.

## Deployment

The site is a static HTML/CSS landing page and can be hosted with GitHub Pages. Enable Pages in the repository settings and select the `main` branch with the root folder as the publishing source.

The public site is informational only. Do not add student sign-up, upload, messaging, or profile functionality until the later security and school-approval milestones are complete.

## Contact

CrowRules Entertainment  
crowrulesentertainment@gmail.com
