---
name: va-foreclosure-case-analyzer
description: >
  Analyzes VA-guaranteed mortgage foreclosure cases for regulatory violations,
  servicer misconduct, and borrower defense strategies. Covers RESPA/Reg X,
  38 CFR 36.4319, CARES Act, M26-4 Chapter 5 loss mitigation waterfall,
  VA Partial Claim, escrow overcharges, and state consumer protection statutes.
  Use when someone mentions VA foreclosure, wrongful foreclosure, VA loan
  violation, servicer misconduct, loss mitigation failure, VASP, escrow
  overcharge, Cash for Keys, or veteran housing rights. Also trigger on
  uploaded VA loan documents, servicer correspondence, or foreclosure notices.
  Also use for CFPB complaints, VA OIG filings, congressional briefs,
  credit disputes, or state AG complaints about mortgage servicing.
  Built for pro se advocates, case managers, social workers, VSO caseworkers,
  and veterans — not for corporate legal review.
metadata:
  author: Leann Ledford
  version: 1.0.0
  domain: veteran-housing-advocacy
  jurisdiction: US-federal, WA-state
  license: Apache-2.0
---

# VA Foreclosure Case Analyzer

Analyzes VA mortgage foreclosure cases for regulatory violations and builds
advocacy strategies from the borrower's perspective. This is the first
borrower-side legal advocacy skill in the Claude ecosystem.

**Who this is for:** Veterans, military families, VSO caseworkers, legal aid
attorneys, congressional staff, social workers, and pro se advocates.

**What it produces:** Violation analyses, evidence maps, damages assessments,
equity impact statements, politically calibrated advocacy documents, and
prioritized next-action lists.

**NOT LEGAL ADVICE.** This skill produces advocacy analysis. Attorney review
is required before filing any legal document.

---

## Quick-Start Mode

If the user signals limited capacity ("quick check," "I only have 20 minutes,"
"just one document," or similar):

1. Ask: What single document or issue is most urgent right now?
2. Run only the most relevant violation check against that one item
3. Output: one paragraph — the violation, the regulation, the single most
   important next action
4. Offer: "When you have more capacity, we can run the full analysis."

Do not run the full workflow in quick-start mode. Respect capacity constraints.
This is a clinical accommodation, not a shortcut.

---

## Full Analysis Workflow

### Checkpoint A: Case Intake

Gather before any analysis. Ask for what's missing — don't require everything
upfront, but flag gaps explicitly.

1. **Loan details** — VA loan number, original rate/balance/date, servicer, guaranty status
2. **Forbearance/modification history** — CARES Act dates, VASP enrollment, modification offers (rate and terms offered vs. original)
3. **Servicer communications** — NOEs, RFIs, loss mitigation correspondence, chronological
4. **VA interactions** — VALERI submissions (or lack thereof), loan technician contacts
5. **Foreclosure process** — notice of default date, trustee sale date, current title holder, judicial vs. non-judicial
6. **Escrow and financials** — escrow disclosure statements, property tax exemption status (especially disabled veteran exemptions), fee itemization, reinstatement figures
7. **Borrower circumstances** — veteran disability rating, occupancy status, household composition, third-party assistance attempted (VSOs, nonprofits)
8. **Existing complaints** — OIG, CFPB, state AG, credit bureau disputes already filed
9. **Call recordings or notes** — dates, participants, key statements
10. **Post-foreclosure status** (if applicable) — title holder, Cash for Keys status, occupancy timeline
11. **Household equity profile** (gather with care):
    - Protected class factors: disability, race/ethnicity, gender, age, LGBTQ+, national origin
    - Household: multigenerational, minor children, caregiver responsibilities
    - Geography: rural vs. urban, alternative housing availability, proximity to VA medical
    - Support network: family/community supports or isolation
    - Economic context: generational wealth/stability, benefits-dependent income
    - The user is never required to disclose this. Explain why it strengthens advocacy and respect "no."
12. **Objectives** — rescission, modification, damages, policy change, media/advocacy, combination

**Defaults if not provided:** Non-judicial foreclosure state, servicer failed to exhaust loss mitigation, veteran is owner-occupant. Do not assume equity factors — ask or note "not assessed." Label all assumptions.

---

### Step 1: Identify Regulatory Framework

Map which laws apply. Consult `references/regulatory-framework.md` for full
provision text.

| Framework | Key question |
|-----------|-------------|
| 38 CFR 36.4319 | Did servicer get VA approval before foreclosure referral? |
| M26-4 Chapter 5 | Was loss mitigation waterfall followed? Rate cap (existing+1%) met? |
| RESPA/Reg X §1024 | NOE/RFI responded to? Dual tracking? Escrow accuracy? |
| CARES Act §4022 | Forbearance protections honored? Credit reporting during forbearance? |
| H.R. 1815 / §3720(h) | Partial claim evaluated? Mandatory mitigation sequence completed? |
| State DTA (WA: RCW 61.24) | Foreclosure notice and recording requirements met? |
| State CPA (WA: RCW 19.86) | Pattern of unfair/deceptive practices? |
| FCRA | Credit reporting accuracy? CARES Act interaction? |
| State property tax exemptions | Disabled veteran exemption reflected in escrow? |

---

### Step 2: Violation Analysis

Check each of the 9 violation categories. For detailed elements, evidence
requirements, and counterargument frameworks, consult
`references/violation-checklist.md`.

For each violation found, document:
- **What the law requires** — cite specific provision
- **What happened** — sourced facts from case documents
- **Why it's a violation** — connect facts to legal standard
- **What the servicer will argue** — anticipated defense
- **Why that argument fails** — rebuttal with evidence
- **Evidence status** — confirmed, unverified, or still needed

The 9 categories:

1. **Loss mitigation failure** — waterfall not exhausted, rate cap violated, VASP/partial claim not evaluated
2. **RESPA NOE/RFI non-response** — qualified written requests unanswered or errors uncorrected
3. **Forbearance breach** — program sunset without notice, post-forbearance options not evaluated
4. **Unauthorized foreclosure** — no VALERI submission, no VA authorization (38 CFR 36.4319)
5. **False credit reporting** — delinquencies reported during CARES Act forbearance
6. **Dual tracking** — foreclosure advanced while loss mitigation pending; "Not Reviewed" markings
7. **State consumer protection** — pattern of unfair/deceptive practices, servicer enforcement history
8. **Defective foreclosure notice** — state-specific procedural requirements not met
9. **Escrow overcharge** — property tax exemption not reflected, surplus not refunded, inflated reinstatement defeating third-party cure attempts

Mark every unverified citation with `[VERIFY]`. Never invent statutory
citations or case names.

---

### Step 3: Evidence Mapping

Build a chronological evidence table:

| Date | Event | Source | Violation | Significance |
|------|-------|--------|-----------|-------------|
| | | | | |

Flag three things explicitly:
- **Gaps** — what evidence is needed but not yet obtained
- **VSO/third-party interference** — where servicer errors defeated external rescue attempts (inflated reinstatement, escrow compounding)
- **Call recording evidence** — admissions against interest from recorded calls

---

### Step 4: Equitable Impact Assessment

Assess how violations produced disproportionate harm based on the household's
equity profile. Consult `references/equity-assessment-guide.md` for the full
framework, disparate impact data sources, and statement templates.

Three components:

**4a. Disparate impact** — Did the servicer's conduct (or the system's
structural gaps) produce worse outcomes because of protected characteristics?
Connect each factor to specific enforcement priorities (CFPB prioritizes
disparate impact; congressional offices respond to constituent equity stories).

**4b. System failure equity** — Beyond the servicer, did the regulatory system
itself fail this household inequitably? (VALERI design gaps, VASP sunset
timing, loss mitigation complexity assuming financial sophistication)

**4c. Equity impact statement** — Draft a 2-3 paragraph insertable block that
can drop into any advocacy document. Name the factors (with consent), connect
violations to disproportionate impact, situate within systemic patterns.

This step transforms a technical complaint into an enforcement priority.
Agencies receive thousands of complaints — the ones that become investigations
are the ones where harm falls on protected populations.

---

### Step 5: Damages Assessment

Consult `references/damages-framework.md` for calculation templates.

Categories to assess:
- Direct escrow overcharges (monthly × months affected)
- RESPA statutory damages
- Actual damages (lost equity: property value at sale vs. outstanding balance)
- Consequential damages (relocation, health, credit, lost exemptions)
- State CPA multipliers (WA: treble damages `[VERIFY current cap]`)
- Fee-shifting (RESPA §2605(f), state CPA)
- VSO payment interference (dollar amount of third-party payments that fell short)

---

### Step 6: Statute of Limitations

Consult `references/sol-tracker.md` for full SOL table by claim type.

Check every identified violation against its SOL. Flag any claim approaching
expiration as **URGENT** — SOL urgency overrides all other sequencing
considerations.

---

### Step 7: Post-Foreclosure Assessment

If foreclosure has occurred, consult `references/post-foreclosure.md`.

Assess: title status, occupancy rights, Cash for Keys consequences (signing
releases all claims), VA authority under §3732, redemption options, and the
decision tree for sign vs. don't sign with timeline mapping.

---

### Step 8: Records Requests

Identify missing evidence and draft requests. Consult
`references/agency-filing-guide.md` for templates and filing URLs.

| Type | Target | What to request |
|------|--------|----------------|
| FOIA | VA (RLC) | VALERI records, internal correspondence, foreclosure authorization |
| QWR | Servicer | Payment history, escrow history, loss mitigation file, internal notes |
| Public records | County | Recording dates for notice of default, trustee sale, trustee deed |
| Credit report | Bureaus | Complete file with reporting dates and furnisher details |
| Congressional | Via office | VA's internal file (constituent services channel) |

---

### Step 9: Servicer Enforcement History

Research the servicer's pattern of conduct. Consult
`references/servicer-audit-guide.md` for search URLs and databases.

Check: CFPB complaint database, CFPB enforcement actions, state AG
settlements, HMDA data, Ginnie Mae/VA restrictions, federal court filings
(PACER), BBB status.

Output: enforcement history summary with total penalties, violation count, and
whether the same conduct appears in prior actions. This transforms an
individual complaint into evidence of a corporate pattern.

---

### Step 10: Strategic & Political Assessment

**10a. Case strength** — Rank claims by evidence strength. Identify the central
factual dispute (the single most resolvable one). Connect to enforcement
history pattern evidence.

**10b. Political landscape** — Consult `references/political-strategy-guide.md`
for the full framework. Assess: congressional session status, election cycle,
committee jurisdiction, agency enforcement posture, pending legislation,
media timing.

**10c. Audience framing** — Same facts, different emphasis:

| Audience | Lead with |
|----------|----------|
| Republican veteran-committee | Failed promise to a Marine; VA system failure; government waste |
| Democratic housing-committee | Disparate impact; corporate pattern; housing equity |
| Bipartisan/moderate | Oversight failure; taxpayer cost; system had tools but didn't use them |
| VA OIG | Specific reg violations; VALERI failure confirms prior OIG audit findings |
| CFPB | RESPA violations; repeat offender pattern; consumer harm data |
| State AG | State CPA hooks; harm to state residents; "first to hold them accountable" |
| Media | Family narrative; smoking gun documents; "how many more?" |
| Attorney | Elements; evidence; novel legal theory; counterarguments |

**10d. Timing** — What goes now (SOL-urgent, deadlines), what benefits from
coordination, what to hold for strategic timing. Legal deadlines always
override political timing.

---

### Step 11: Output Routing

Based on the analysis, recommend which outputs to generate:
- Agency complaints (CFPB, OIG, state AG)
- Congressional advocacy brief
- Credit dispute letters
- Media background memo
- Legal intake summary for attorney
- Records requests (FOIA, QWR)
- Post-foreclosure decision analysis
- Phone scripts for delegatable calls

---

### Checkpoint B: Post-Analysis Verification

Before delivering the analysis, verify:

1. All factual claims sourced to specific documents?
2. All citations verified or marked `[VERIFY]`?
3. Each violation includes servicer counterargument and rebuttal?
4. Central factual dispute clearly identified?
5. Next actions prioritized by deadline urgency?
6. Escrow/property tax exemption checked?
7. VSO payment interference assessed?
8. Servicer enforcement history checked or flagged?
9. Post-foreclosure status addressed (if applicable)?
10. Equitable impact assessment completed (with consent)?
11. Political landscape assessed and framing calibrated?
12. Timing/sequencing strategy documented?
13. Call recordings inventoried?

---

## Quality Audit

Run before finalizing any output:

- [ ] Every assertion sourced or labeled "unverified"
- [ ] Citations verified or marked `[VERIFY]`
- [ ] No conclusory labels without supporting facts
- [ ] Counterargument addressed for each violation
- [ ] Servicer enforcement history checked or flagged
- [ ] Disability status noted where relevant to protections
- [ ] State-specific requirements addressed
- [ ] Property tax exemption checked against escrow
- [ ] Cross-referenced against prior filed documents
- [ ] Timeline gaps flagged
- [ ] SOL deadlines calculated, urgent claims flagged
- [ ] Post-foreclosure status assessed (if applicable)
- [ ] Damages framework populated
- [ ] Equity impact statement drafted
- [ ] Audience framing verified for target
- [ ] NOT LEGAL ADVICE disclaimer included

---

## Anti-Hallucination Protocol

- Never invent statutory citations, case names, or regulatory provisions
- Mark all unverified claims with `[VERIFY: description]`
- Cross-reference current statements against prior filed documents — this
  matters because stress-induced memory gaps are real and common in crisis
  cases, and inconsistencies between documents undermine credibility
- Do not assert rights without verified statutory basis
- When citing VA circulars, note they may have been superseded
- Do not assume H.R. 1815 implementation details not yet published

---

## Guidelines

### Trauma-informed practice
- Use advocate language, not clinical or shame-based language
- Frame the veteran as the expert on their own experience
- Distinguish confirmed, pending, and unknown facts
- Respect capacity — if the user signals low spoons, switch to quick-start
- Never pressure disclosure of protected class information
- No "you should have" or "don't forget to" — use "next step:" or "when ready:"

### Phone delegation
When a household member can make simple calls, provide:
- Script-like talking points (3-5 bullets max)
- Who to ask for, what to say, what to write down, what NOT to agree to

### Tool integration
This skill works alongside NotebookLM in a dual-tool workflow:
- Skill outputs (violations, timelines, evidence gaps) feed into NotebookLM
- NotebookLM source-gap analysis feeds back into evidence mapping
- See `references/notebooklm-integration.md` for notebook structure

### Recommended Claude styles
This skill ships with pre-built custom styles in `styles/`:
- **Field Manual** (default) — neurodivergent/crisis-optimized scannability
- **Congressional Brief** — formal, policy-focused, partisan-calibrated
- **Plain Language** — family, friends, non-expert audiences
- **Legal Intake** — attorney-facing, elements-focused

Set up via Settings → Style → Create style. See each style file for the
description to paste.

---

## Reference Files

Consult these as directed in the workflow steps above:

| File | When to consult |
|------|----------------|
| `references/regulatory-framework.md` | Step 1 — full provision text for each framework |
| `references/violation-checklist.md` | Step 2 — detailed elements, evidence, counterarguments for all 9 categories |
| `references/equity-assessment-guide.md` | Step 4 — disparate impact tables, data sources, statement templates |
| `references/damages-framework.md` | Step 5 — calculation templates for each damage category |
| `references/sol-tracker.md` | Step 6 — SOL by claim type with clock-start events |
| `references/post-foreclosure.md` | Step 7 — §3732 options, Cash for Keys analysis, decision tree |
| `references/agency-filing-guide.md` | Step 8 — FOIA/QWR templates, filing URLs, required info |
| `references/servicer-audit-guide.md` | Step 9 — enforcement history search URLs and databases |
| `references/political-strategy-guide.md` | Step 10 — political landscape framework, framing matrices |
| `references/call-recording-guide.md` | Step 3 — how to process recordings, flag admissions |
| `references/phone-scripts.md` | Step 11 — delegatable call scripts |
| `references/notebooklm-integration.md` | Guidelines — dual-tool workflow setup |
