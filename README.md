# VA Foreclosure Advocacy

Public resources, tools, and crisis case management infrastructure for veteran families facing VA mortgage foreclosure.

## What's Here

### Public Resources
- **[index.html](index.html)** — Foreclosure Action Kit with call scripts, talking points, cited statistics, and step-by-step resources.
- **[fiscal-dashboard.html](fiscal-dashboard.html)** — Fiscal analysis dashboard: the real cost of VA foreclosure vs. partial claim. Verified federal data, sourced citations.

### Crisis Case Management Skill System ("Social Worker in a Box")
A Claude AI skill system for veteran families, case managers, and advocates navigating VA mortgage foreclosure. Built by a social worker for crisis case management — designed to work when executive function is degraded and professional help isn't available.

**This is not legal advice.** This is a crisis case management toolkit that helps families organize documentation, identify potential violations, understand options, and communicate effectively with attorneys, congressional offices, and agencies.

```
skills/
  SKILL.md                              — Core 13-step case analyzer
  va-complaint-drafter_SKILL.md         — CFPB, VA OIG, state AG, credit disputes, FOIA, QWR
  va-congressional-brief_SKILL.md       — Congressional briefs, staffer emails, testimony
  va-post-foreclosure-advisor_SKILL.md  — Eviction defense, Cash for Keys, occupancy rights
  leann-workflow-enforcer_SKILL.md      — Workflow rules and session management

references/
  regulatory-framework.md       — 38 CFR 36.4319, M26-4 Ch.5, RESPA, RCW 61.24
  violation-checklist.md         — Violation identification and evidence mapping
  damages-framework.md           — Damages assessment and quantification
  sol-tracker.md                 — Statute of limitations calculator
  agency-filing-guide.md         — Filing URLs, templates, procedures
  political-strategy-guide.md    — Audience framing, timing, sequencing
  phone-scripts.md               — Delegatable call scripts
  call-recording-guide.md        — State consent laws, recording practices
  servicer-audit-guide.md        — CFPB, PACER, HMDA, enforcement history
  post-foreclosure.md            — Post-sale rights, CFK analysis, UD defense
  equity-assessment-guide.md     — Equitable impact assessment
  de-identification.md           — Privacy protection for minors/clients

docs/
  getting-started.md                        — Setup instructions
  VA_Foreclosure_Advocacy_Skill_Scope_v4.md — Full architecture and design spec
```

### Trackers
- **Ledford_Expanded_Tracker_v2.xlsx** — Case tracking spreadsheet
- **Ledford_Influencer_Outreach_Tracker.xlsx** — Outreach and contact tracking

## Known Issues — Help Wanted

1. **Context loss between sessions** — Skills drop guidelines and workflow rules when starting a new Claude chat. This is the #1 bug.
2. **Skill activation inconsistency** — Sub-skills don't always activate on new chat start.
3. **Memory compaction** — Long sessions cause context compaction that drops critical case details.
4. **Violation calculator** — Need a JavaScript widget that lets a veteran enter their existing rate and offered rate to check for M26-4 Ch.5 rate cap violations.
5. **Full website build** — All the raw materials are here for someone to build a proper website with database, search, and interactive tools.

## The Crisis

- 90,000+ VA borrowers currently delinquent
- 10,000+ veteran families already lost homes since VASP ended May 2025
- 160,000+ families total impacted and climbing
- Congress passed H.R. 1815 unanimously (signed July 2025) — VA still hasn't implemented it
- Freedom Mortgage: $130.3M in cumulative federal penalties

## Design Principles

- **Zero-decision-point**: Works when executive function is degraded
- **Low-spoon**: Minimal user input required
- **Trauma-informed**: No shame-based framing, no unnecessary friction
- **Domain-transferable**: Framework applies to FEMA, CPS, immigration, SSI, Medicaid
- **Pro se first**: Built for people without attorneys

## Contributing

If you have improvements, tools, or resources to add — open a pull request or start a Discussion.

We especially need:
- RESPA/mortgage servicing attorneys in every state
- Developers to build out a full website and database from these materials
- Tech help debugging the crisis case management skill system
- Organizers willing to coordinate state-level outreach
- Anyone who can build the rate cap violation calculator

## Links

- [NPR Investigation (April 2, 2026)](https://www.npr.org/2026/04/02/nx-s1-5750814/veterans-mortgages-foreclosure-va-rescue)
- [NPR Families Contact Page](https://www.npr.org/2023/11/10/1212408194/military-veteran-mortgage-foreclosure-covid-forbearance)
- [VASP Family Support (Facebook)](https://www.facebook.com/groups/1600985297835973/)
- [Linktree (all resources)](https://linktr.ee/leann.salmonberry)

## Contact

Leann Ledford · 2022 Elizabeth Dole Foundation Caregiver Fellow · MSW Graduate Student · WA Certified Victim Advocate
jlledford.family@gmail.com
