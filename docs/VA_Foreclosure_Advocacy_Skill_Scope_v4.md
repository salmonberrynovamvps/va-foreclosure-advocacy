# VA FORECLOSURE ADVOCACY SKILL & CRISIS CASE MANAGEMENT OS — SCOPE & DESIGN v4
## Custom Claude Skill for Pro Se Veteran Mortgage Defense
### Prepared for Leann Ledford | March 28, 2026

---

## WHAT WE LEARNED FROM EXISTING LEGAL SKILLS

### Structural patterns worth adopting

**From the Demand Letter skill (agentskills.legal):**
- Mandatory pre-draft intake checkpoint (Checkpoint A) — forces Claude to gather facts before drafting
- Element-driven fact narrative — chronological, sourced, no conclusory labels
- **Servicer counterargument anticipation** — each claim analyzed for how opposing counsel would attack it
- Anti-hallucination protocol — `[VERIFY]` markers on unconfirmed citations
- Post-draft alignment checkpoint (Checkpoint B) — confirms the output matches intent
- Quality audit checklist — runs before final delivery
- "ATTORNEY REVIEW REQUIRED" disclaimer

**From the Regulatory Practice skill:**
- Sub-practice area routing table — maps which regulatory framework applies
- Core workflow: identify framework → map obligations → gap analysis → design response → manage agency interactions
- Tracks enforcement trends alongside static rules

**From the Litigation Practice skill:**
- Sub-area taxonomy with routing logic
- Core principles section (zealous advocacy, investigate before concluding)
- Pitfalls section — common failure modes stated explicitly
- Jurisdiction check as mandatory first step

**From the Anthropic skill-building PDF:**
- SKILL.md with YAML frontmatter (name + description with trigger phrases)
- Progressive disclosure: frontmatter → body → references/
- Keep SKILL.md under 5,000 words; move detail to references/
- Composability — should work alongside other skills
- `[VERIFY]` convention for unconfirmed legal citations

**From the Lawvable repo:**
- Jurisdiction-tagged folders (🇺🇸, 🇫🇷, 🌐)
- Utility skills separate from substantive skills
- AGPL-3.0 licensing for open-source legal skills

### What NONE of them do (our gap)

Every existing legal skill is built for **lawyers reviewing corporate transactions**. Zero skills exist for:
- Borrower-side mortgage defense
- VA-specific regulatory frameworks (38 CFR, M26-4)
- RESPA/Reg X enforcement from the consumer perspective
- Pro se advocacy document generation
- Congressional/agency complaint workflows
- Wrongful foreclosure timeline construction
- Loss mitigation waterfall analysis
- Credit reporting dispute frameworks
- Escrow overcharge analysis (especially disabled veteran property tax exemptions)
- Post-foreclosure occupancy rights and remediation options
- Audio/call recording analysis for servicer admissions

---

## PROPOSED SKILL ARCHITECTURE

### Option A: Single skill (simpler, faster to build)
One SKILL.md covering all VA foreclosure advocacy functions.
- Pro: one file to maintain, one upload
- Con: could get long (5,000+ words), may over-trigger

### Option B: Skill family (modular, more precise) ← RECOMMENDED
A coordinated set of 3-5 skills that work together:

```
va-foreclosure-advocacy/
├── SKILL.md                    # Root skill — case analysis & routing
├── references/
│   ├── regulatory-framework.md # 38 CFR 36.4319, M26-4, RESPA, RCW 61.24
│   ├── violation-checklist.md  # The 9 documented violation categories + counterarguments
│   ├── timeline-template.md    # Chronological evidence framework
│   ├── agency-contacts.md      # VA, CFPB, WA AG, OIG filing info + FOIA guidance
│   ├── document-templates.md   # Congressional brief, complaint, dispute letter
│   ├── damages-framework.md    # Escrow, statutory, consequential, fee-shifting calculations
│   ├── post-foreclosure.md     # Title status, occupancy rights, §3732 options, Cash for Keys
│   ├── sol-tracker.md          # Statute of limitations by claim type with clock-start events
│   ├── call-recording-guide.md # How to process/summarize servicer calls for legal use
│   └── de-identification.md    # Guide for community release (what to replace, what to keep)
├── styles/                     # Recommended Claude custom styles — zero-decision formatting
│   ├── field-manual.md         # Default for all skill outputs (neurodivergent/crisis-optimized)
│   ├── congressional-brief.md  # Formal, policy-focused, partisan-calibrated
│   ├── plain-language.md       # For family, friends, VSO caseworkers, non-expert audiences
│   └── legal-intake.md         # Attorney-facing, elements-focused, procedural
├── scripts/                    # (optional) Python helpers
│   └── timeline_builder.py     # Parse dates from documents
```

Individual sub-skills (can be separate uploads or bundled):

| Skill | Triggers on | Output |
|-------|------------|--------|
| `va-foreclosure-case-analyzer` | "analyze this foreclosure" "review my VA loan case" "what violations occurred" | Structured violation analysis with regulatory citations |
| `va-complaint-drafter` | "draft complaint" "CFPB complaint" "OIG supplement" "WA AG filing" | Agency-specific complaint documents |
| `va-congressional-brief` | "congressional brief" "advocacy one-pager" "write to my representative" | Legislative audience documents with policy framing |
| `va-timeline-builder` | "build timeline" "case chronology" "evidence sequence" | Sourced chronological timeline from case documents |
| `va-credit-dispute` | "credit dispute" "false reporting" "credit bureau letter" | FCRA/CARES Act dispute letters |

---

## ROOT SKILL DESIGN: `va-foreclosure-case-analyzer`

### YAML Frontmatter
```yaml
---
name: va-foreclosure-case-analyzer
description: >
  Analyzes VA-guaranteed mortgage foreclosure cases for regulatory violations,
  servicer misconduct, and borrower defense strategies. Covers RESPA/Reg X,
  38 CFR 36.4319, CARES Act forbearance protections, Washington DTA (RCW 61.24),
  M26-4 Chapter 5 loss mitigation waterfall, VA Partial Claim authority,
  escrow overcharges, and state consumer protection statutes. Use when reviewing
  VA loan foreclosure documents, identifying servicer violations, building case
  chronologies, preparing advocacy materials for congressional offices, OIG, CFPB,
  or state AG complaints, or assessing post-foreclosure options. Also use for
  "quick check" — rapid single-document triage when time/energy is limited.
  Trigger phrases: VA foreclosure, wrongful foreclosure, loss mitigation failure,
  VASP, VA loan violation, servicer misconduct, mortgage servicing abuse,
  veteran housing rights, escrow overcharge, Cash for Keys, post-foreclosure.
metadata:
  author: Leann Ledford
  version: 1.0.0
  domain: veteran-housing-advocacy
  jurisdiction: US-federal, WA-state
---
```

### Low-Spoon Quick-Start Mode

If the user says "quick check," "I only have 20 minutes," "just one document," or signals limited capacity:

1. Ask: What single document or issue is most urgent right now?
2. Run ONLY the most relevant violation check against that one item
3. Output: one paragraph identifying the violation, the regulation, and the single most important next action
4. Offer: "When you have more capacity, we can run the full analysis. Here's what to prioritize next."

Do not run the full multi-step workflow in quick-start mode. Respect capacity constraints.

### Checkpoint A: Case Intake (Mandatory for full analysis)

Gather before any analysis:

1. **Loan details** — VA loan number, original terms (rate, balance, date), servicer, guaranty status
2. **Forbearance/modification history** — CARES Act forbearance dates, VASP enrollment, modification offers (including rate and terms offered vs. original), accepted/rejected status
3. **Servicer communications** — NOEs, RFIs, loss mitigation correspondence (chronological)
4. **VA interactions** — VALERI submissions (or lack thereof), loan technician contacts, VA letters
5. **Foreclosure process** — notice of default date, trustee sale date, current title holder, state foreclosure type (judicial vs. non-judicial)
6. **Escrow and financial records** — escrow disclosure statements, property tax exemption status (especially disabled veteran exemptions), fee itemization, reinstatement figures provided to borrower or third parties
7. **Borrower circumstances** — veteran status/disability rating, hardship type, current occupancy status, household composition, third-party assistance attempted (VSOs, nonprofits)
8. **Existing complaints** — OIG, CFPB, state AG, credit bureau disputes already filed
9. **Call recordings or notes** — dates, participants, key statements (see `call-recording-guide.md`)
10. **Post-foreclosure status** (if applicable) — who holds title, Cash for Keys offer status, occupancy timeline, eviction proceedings
11. **Household equity profile** (gather with care — this information strengthens advocacy but must be handled with informed consent):
    - Protected class factors present: disability (veteran and/or spouse/dependents), race/ethnicity, gender, age (elderly household members, minor children), LGBTQ+ status, national origin, language access needs
    - Household composition: multigenerational home, minor children, dependents with disabilities, caregiving responsibilities
    - Geographic context: rural vs. urban, housing market conditions, availability of alternative housing, proximity to VA medical facilities
    - Support network: existing family/community supports vs. isolation, distance from extended family, faith community, VSO chapter access
    - Economic context: generational wealth/stability or absence thereof, single-income household, caregiver who cannot work, benefits-dependent income
    - Compounding vulnerabilities: TBI/PTSD affecting the veteran's ability to self-advocate, spouse serving as both caregiver and case manager, medical conditions requiring stable housing
    - *Note to user:* You are never required to disclose any of this. But if these factors are present, they can significantly strengthen your case — agencies prioritize enforcement where harm falls on protected populations, and congressional offices respond to constituent stories that illustrate systemic inequity. This information is used solely for advocacy framing, never shared without explicit consent.
12. **Objectives** — rescission, modification, damages, policy change, media/advocacy, combination

Defaults (if not provided): assume non-judicial foreclosure state, assume servicer failed to exhaust loss mitigation, assume veteran is owner-occupant. Do not assume equity factors — ask or note "not assessed." Label all assumptions explicitly.

### Step 1: Identify Regulatory Framework

Map which laws and regulations apply:

| Framework | Scope | Key Provisions |
|-----------|-------|----------------|
| 38 CFR 36.4319 | VA foreclosure authorization | Servicer must obtain VA approval before foreclosure referral |
| M26-4 Chapter 5 | Loss mitigation waterfall | Rate cap (existing+1%), modification sequence, partial claim |
| RESPA/Reg X (12 CFR 1024) | Servicer obligations | NOE/RFI response (§1024.35-36), dual tracking prohibition (§1024.41(g)), loss mitigation procedures, escrow accuracy (§1024.17) |
| CARES Act §4022 | Forbearance protections | 180-day forbearance, credit reporting protections during forbearance |
| H.R. 1815 (VA Home Loan Reform Act) | Partial claim authority | Permanent partial claim program, implementation timeline, §3720(h) mandatory mitigation |
| RCW 61.24 | Washington DTA | Non-judicial foreclosure notice, mediation, recording requirements |
| WA CPA (RCW 19.86) | State consumer protection | Unfair/deceptive acts, private right of action |
| FCRA (15 U.S.C. §1681) | Credit reporting | Accuracy obligations, dispute process, CARES Act interaction |
| 38 U.S.C. §3720(h) | VA statutory authority | Mandatory mitigation sequence before foreclosure |
| 38 U.S.C. §3732 | VA post-foreclosure authority | VA can sell, lease, or convey acquired property |
| State property tax exemption statutes | Varies by state (WA: RCW 84.36.381) | Disabled veteran exemptions affecting escrow calculations |

### Step 2: Violation Analysis

For each potential violation category, assess the violation, identify supporting evidence, and anticipate the servicer's counterargument.

**Format for each violation:**
- **What the law requires** — cite specific provision
- **What happened** — sourced facts from case documents
- **Why it's a violation** — connect facts to legal standard
- **What the servicer will argue** — anticipated defense
- **Why that argument fails** — rebuttal with evidence
- **Evidence needed** — what's confirmed vs. what still needs to be obtained

---

**1. Loss mitigation failure / Race to foreclose**
- Did servicer exhaust all loss mitigation options before foreclosure referral?
- Was modification offered at compliant rate (existing+1% cap per M26-4)?
- Was VASP/partial claim evaluated before foreclosure?
- *Servicer will argue:* "We offered a modification and borrower declined."
- *Rebuttal framework:* Check VALERI submission records; check whether offered rate complied with M26-4 cap; check whether "Not Reviewed" markings contradict the claim.

**2. RESPA NOE/RFI non-response (12 CFR §1024.35-36)**
- Were qualified written requests answered within 30/5 business days?
- Were errors acknowledged and corrected?
- *Servicer will argue:* "We responded" or "The letter wasn't a valid QWR."
- *Rebuttal framework:* Check whether response addressed specific errors raised; check whether escrow corrections were actually made.

**3. Forbearance contract breach**
- Did forbearance program sunset without individual notice?
- Were post-forbearance options properly evaluated?
- *Servicer will argue:* "Program ended per its terms; borrower was notified through general communications."
- *Rebuttal framework:* Check for individual (not mass) notice; check whether transition to post-forbearance evaluation actually occurred.

**4. Unauthorized foreclosure (38 CFR 36.4319)**
- Did servicer submit loan file to VALERI before foreclosure referral?
- Did VA authorize the foreclosure?
- *Servicer will argue:* "We followed standard procedure" or "VA was informed."
- *Rebuttal framework:* VALERI audit is the kill shot — if no submission exists in VALERI, no authorization was obtained. VA technician statements confirming non-submission are direct evidence.

**5. False credit reporting (FCRA + CARES Act)**
- Were delinquencies reported during CARES Act forbearance?
- Were reports backdated into protected periods?
- *Servicer will argue:* "Reports reflected actual loan status after forbearance ended."
- *Rebuttal framework:* Check reporting dates against forbearance period; backdating into a CARES-protected window is per se violation.

**6. Dual tracking (12 CFR §1024.41(g))**
- Was foreclosure pursued while loss mitigation was pending?
- Were modification applications marked "Not Reviewed"?
- *Servicer will argue:* "No complete application was pending" or "Application was reviewed and denied."
- *Rebuttal framework:* The Jan 15, 2025 VASP letter + Feb 3 "Not Reviewed" decision is the smoking gun — you can't claim you reviewed something and simultaneously mark every option "Not Reviewed."

**7. State consumer protection violations (WA CPA, RCW 19.86)**
- Pattern of unfair/deceptive practices?
- Servicer's enforcement history across jurisdictions?
- *Servicer will argue:* "Isolated errors, not a pattern."
- *Rebuttal framework:* Enforcement history audit — if CFPB, other state AGs, and consent orders show the same conduct, the "isolated" defense collapses. Cross-reference the servicer's public enforcement record.

**8. Defective foreclosure notice/recording (RCW 61.24)**
- Did notice comply with RCW 61.24.030/.040 requirements?
- Were recording requirements met with Spokane County Auditor?
- Were notices properly served?
- *Servicer will argue:* "All procedural requirements were met."
- *Rebuttal framework:* Verify recording dates and service dates against statutory requirements — any defect is a procedural ground to challenge the sale's validity.

**9. Escrow overcharge / Property tax exemption failure (12 CFR §1024.17)**
- Did servicer conduct annual escrow analysis using actual (not estimated) tax obligations?
- Was disabled veteran property tax exemption reflected in escrow calculations?
- Was escrow surplus (>$50) refunded within 30 days per §1024.17(f)?
- Did escrow overcharge inflate the reinstatement figure, defeating third-party cure attempts?
- *Servicer will argue:* "We used the best available tax information" or "Borrower didn't notify us of the exemption."
- *Rebuttal framework:* Exemption was a public county record; RESPA requires servicer to use actual projected tax obligations, not borrower-reported data. Calculate the dollar impact: monthly overcharge × months = total, plus downstream harm (inflated reinstatement figure that caused VSO payment efforts to fall short).

For each violation found: cite the specific regulation, quote the relevant servicer action/inaction, note the evidence source, and mark unverified citations with `[VERIFY]`.

### Step 3: Evidence Mapping

Build a chronological evidence table:

| Date | Event | Source Document | Violation Category | Notes |
|------|-------|----------------|-------------------|-------|
| [date] | [what happened] | [exhibit/document] | [which violation] | [significance] |

**Flag gaps:** what evidence is needed but not yet obtained.

**Flag VSO/third-party interference:** where servicer errors compounded to defeat external rescue attempts (e.g., inflated reinstatement figures causing nonprofit payment efforts to fall short). This is a distinct harm multiplier that strengthens damages claims and makes compelling narrative for congressional/media audiences.

**Flag call recording evidence:** note any recorded calls with dates, participants, and key admissions. Reference `call-recording-guide.md` for processing instructions.

### Step 4: Equitable Impact Assessment

Assess how the servicer's violations produced disproportionate or compounding harm based on the household's equity profile. This step transforms a regulatory compliance analysis into an advocacy document that reflects lived reality.

**4a. Disparate impact analysis**

Evaluate whether the servicer's conduct — or the system's structural gaps — produced worse outcomes for this household because of protected characteristics:

| Factor | How it compounds harm | Advocacy relevance |
|--------|----------------------|-------------------|
| **Disability (veteran)** | TBI/PTSD may impair ability to navigate complex loss mitigation processes; servicer's failure to provide accessible communication is itself a violation consideration | VA OIG, congressional (veteran protection mandate), Fair Housing Act if applicable |
| **Disability (spouse/caregiver)** | Caregiver burden means the person managing the case is also providing medical/ADL support — capacity constraints are not a choice | Congressional (caregiver equity), media (human interest), Elizabeth Dole Foundation framing |
| **Race/ethnicity (BIPOC)** | Check servicer's HMDA data for disparate denial/foreclosure rates by race in the same geography; CFPB and DOJ prioritize pattern-or-practice racial disparities | CFPB (fair lending), DOJ Civil Rights Division, state AG, media |
| **Gender** | Women disproportionately serve as household case managers while also managing caregiving — the "unpaid labor" of fighting foreclosure falls on them; check if servicer's conduct patterns differ by borrower gender | Congressional (gender equity framing), CFPB |
| **LGBTQ+** | Housing discrimination compounds foreclosure harm; reduced access to family support networks in some communities; may affect available alternative housing | Fair housing framing, state-specific protections |
| **Age (elderly)** | Elderly household members face higher displacement mortality risk; multigenerational homes mean foreclosure displaces people who cannot independently relocate | Congressional (elder protection), media, Adult Protective Services if applicable |
| **Children/minors** | School disruption, loss of stability, documented adverse childhood experiences from housing instability; children cannot advocate for themselves | Congressional (strongest emotional leverage), media, child welfare framing |
| **Multigenerational household** | Foreclosure displaces not just the borrower but extended family who may have no independent housing options; cultural factors in multigenerational living | Congressional, media, community impact framing |
| **Rural vs. urban** | Rural veterans have fewer alternative housing options, less access to legal aid, longer distances to VA facilities; foreclosure in a tight rural market may mean leaving the community entirely | Congressional (rural constituent impact), VA (continuity of care argument) |
| **Economic/generational context** | First-generation homeowner? No family wealth safety net? Benefits-dependent income with no ability to absorb payment shock? This is the difference between "temporary hardship" and "permanent displacement" | All audiences — this contextualizes why a regulatory violation destroyed a family rather than being a recoverable setback |

**4b. System failure equity analysis**

Beyond the servicer's conduct, assess whether the regulatory system itself failed this household inequitably:

- Did the loss mitigation waterfall assume financial sophistication the borrower didn't have?
- Did VA's VALERI system fail to catch what it was designed to catch — and did that failure disproportionately affect veterans with disabilities who couldn't self-advocate through alternative channels?
- Did the gap between VASP sunset and H.R. 1815 implementation fall hardest on the most vulnerable borrowers (those already in forbearance)?
- Was the household's geographic isolation (rural) or support network absence a factor in why third-party intervention came too late?
- Did language access, digital literacy, or communication barriers prevent the borrower from navigating the servicer's process?

**4c. Output: Equity impact statement**

Produce a 2-3 paragraph equity impact statement that can be inserted into any advocacy document. This statement should:
- Name the specific protected characteristics present (with the user's consent)
- Connect each regulatory violation to its disproportionate impact on this household
- Situate the individual case within documented systemic patterns (e.g., CFPB data on foreclosure rates by race/disability, VA OIG findings on oversight gaps)
- Frame the relief requested as an equity correction, not just a regulatory remedy

*Note:* The equity impact statement is the single most important differentiator between a technical complaint and an enforcement priority. Agencies receive thousands of complaints; the ones that become investigations are the ones where the harm pattern implicates protected populations.

### Step 5: Damages Assessment

Calculate and categorize damages:

| Category | Calculation Method | Evidence Needed |
|----------|-------------------|-----------------|
| **Direct escrow overcharges** | Monthly overcharge × months affected | Escrow statements, county tax records, exemption approval date |
| **RESPA statutory damages** | Per-violation amounts under 12 CFR 1024.35(e), 1024.41(a) | Documentation of each violation |
| **Actual damages (lost equity)** | Property value at sale vs. outstanding loan balance | Trustee deed, county assessment, appraisal |
| **Consequential damages** | Relocation costs, health impacts, lost property tax exemption going forward, credit damage | Receipts, medical records, credit reports |
| **State CPA damages** | WA CPA allows treble damages up to $25,000 (RCW 19.86.090) `[VERIFY current cap]` | Pattern evidence, per-violation documentation |
| **Fee-shifting** | Attorney fees if statutory basis exists (RESPA §2605(f), WA CPA) | Verification of fee-shifting provisions |
| **VSO payment interference** | Dollar amount of third-party payments that fell short due to inflated reinstatement figure | VSO correspondence, reinstatement quotes, escrow error calculations |

Address mitigation, offsets, and credits. Note: damages calculation is for advocacy framing and complaint narratives, not for litigation — attorney review required for formal damages claims.

### Step 6: Statute of Limitations Check

For each identified violation, track the applicable SOL:

| Claim Type | SOL Period | Clock Starts | Deadline (if known) | Status |
|------------|-----------|--------------|--------------------:|--------|
| RESPA §2605 (NOE/RFI) | 3 years | Date of violation | | |
| RESPA §2605 (damages) | 1 year | Date of violation | | |
| WA CPA (RCW 19.86) | 4 years | Date of violation | | |
| FCRA | 2 years from discovery, 5 years from violation | Discovery of false reporting | | |
| 38 CFR violations | Varies — may be administrative, not civil SOL | | | |
| WA DTA (RCW 61.24) | Varies by challenge type | Sale date (1/23/26) | | |

Flag any claim approaching SOL expiration as **URGENT** in the strategic assessment.

### Step 7: Post-Foreclosure Status Assessment (if applicable)

If foreclosure has already occurred:

1. **Title status** — Who currently holds title? (VA Secretary, servicer, third-party purchaser)
2. **Occupancy rights** — What are the occupant's rights under state law? (RCW 61.24.060 timeline, PTFA if applicable)
3. **Cash for Keys analysis** — What does signing release? What does not signing preserve? What are the deadlines?
4. **VA authority under 38 U.S.C. §3732** — VA can sell, lease, or convey acquired property; can VA lease back to the veteran? What's the REO disposition timeline?
5. **Redemption** — Does the state have a statutory right of redemption? (WA: generally no for non-judicial, but procedural defects may create grounds to challenge sale validity)
6. **Decision tree:** Sign Cash for Keys (releases all claims) vs. Do not sign (preserves legal rights but triggers eviction proceedings) — map the consequences of each path with timelines

### Step 8: Records Requests and Evidence Gathering

Identify and draft requests for missing evidence:

| Request Type | Target | What to Request | Authority |
|-------------|--------|-----------------|-----------|
| **FOIA** | VA (RLC Denver) | VALERI records for loan, all internal correspondence, foreclosure authorization records | 5 U.S.C. §552 |
| **QWR (Qualified Written Request)** | Servicer | Complete payment history, escrow analysis history, loss mitigation file, all internal notes | RESPA §2605(e) |
| **State public records** | Spokane County Auditor | Notice of Default recording, Notice of Trustee Sale recording, trustee deed recording dates | State public records law |
| **Credit report requests** | Equifax, Experian, TransUnion | Complete credit file with reporting dates and furnisher details | FCRA §1681g |
| **Congressional records request** | Via congressional office | VA's internal file on the loan (constituent services channel) | Congressional inquiry authority |

### Step 9: Servicer Enforcement History Audit

Research the servicer's pattern of conduct:

1. **CFPB complaint database** — search by company name, filter by mortgage servicing
2. **CFPB enforcement actions** — consent orders, civil penalties, repeat offender designations
3. **State AG actions** — search each state AG's press releases and settlement databases
4. **HMDA data** — lending patterns, denial rates by demographic
5. **Ginnie Mae/VA restrictions** — churning restrictions, servicing transfers
6. **Federal court filings** — PACER search for class actions, pattern litigation
7. **BBB status** — accreditation revocations, complaint patterns

Output: enforcement history summary with total penalties, violation count, and whether the same conduct alleged in the current case appears in prior enforcement actions. This transforms an individual complaint into evidence of a corporate pattern — which is what elevates a case from "constituent services" to "enforcement priority" for agencies.

### Step 10: Strategic & Political Assessment

**10a. Case strength assessment**
- **Strongest claims** — rank by evidence strength and legal clarity
- **Central factual dispute** — identify the single most resolvable dispute (e.g., VALERI audit)
- **Equity amplifier** — which claims are strongest when combined with the equity impact assessment?
- **Remediation framing** — frame relief as beneficial to all parties where possible (e.g., "clean exit from REO liability" for VA)
- **SOL urgency** — flag any claims approaching expiration
- **Pattern evidence** — connect individual violations to servicer's documented enforcement history
- **VSO interference multiplier** — where servicer errors defeated third-party rescue attempts, flag for damages and narrative impact

**10b. Political landscape assessment**

Advocacy doesn't happen in a vacuum. Assess the current political environment before choosing targets and framing:

| Factor | What to assess | How it affects strategy |
|--------|---------------|----------------------|
| **Congressional session status** | Is Congress in session or recess? Are relevant committees holding hearings? Is an appropriations cycle active? | Recess = constituent meetings possible; active hearings = real-time testimony/submissions; appropriations = leverage for VA oversight riders |
| **Election cycle proximity** | How close is the next election for the target legislator? Primary vs. general? | Pre-election legislators are more responsive to constituent stories; "veteran family loses home" is a potent campaign-season story for any party |
| **Committee composition & leadership** | Who chairs HVAC, Senate VAC, House Financial Services? What are their priorities? Which subcommittees have jurisdiction? | Match your ask to the committee's active agenda; don't send a housing complaint to the oversight subcommittee if the economic opportunity subcommittee is already holding foreclosure hearings |
| **Partisan framing opportunities** | The same case facts can be framed for different political audiences | *For defense/veteran-focused conservatives:* "The system failed a Marine — the VA didn't protect its own." *For housing equity progressives:* "A disabled veteran of color lost his home because a repeat-offender servicer exploited regulatory gaps." *For government accountability moderates:* "VA oversight failed; the system designed to catch this didn't work." The facts don't change — the frame does. |
| **Agency leadership posture** | What is the current CFPB director's enforcement stance? Is VA leadership prioritizing foreclosure prevention or not? Is the state AG's office actively pursuing mortgage cases? | Under aggressive enforcement leadership, file with the agency. Under passive leadership, congressional pressure to *force* agency action may be more effective. Note: agency leadership can change rapidly — don't build a strategy that depends on a specific appointee. |
| **Pending legislation/rulemaking** | Is there active rulemaking (M26-4 Ch.5 drafting table), pending legislation (H.R. 1815 implementation), or proposed rules that your case illustrates? | Your case becomes a "real-world example" for the policy argument — this is the most powerful form of public comment. Time submissions to open comment periods or hearing schedules. |
| **Media cycle** | Is there active media coverage of VA mortgage issues? Are reporters working on related stories? | Coordinate timing — a complaint filed the same week as an NPR investigative piece gets more traction than one filed in a news vacuum. But don't hold urgent filings for media timing if SOL is running. |
| **Opposing political dynamics** | Is the servicer politically connected? Does the servicer have lobbyists or PAC relationships with relevant legislators? | This doesn't change what you file — but it may change who you file with. If the servicer is a major donor to the committee chair, the ranking member's office may be a more receptive entry point. |

**10c. Audience-specific framing matrix**

For each output document, select the frame that matches the target's political psychology:

| Audience | Primary frame | Secondary frame | What NOT to lead with |
|----------|--------------|----------------|----------------------|
| **Republican veteran-committee member** | Failed promise to a Marine; VA system didn't protect its own | Government waste (VA now holds a house it shouldn't have had to acquire) | Systemic racism framing as the lead (can include as supporting data) |
| **Democratic housing-committee member** | Disparate impact on disabled veteran family; corporate pattern of abuse | Regulatory gap that H.R. 1815 was supposed to fix | "Government is the problem" framing |
| **Bipartisan/moderate** | Oversight failure — the system had the tools and didn't use them | Cost to taxpayer (REO acquisition, VA liability) | Strongly partisan framing in either direction |
| **VA OIG** | Specific regulatory violations with evidence; systemic oversight gap | VALERI failure confirms OIG's own prior audit findings | Emotional narrative (they want facts and regulation numbers) |
| **CFPB** | RESPA violations, repeat offender pattern, consumer harm | Disparate impact data if available | VA-specific regulatory framework (not their jurisdiction) |
| **State AG** | State CPA violations, harm to state residents, no prior state enforcement against this servicer | "Your state could be first to hold them accountable" | Federal regulatory arguments (they want state law hooks) |
| **Media** | Family narrative, smoking gun documents, systemic pattern | Human cost + policy failure + "how many more?" | Legal jargon, regulation numbers in the lead |
| **Legal aid / pro bono attorney** | Clean factual record, strong claims, manageable scope | Novel legal theory (§3720(h) catch-22) that could make precedent | Emotional narrative without legal substance |

**10d. Timing and sequencing strategy**

Not everything should be filed or sent at once. Assess optimal sequencing:

1. **What needs to go NOW** — SOL-urgent claims, pending deadlines (Cash for Keys, eviction)
2. **What benefits from coordination** — congressional inquiry before or after agency complaint? Media story before or after filing?
3. **What to hold** — evidence or arguments that are stronger if revealed at a specific moment (e.g., VALERI audit results after FOIA response, enforcement history after initial agency acknowledgment)
4. **What depends on external events** — pending hearings, rulemaking deadlines, election calendars, NPR publication timing

### Step 11: Output Routing

Based on the analysis, recommend which sub-skills to invoke:
- Complaint drafting (CFPB, OIG, state AG)
- Congressional advocacy brief
- Credit dispute letters
- Media background memo
- Legal intake summary for attorney
- Records requests (FOIA, QWR, public records)
- Post-foreclosure decision analysis

### Checkpoint B: Post-Analysis Verification (Mandatory)

1. Are all factual claims sourced to specific documents?
2. Are all regulatory citations verified or marked `[VERIFY]`?
3. Does each violation analysis include the servicer's likely counterargument and rebuttal?
4. Has the central factual dispute been clearly identified?
5. Are next actions prioritized by deadline urgency (SOL, Cash for Keys, eviction)?
6. Has the escrow/property tax exemption been checked?
7. Have third-party (VSO) payment interference effects been assessed?
8. Has the servicer's enforcement history been checked or flagged for checking?
9. Are post-foreclosure status and options addressed (if applicable)?
10. Have call recordings been inventoried and key admissions flagged?
11. Has the equitable impact assessment been completed? Are protected class factors identified (with consent) and connected to specific violations?
12. Has the political landscape been assessed? Is the framing calibrated to the target audience's political psychology?
13. Is the timing/sequencing strategy documented — what goes now vs. what benefits from coordination?

### Quality Audit

- [ ] Every factual assertion sourced or labeled "unverified"
- [ ] Legal citations verified or marked `[VERIFY]`
- [ ] No conclusory labels without supporting facts
- [ ] Servicer counterargument addressed for each violation
- [ ] Servicer's enforcement history checked or flagged
- [ ] Veteran's disability status noted where relevant to protections
- [ ] State-specific requirements addressed (escrow, foreclosure procedure, CPA)
- [ ] Property tax exemption status checked against escrow calculations
- [ ] Cross-referenced current statements against prior filed documents
- [ ] Timeline gaps explicitly flagged
- [ ] SOL deadlines calculated and urgent claims flagged
- [ ] Post-foreclosure status assessed (if applicable)
- [ ] Call recording evidence inventoried
- [ ] Damages framework populated
- [ ] Equitable impact assessment completed with protected class factors identified
- [ ] Equity impact statement drafted (2-3 paragraphs, insertable into any document)
- [ ] Political landscape assessed — target audience framing calibrated
- [ ] Timing/sequencing strategy documented
- [ ] Audience-specific framing verified (not using progressive frame for conservative target or vice versa)
- [ ] NOT LEGAL ADVICE disclaimer included

### Anti-Hallucination Protocol

- Never invent statutory citations, case names, or regulatory provisions
- Mark all unverified claims with `[VERIFY: description]`
- Cross-reference current statements against prior filed documents (essential for stress-induced memory gaps)
- Do not assert rights or remedies without verified statutory or regulatory basis
- When citing VA circular letters or guidance, note they may have been superseded
- Do not assume H.R. 1815 implementation details that have not been published — the partial claim program was authorized but implementing regulations may still be pending

### Guidelines

**Trauma-informed framing:**
- Use advocate language, not clinical/shame-based language
- Acknowledge the human cost without sensationalizing
- Frame the veteran as the expert on their own experience
- Distinguish between confirmed, pending, and unknown facts
- Respect capacity constraints — if the user signals low spoons, switch to quick-start mode
- Never pressure disclosure of protected class information — offer the equity assessment, explain why it's powerful, and respect "no"

**Equity and intersectionality principles:**
- Recognize that housing instability compounds along every axis of vulnerability — a disabled BIPOC veteran spouse caring for children in a rural area with no family network is not experiencing the same foreclosure as a dual-income household with savings and extended family nearby
- Use equity data to strengthen advocacy, never to define or reduce the person
- When protected class factors are present, connect them to *specific* regulatory protections and enforcement priorities — don't just list demographics, show how the system's failure was worse *because* of those factors
- Check for intersecting harms: disability + caregiving burden + economic isolation + geographic barriers can create a cascade where each factor makes recovery from the others harder
- For community release: the equity assessment framework should be adaptable across demographics — a skill used by a VSO caseworker in rural Alabama needs the same framework as one used in urban Seattle, but the specific factors and framing will differ
- Do not assume which equity factors are relevant — ask. A veteran may not consider their race relevant to their case; another may consider it central. Follow the user's lead.

**Political strategy principles:**
- The same facts support multiple political frames — always identify at least two framings (e.g., "veteran betrayal" for conservative audiences, "corporate accountability" for progressive audiences, "system failure" for moderates)
- Never fabricate political dynamics — if the current enforcement posture of an agency is unknown, say so rather than guessing
- Track the difference between *permanent* advocacy positions (regulatory violations are violations regardless of administration) and *time-sensitive* political opportunities (a hearing next week, an election in 6 months)
- Political strategy is about sequencing and framing, not about changing the facts — every document should be factually identical regardless of audience; only the emphasis and frame change
- When advising on timing: urgent legal deadlines (SOL, eviction) always override political timing considerations. Never hold a time-sensitive filing for better political optics.
- Note which political dynamics are stable (committee jurisdiction, party platforms) vs. volatile (agency leadership, enforcement posture, media cycles) and plan accordingly

**Audience calibration:**
- Congressional (R): veteran sacrifice, government waste, failed promise, VA accountability
- Congressional (D): disparate impact, corporate pattern of abuse, housing equity, consumer protection
- Congressional (bipartisan): oversight failure, system had tools but didn't use them, taxpayer cost
- Legal: elements, evidence, procedural posture, counterarguments, novel theories
- Media: family narrative, smoking gun documents, systemic pattern, "how many more?"
- Agency — OIG: specific regulatory violations, evidence, systemic gap, prior audit confirmation
- Agency — CFPB: RESPA violations, repeat offender, consumer harm, disparate impact data
- Agency — State AG: state law hooks, harm to state residents, "first to hold them accountable"
- Family/friends: plain language, specific help needed, what they can share publicly vs. not

**Phone call delegation guidance:**
When the user indicates a household member (e.g., the veteran) can make simple phone calls:
- Provide a script-like talking point sheet for the specific call (VA hotline, servicer, VRM, congressional office)
- Include: who to ask for, what to say, what to write down, what NOT to agree to
- Keep scripts to 3-5 bullet points maximum

**Complementary tool integration (NotebookLM):**
This skill is designed to work alongside NotebookLM in a dual-tool workflow:
- Skill outputs (violation analysis, timeline, evidence gaps) can feed into NotebookLM notebooks as source documents
- NotebookLM source-gap analysis can feed back into this skill's evidence mapping step
- Recommended notebook structure: (1) Servicer Communications, (2) VA Communications & Oversight, (3) Financial Records — see `references/notebooklm-integration.md` if available

**NOT LEGAL ADVICE** — This skill produces advocacy analysis, not legal advice. Attorney review is required before filing any legal document. This skill is designed for pro se advocates, case managers, and social workers supporting veterans in housing crises.

---

## PART 2: CRISIS CASE MANAGEMENT OPERATING SYSTEM

The advocacy skill above is the analytical brain. This section is the body — the filing system, the daily checklist, the thing that catches what falls through the cracks when someone's prefrontal cortex is offline from chronic stress.

### Design principle: Crisis-proof means zero-decision-point

A person in housing crisis is operating in survival mode. Executive function is degraded. Working memory is shortened. The ability to plan, sequence, and prioritize is exactly what trauma and chronic stress attack first. This system must:

- **Never require the user to decide where to save something.** Auto-file by type, date, and source.
- **Never require the user to remember what to do next.** Surface the next action automatically.
- **Never require the user to name a file correctly.** Auto-name by convention.
- **Never require the user to check multiple places.** One dashboard shows everything.
- **Never require the user to remember what happened yesterday.** The system remembers.
- **Gracefully degrade.** If the user skips a day, a week, or a month, the system doesn't break. When they come back, it tells them what changed and what's urgent.

### Architecture: What exists now vs. what needs to be built

#### LAYER 1: What Claude can do today (no additional tools)

| Capability | How it works | Limitation |
|-----------|-------------|------------|
| **Gmail scanning** | Gmail MCP connector — Claude can search, read, and draft emails | Connected in this project; works now |
| **Google Drive scanning** | Google Drive connector — Claude can search, read, and fetch documents | Connected in this project; works now |
| **File naming enforcement** | Claude can rename files to convention when creating outputs | Only applies to files Claude creates; can't rename files on your PC |
| **Daily task list generation** | Claude can generate a prioritized task list from memory + project knowledge + calendar | Requires user to open a session; no push notifications |
| **Session handoff memory** | Claude's memory system persists key facts across conversations | Memory is append-only and has recency bias; can be edited via memory_user_edits |
| **Document analysis on upload** | Claude can read uploaded PDFs, images, docs and classify them | User must upload; Claude can't pull from local PC autonomously |
| **Calendar integration** | Google Calendar MCP — Claude can read, create, and modify events | Connected; can set deadline reminders |

#### LAYER 2: What Claude Cowork/plugins could do (requires setup)

| Capability | How | Status |
|-----------|-----|--------|
| **Automated email monitoring** | Cowork scheduled task: "Every morning, scan Gmail for new emails from Freedom Mortgage, VA, congressional offices, VRM, or NPR. Summarize and flag urgent items." | Available on Pro/Max plan via Cowork scheduled tasks |
| **Drive monitoring** | Cowork scheduled task: "Every evening, check Google Drive case folder for new/modified files. Log changes." | Available via Cowork |
| **Auto-filing from email** | Cowork plugin: when case-relevant email arrives, extract attachments, rename to convention, move to correct Drive folder | Requires custom Cowork plugin build |
| **Dashboard generation** | Cowork scheduled task: "Every morning at 7am, generate today's case dashboard and save to Google Doc." | Available via Cowork + Google Drive |

#### LAYER 3: What requires additional tools (beyond Claude alone)

| Capability | Tool needed | How it connects |
|-----------|------------|-----------------|
| **Local PC file scanning** | Claude Code (CLI) or Cowork desktop agent | Claude Code can read local filesystem; Cowork desktop agent can watch folders |
| **Paper document scanning** | Phone camera + Google Drive app (auto-upload to Drive folder) → Claude reads from Drive | Samsung phone camera → Google Drive auto-sync → Claude Drive connector |
| **Photo-to-document OCR** | Google Drive's built-in OCR on uploaded images, or Claude's native image reading | Upload photo to Drive or directly to Claude chat |
| **Push notifications** | Zapier or Google Calendar reminders triggered by Claude's scheduled tasks | Zapier MCP connector is available; Google Calendar reminders are native |
| **True automated filing** | n8n or Zapier automation: email arrives → extract attachment → rename → file to Drive folder | Requires Zapier paid plan or self-hosted n8n |
| **Offline/no-internet operation** | Samsung Notes (already in use) as fallback system | Existing workflow — analog backup |

### File naming convention (auto-applied)

Every case document should follow this pattern — Claude enforces it when creating files, and the convention guide tells users how to rename existing files:

```
[DATE]_[SOURCE]_[TYPE]_[DESCRIPTION].[ext]

DATE:       YYYYMMDD (e.g., 20260128)
SOURCE:     FM (Freedom Mortgage), VA, OIG, CFPB, WAAG (WA AG),
            CONG (Congressional), NPR, VRM, COURT, SELF, VSO
TYPE:       LTR (letter), EMAIL, STMT (statement), MOD (modification),
            COMPLAINT, BRIEF, TIMELINE, ANALYSIS, RECORDING, NOTES,
            RECEIPT, TAX, ESCROW, CREDIT, LEGAL
DESCRIPTION: 2-4 word slug in kebab-case

Examples:
20250115_FM_LTR_vasp-evaluation-promise.pdf
20250203_FM_LTR_not-reviewed-decision.pdf
20250728_VA_LTR_report-letter.pdf
20260120_SELF_COMPLAINT_oig-supplement.pdf
20260328_SELF_ANALYSIS_rate-cap-violation.md
20230601_VSO_EMAIL_semperfi-payment-attempt.pdf
20250904_FM_ESCROW_disclosure-statement.pdf
```

**For paper documents being scanned:**
1. Take photo with phone camera
2. Upload to Google Drive → `Case Files/Inbox/` folder
3. Claude reads from Inbox, renames to convention, moves to correct subfolder
4. Or: user uploads photo directly to Claude chat → Claude reads, classifies, and tells user where to save it

### Folder structure (Google Drive)

```
3714 E 5th Ave - VA Foreclosure Case/
├── 00_DASHBOARD/
│   ├── Daily_Dashboard_Current.gdoc          # Auto-updated by Cowork
│   ├── Master_Timeline.gdoc                  # Living document
│   ├── Task_Queue.gdoc                       # Priority-ordered
│   └── Advocacy_Network_Map.gdoc             # Who's doing what
├── 01_SERVICER_FM/
│   ├── Correspondence/                       # All FM letters, emails
│   ├── Statements/                           # Account statements, escrow
│   ├── Modification/                         # Mod offers, agreements
│   └── Loss_Mitigation/                      # Applications, responses
├── 02_VA/
│   ├── Correspondence/                       # VA letters, emails
│   ├── VALERI/                               # Any VALERI-related docs
│   ├── OIG/                                  # OIG complaints, supplements
│   └── Policy/                               # Circulars, M26-4, regs
├── 03_LEGAL/
│   ├── Foreclosure_Docs/                     # Notice of default, trustee deed
│   ├── Complaints_Filed/                     # CFPB, WA AG, OIG
│   ├── Credit_Disputes/                      # Bureau disputes, responses
│   ├── Attorney_Intake/                      # Packages for potential counsel
│   └── Court_Filings/                        # If litigation initiated
├── 04_CONGRESSIONAL/
│   ├── Briefs/                               # One-pagers, advocacy docs
│   ├── Correspondence/                       # Emails to/from offices
│   └── Hearing_Materials/                    # Transcripts, testimony, video notes
├── 05_MEDIA/
│   ├── NPR/                                  # NPR correspondence, shared docs
│   ├── Background_Memos/                     # Reporter packages
│   └── Published/                            # Published articles, clips
├── 06_FINANCIAL/
│   ├── Tax/                                  # Property tax exemption docs
│   ├── Escrow/                               # Escrow analysis, overcharge calc
│   ├── Payments/                             # Payment history, VSO payments
│   └── Damages/                              # Damages calculations
├── 07_PERSONAL/
│   ├── Housing_Search/                       # Rental applications, options
│   ├── Relocation/                           # Moving plans, storage
│   ├── Benefits/                             # VA benefits, disability docs
│   └── Family_Updates/                       # Weekly updates to family/friends
├── 08_RECORDINGS/
│   ├── Raw/                                  # Original recordings
│   ├── Transcripts/                          # Otter.ai / TurboScribe output
│   └── Summaries/                            # Claude-generated summaries
├── 09_RESEARCH/
│   ├── FM_Enforcement_History/               # CFPB, state AG, PACER
│   ├── Legal_Research/                       # Case law, regulations
│   └── Policy_Analysis/                      # Public comments, hearing analysis
├── Inbox/                                    # Drop zone for unsorted docs
│   └── (Claude sorts from here)
└── Archive/                                  # Superseded versions, old drafts
```

### Smart Dashboard System

The dashboard is a single Google Doc that gets regenerated daily (via Cowork scheduled task or manual Claude request). It should be the ONE thing the user looks at when they open their laptop.

**Dashboard sections:**

```
╔══════════════════════════════════════════════════╗
║  VA FORECLOSURE CASE DASHBOARD                   ║
║  Last updated: [date/time]                       ║
║  Days until Cash for Keys deadline: [X]          ║
║  Days since foreclosure sale: [X]                ║
╠══════════════════════════════════════════════════╣
║                                                  ║
║  🔴 URGENT (do today or lose something)          ║
║  • [action] — deadline [date] — [why urgent]     ║
║                                                  ║
║  🟡 THIS WEEK                                    ║
║  • [action] — [status] — [who's responsible]     ║
║                                                  ║
║  🟢 MONITORING (no action needed yet)            ║
║  • [item] — next check [date]                    ║
║                                                  ║
║  📬 NEW SINCE LAST CHECK                         ║
║  • [email from X] — [date] — [summary]           ║
║  • [new file in Drive] — [date] — [what it is]   ║
║                                                  ║
║  📊 CASE STATUS                                  ║
║  • Legal rep: [status]                           ║
║  • CFPB complaint: [filed/not filed]             ║
║  • OIG: [status]                                 ║
║  • Congressional: [status by office]             ║
║  • Media: [status]                               ║
║  • Credit disputes: [status]                     ║
║                                                  ║
║  ⏰ SOL TRACKER                                  ║
║  • [claim type] — expires [date] — [X days]      ║
║                                                  ║
║  📅 UPCOMING                                     ║
║  • [meeting/deadline] — [date] — [prep needed]   ║
║                                                  ║
║  💡 DELEGATABLE (Jerrod can handle)              ║
║  • [phone call] — [script link]                  ║
║                                                  ║
║  📝 SESSION LOG                                  ║
║  • Last session: [date] — [what was done]        ║
║  • Open items from last session: [list]          ║
╚══════════════════════════════════════════════════╝
```

**Dashboard update triggers:**
1. **Cowork scheduled task** (if set up): regenerates every morning at 7am
2. **Session open**: Claude regenerates at start of every session from memory + Drive scan + Gmail scan + calendar check
3. **Manual request**: user says "dashboard" or "what's urgent" at any time
4. **Graceful degradation**: if the user hasn't opened a session in 3+ days, the dashboard leads with "It's been [X] days. Here's what may have changed:" and runs email + Drive scans before showing tasks

### Email scanning protocol

**Automated (Cowork scheduled task):**
```
Every morning at 7:00 AM Pacific:
1. Search Gmail for new messages since last scan from:
   - Freedom Mortgage / freedommortgage.com
   - Any @va.gov address
   - VRM / James Madsen
   - Congressional offices (Murray, Baumgartner, HVAC)
   - NPR (Chris Arnold, Quil Lawrence)
   - VSOs (WWP, EDF, Semper Fi)
   - Any attorney contacts
   - Any unknown sender mentioning loan number, case, or property address
2. For each new message:
   - Extract: sender, date, subject, key content (2-3 sentences)
   - Flag urgency: URGENT (deadline, threat, legal notice) / IMPORTANT (substantive update) / FYI
   - Check for attachments — if present, note filename and type
   - Add to Dashboard → "NEW SINCE LAST CHECK"
3. For URGENT items: create a Google Calendar reminder for today
4. Check leann.r.ledford@gmail.com for any case-related emails that need forwarding
```

**Manual (any session):**
User says "scan email" or "check my email" → Claude runs the same protocol on demand.

### Document intake workflow (paper and digital)

**For paper documents arriving by mail:**
1. Take photo with phone camera (Samsung: just open camera, point, shoot)
2. Photos auto-sync to Google Photos → set up auto-backup to a Drive folder
3. OR: open Google Drive app → tap + → tap Camera → take photo → saves directly to Drive
4. Tell Claude: "I got mail from [who]" or just upload the photo
5. Claude reads the image, classifies it, suggests the filename, and tells you which folder

**For digital documents (email attachments, downloads):**
1. Save to `Inbox/` folder in Drive (or just upload to Claude)
2. Claude reads, classifies, renames, tells you where to move it
3. If Cowork plugin is set up: auto-moves to correct folder

**For documents already on local PC:**
1. Claude Code (CLI) can scan local directories if installed
2. Or: user drags files from local PC to Google Drive case folder
3. Claude scans Drive and processes anything in `Inbox/`

**File classification rules (Claude applies automatically):**

| If document contains... | Classify as | File to |
|------------------------|-------------|---------|
| Freedom Mortgage letterhead or return address | FM correspondence | 01_SERVICER_FM/Correspondence/ |
| VA letterhead, @va.gov sender | VA correspondence | 02_VA/Correspondence/ |
| Escrow statement, payment breakdown | Financial - escrow | 06_FINANCIAL/Escrow/ |
| Credit report, credit bureau | Credit | 03_LEGAL/Credit_Disputes/ |
| Congressional office letterhead | Congressional | 04_CONGRESSIONAL/Correspondence/ |
| Court filing, legal notice, trustee | Legal - foreclosure | 03_LEGAL/Foreclosure_Docs/ |
| Property tax statement | Financial - tax | 06_FINANCIAL/Tax/ |
| Unknown / unclear | Hold in Inbox | Inbox/ (flag for user review) |

### Memory and continuity system

**Problem:** Claude's memory updates periodically but has recency bias and can lose older context. The session handoff system (Samsung Notes → Activity Log → CLAUDE.md) works but requires executive function to maintain.

**Solution: Layered redundancy**

| Layer | What it does | Who maintains it | Failure mode |
|-------|-------------|-----------------|--------------|
| **Claude memory** | Persists key facts, contacts, case status across sessions | Claude (automatic) | Recency bias; may lose older details |
| **Claude Project Knowledge** | Case documents, analysis, guides always available | User uploads; Claude reads | Static — doesn't auto-update |
| **Google Drive dashboard** | Living document with current status, tasks, timeline | Claude regenerates (scheduled or manual) | Goes stale if no sessions for days |
| **Samsung Notes activity log** | Append-only offline record of what happened each session | User pastes session close summary | Works offline; survives internet outage |
| **CLAUDE.md** | Persistent instructions for Claude Code sessions | User updates after major developments | Only for Claude Code; not claude.ai |
| **Google Calendar** | Deadlines, meetings, SOL dates, monitoring schedule | Claude creates events; user gets phone alerts | Push notifications even when not in a session |
| **Gmail drafts** | Staged emails ready to send | Claude drafts; user reviews and sends | Persists across sessions; user can send from phone |

**The key insight:** Google Calendar is the only system that can *push* to the user without them initiating a session. Every critical deadline should exist as a Calendar event with a reminder. This is the safety net when the user can't open Claude for days.

### Crisis-proof daily protocol (what it looks like in practice)

**If the user has 5 minutes:**
1. Check phone for Google Calendar alerts (deadlines, meetings)
2. Open Dashboard Google Doc on phone — read red items only
3. Done. They know what's urgent.

**If the user has 20 minutes:**
1. Open Claude → "dashboard" → Claude regenerates with fresh email/Drive scan
2. Handle the single most urgent red item
3. Claude auto-updates the dashboard
4. Done.

**If the user has an hour:**
1. Open Claude → "dashboard" → full scan
2. Work through red and yellow items
3. Claude drafts whatever's needed (email, complaint section, phone script for Jerrod)
4. Session close summary → Samsung Notes
5. Dashboard auto-updates

**If the user hasn't been able to open Claude for a week:**
1. Open Claude → "I've been offline for a week, what did I miss?"
2. Claude scans Gmail for all new case-related emails
3. Claude scans Drive for any new files
4. Claude checks Calendar for any passed or upcoming deadlines
5. Claude regenerates dashboard with "MISSED" items flagged
6. Produces a catch-up brief: "Here's what happened while you were away, here's what's now urgent"
7. No judgment. No "you should have..." — just facts and next actions.

### Implementation plan for the operating system

**Phase 1: Immediate (today/this week — no new tools required)**
- [ ] Create the Google Drive folder structure above
- [ ] Move existing case files into the correct folders
- [ ] Create the Dashboard Google Doc (Claude can generate the first version now)
- [ ] Set up Google Calendar events for all known deadlines (April 3 Cash for Keys, SOL dates, Monday meeting)
- [ ] Create a "scan email" and "dashboard" shortcut in session opening prompt
- [ ] Post the file naming convention somewhere visible (Samsung Notes or printed)

**Phase 2: Near-term (this week/next — Cowork setup)**
- [ ] Set up Cowork scheduled task: daily email scan at 7am
- [ ] Set up Cowork scheduled task: daily dashboard regeneration
- [ ] Set up Cowork scheduled task: weekly Drive scan for new/modified files
- [ ] Set up auto-backup from Samsung phone camera to Google Drive Inbox folder
- [ ] Test the paper document → phone photo → Drive → Claude classification workflow

**Phase 3: Future (when capacity allows)**
- [ ] Evaluate Claude Code CLI for local PC file scanning
- [ ] Evaluate Zapier connector for true automated email → Drive filing
- [ ] Evaluate n8n for more complex automation (if self-hostable)
- [ ] Build Cowork plugin for auto-filing email attachments to correct Drive folders
- [ ] Consider whether the dashboard should be a React artifact with persistent storage instead of a Google Doc

---

## REFERENCE FILES (to be built)

### Part 1: Advocacy Skill Reference Files

| File | Contents | Priority |
|------|----------|----------|
| `regulatory-framework.md` | Key provisions from 38 CFR 36.4319, M26-4 Ch.5, RESPA §6/§1024.17/.35/.36/.41, RCW 61.24, CARES Act §4022, H.R. 1815 §3(h), RCW 84.36.381 | HIGH |
| `violation-checklist.md` | Detailed checklist for each of the 9 violation categories with elements, evidence needed, servicer counterarguments, and rebuttal frameworks | HIGH |
| `damages-framework.md` | Calculation templates for escrow overcharges, statutory damages, consequential damages, VSO interference, fee-shifting, state CPA multipliers | HIGH |
| `agency-filing-guide.md` | How to file with CFPB, VA OIG, WA AG (OMVLA + Consumer Protection), credit bureaus — URLs, formats, required info, FOIA/QWR templates | HIGH |
| `sol-tracker.md` | Statute of limitations by claim type, clock-start events, state-specific variations | HIGH |
| `equity-assessment-guide.md` | Protected class factors, intersectionality analysis, disparate impact data sources, equity impact statement templates, informed consent language | HIGH |
| `post-foreclosure.md` | 38 U.S.C. §3732 options, Cash for Keys analysis framework, lease-back authority, REO disposition, occupancy rights by state, decision tree | MEDIUM |
| `political-strategy-guide.md` | Congressional calendar references, committee jurisdiction mapping, partisan framing matrices, agency enforcement posture assessment, election cycle timing, sequencing templates | MEDIUM |
| `timeline-template.md` | Blank chronological evidence framework with column headers, gap-flagging instructions, VSO interference tracking | MEDIUM |
| `document-templates.md` | Templates for congressional one-pager, OIG supplement, CFPB narrative, credit dispute, media background memo, legal intake summary | MEDIUM |
| `call-recording-guide.md` | How to process servicer call recordings: what to listen for, transcript summary format, flagging admissions against interest | MEDIUM |
| `servicer-audit-guide.md` | How to research a servicer's enforcement history (CFPB, state AG, consent orders, HMDA, PACER, BBB, Ginnie Mae) with search URLs | MEDIUM |
| `phone-scripts.md` | Delegatable phone call scripts for VA hotline, servicer, VRM/Cash for Keys, congressional offices | LOW |
| `de-identification.md` | Guide for community release: what to replace, what to keep, how to adapt for other states | LOW |
| `notebooklm-integration.md` | Recommended notebook structure, starter prompts, how to feed skill outputs into NotebookLM and vice versa | LOW |

### Part 1b: Recommended Claude Styles (shipped with the skill)

No existing Claude skill ships with recommended styles. This is a trauma-informed quality control measure — the user doesn't have to figure out how to get good formatting. They install the style, and every output is automatically optimized for their context.

Each style file contains: the style description (copy-paste into Claude Settings → Style), when to use it, what it optimizes for, and a short before/after example.

| Style | When to use | Optimizes for |
|-------|------------|---------------|
| **Field Manual** (default) | All skill outputs, case analysis, reference doc reading, daily dashboard | Neurodivergent/crisis-optimized scannability: chunked paragraphs (3-4 sentences max), headings/subheaders, bullets, tables, bold key terms, plain language with inline definitions, no shame-based language, inverted pyramid (most important info first), active voice, no filler phrases |
| **Congressional Brief** | Drafting one-pagers, advocacy briefs, emails to congressional offices | Formal but accessible, policy-focused, numbers over adjectives, partisan-calibrated framing, 1-page constraint awareness, specific asks at the end |
| **Plain Language** | Outputs shared with family, friends, VSO caseworkers, community members, non-expert audiences | 8th-grade reading level, no jargon, short sentences, concrete examples, "what this means for you" framing, empathetic tone |
| **Legal Intake** | Attorney-facing documents, legal intake summaries, case analysis for counsel | Elements-focused, procedural posture, citation-heavy, counterargument structure, assumes legal literacy, professional-formal tone |

**Setup instructions for users (included in README):**
1. Download the skill package
2. Upload SKILL.md to Claude (Settings → Capabilities → Skills)
3. Go to Settings → Style → Create style
4. Open `styles/field-manual.md`, copy the description block, paste into the style creator
5. Name it and save
6. Switch styles as needed when generating different output types

**Why this matters:** A person in crisis who downloads this skill and gets a wall of dense unformatted text from Claude will not use it again. The style ensures every interaction is immediately usable regardless of the user's current cognitive capacity. This is the same principle as the zero-decision-point OS design — remove the formatting burden from the user entirely.

### Part 2: Operating System Reference Files

| File | Contents | Priority |
|------|----------|----------|
| `file-naming-convention.md` | Full naming convention with examples for every document type, classification rules, and a printable quick-reference card | HIGH |
| `folder-structure-setup.md` | Google Drive folder creation guide with step-by-step instructions, what goes where, and the Inbox workflow | HIGH |
| `dashboard-template.md` | Dashboard Google Doc template with all sections, auto-generation prompt for Claude/Cowork, and manual refresh instructions | HIGH |
| `email-scan-protocol.md` | Gmail scan configuration: sender watchlist, urgency classification rules, attachment handling, Cowork scheduled task setup | HIGH |
| `crisis-daily-protocol.md` | The "what to do" card for 5-minute, 20-minute, and 1-hour sessions, plus the "I've been offline" recovery protocol — designed to be printed and posted on the fridge | HIGH |
| `paper-scan-workflow.md` | Step-by-step: phone photo → Drive → Claude classification, with Samsung-specific camera/Drive app instructions and screenshots | MEDIUM |
| `cowork-setup-guide.md` | How to set up Cowork scheduled tasks for email scanning, dashboard generation, and Drive monitoring | MEDIUM |
| `calendar-deadline-setup.md` | All known deadlines as Google Calendar events with reminder settings, plus how to add new ones | MEDIUM |

---

## BUILD PLAN

### Phase 1a: Core advocacy skill (this week)
- [ ] Write SKILL.md for `va-foreclosure-case-analyzer`
- [ ] Write `regulatory-framework.md` reference file
- [ ] Write `violation-checklist.md` reference file (with counterarguments)
- [ ] Write `damages-framework.md` reference file
- [ ] Write `sol-tracker.md` reference file
- [ ] Test against Ledford case documents
- [ ] Iterate based on output quality

### Phase 1b: Operating system foundation (this week — no new tools)
- [ ] Create Google Drive folder structure
- [ ] Move existing case files into correct folders using naming convention
- [ ] Create Dashboard Google Doc (Claude generates first version)
- [ ] Set up Google Calendar events for all known deadlines
- [ ] Print crisis daily protocol card (5min / 20min / 1hr versions)
- [ ] Write `file-naming-convention.md` (printable quick-reference)
- [ ] Write `crisis-daily-protocol.md` (printable, fridge-postable)
- [ ] Test paper document → phone photo → Drive → Claude classification workflow

### Phase 2a: Companion advocacy skills (next week)
- [ ] `va-complaint-drafter` — CFPB, OIG, state AG complaint generation
- [ ] `va-congressional-brief` — advocacy document generation
- [ ] `va-credit-dispute` — FCRA/CARES dispute letters
- [ ] `va-post-foreclosure-advisor` — Cash for Keys analysis, occupancy rights, §3732 options
- [ ] Write remaining advocacy reference files

### Phase 2b: Operating system automation (next week — Cowork setup)
- [ ] Set up Cowork scheduled task: daily email scan at 7am Pacific
- [ ] Set up Cowork scheduled task: daily dashboard regeneration
- [ ] Set up Cowork scheduled task: weekly Drive scan
- [ ] Set up Samsung phone → Google Drive auto-sync for photos
- [ ] Write `cowork-setup-guide.md`
- [ ] Write `email-scan-protocol.md`
- [ ] Test full workflow: mail arrives → photo → Drive → Claude classifies → dashboard updates

### Phase 3: Community release (when ready)
- [ ] De-identify all Ledford-specific content using `de-identification.md` protocol
- [ ] Write README for GitHub (outcomes, install instructions, screenshots, disclaimers)
- [ ] Adapt state-specific references for at least 2-3 other states (TX, CA, FL — highest VA foreclosure volume)
- [ ] Adapt operating system for generic use (remove Ledford-specific folder contents, keep structure)
- [ ] Submit to lawvable/awesome-legal-skills (AGPL-3.0 compatible)
- [ ] Submit to agentskills.legal / CaseMark (Apache 2.0 — check compatibility)
- [ ] Submit to skills.sh directory for install-count tracking
- [ ] Consider MCP server integration via `https://skills.case.dev/api/mcp` for auto-discovery
- [ ] License decision: Apache 2.0 (maximum adoption) vs. AGPL-3.0 (prevents commercial appropriation without contribution)
- [ ] Write case study / blog post for MSW audience: "Building a Crisis Case Management OS with AI"

---

## WHY THIS MATTERS BEYOND ONE CASE

Per the March 26 HVAC hearing, 30,000+ veterans face payment increases under the draft M26-4 Ch.5 waterfall. 75% of VA foreclosures go to REO vs. <50% for GSEs/FHA. The VA Home Loan Reform Act created partial claim authority but implementation is still pending 8+ months later.

A well-built skill that any veteran, VSO caseworker, legal aid attorney, or congressional staffer can upload to Claude and immediately use to analyze a VA foreclosure case would be — as far as we can find — the first of its kind. It turns Leann's hard-won case expertise into a reusable tool for every veteran facing the same system failures.

**Target users for community release:**
- Pro se veterans and military families facing foreclosure
- VSO caseworkers (WWP, DAV, VFW, American Legion) who handle housing cases
- Legal aid attorneys at organizations like NVLSP, Veterans Consortium, NJP, Veterans Legal Institute
- Congressional constituent services staff handling VA housing complaints
- Social workers and MSW students working with veteran populations
- Investigative journalists covering VA mortgage servicing
- State AG consumer protection divisions handling mortgage complaints

**What makes this skill different from corporate legal skills:**
- Built from the borrower's perspective, not the lender's
- Assumes the user may not be an attorney (pro se / advocate framing)
- Includes trauma-informed language guidance
- Has a low-spoon quick-start mode for users with limited capacity
- Integrates servicer counterargument analysis (what they'll say and why it fails)
- Tracks downstream harm multipliers (VSO interference, escrow compounding)
- Includes practical delegation tools (phone scripts for household members)
- Designed for multi-tool workflows (Claude + NotebookLM)
- **Equitable impact assessment** — analyzes how violations produce disproportionate harm along axes of disability, race, gender, age, geography, economic isolation, and household composition; generates insertable equity impact statements for any advocacy document
- **Political strategy layer** — assesses congressional dynamics, agency enforcement posture, election cycles, and partisan psychology; produces audience-calibrated framing for the same case facts; includes timing and sequencing guidance
- **Intersectionality-aware** — recognizes that a disabled BIPOC veteran spouse with children in a rural area experiences foreclosure differently than the "generic borrower" in every other legal skill, and builds advocacy that reflects that reality
- **Ships with recommended Claude styles** — four pre-built custom styles (Field Manual, Congressional Brief, Plain Language, Legal Intake) so every output is automatically formatted for its audience and the user's cognitive context. No other skill in the ecosystem does this. This is a trauma-informed quality control measure that eliminates formatting decisions entirely.

---

## CHANGELOG

**v4.1 (March 29, 2026):**
- Added `styles/` directory to skill package architecture (4 styles: Field Manual, Congressional Brief, Plain Language, Legal Intake)
- Added Part 1b: Recommended Claude Styles section to reference files with full descriptions, use cases, and setup instructions
- First skill in the Claude ecosystem to ship with pre-built custom styles as a trauma-informed quality control measure
- Added styles to "what makes this different" differentiators list

**v4 (March 28, 2026):**
- Added Part 2: Crisis Case Management Operating System
- Added automated file naming convention with classification rules
- Added Google Drive folder structure (10 top-level folders, ~30 subfolders)
- Added smart dashboard system with auto-generation protocol
- Added email scanning protocol (automated via Cowork + manual fallback)
- Added paper document intake workflow (phone photo → Drive → Claude classification)
- Added memory and continuity system (6-layer redundancy model)
- Added crisis-proof daily protocol (5min / 20min / 1hr / offline-recovery versions)
- Added 3-layer architecture assessment (what Claude does now / Cowork can do / requires additional tools)
- Added 8 new operating system reference files
- Added implementation plan for operating system (3 phases matching skill phases)
- Split build plan into parallel tracks: advocacy skill (a) + operating system (b)
- Added "crisis-proof means zero-decision-point" as core design principle
- Total reference files: 23 (15 advocacy + 8 operating system)

**v3 (March 28, 2026):**
- Added Step 4: Equitable Impact Assessment — disparate impact analysis across disability, race/ethnicity, gender, LGBTQ+, age, children, multigenerational households, rural/urban, economic/generational context, support network presence/absence
- Added system failure equity analysis (did the regulatory system itself fail this household inequitably?)
- Added equity impact statement output (2-3 paragraphs, insertable into any advocacy document)
- Added Step 10b: Political landscape assessment — congressional session status, election cycle, committee composition, partisan framing, agency enforcement posture, pending legislation/rulemaking, media cycle, opposing political dynamics
- Added Step 10c: Audience-specific framing matrix with partisan psychology guidance
- Added Step 10d: Timing and sequencing strategy
- Added household equity profile to Case Intake (item 11) with informed consent language
- Added equity and intersectionality principles to Guidelines
- Added political strategy principles to Guidelines
- Expanded audience calibration with partisan-specific framing (R, D, bipartisan)
- Added `equity-assessment-guide.md` reference file (HIGH priority)
- Added `political-strategy-guide.md` reference file (MEDIUM priority)
- Expanded Checkpoint B from 10 to 13 verification items
- Expanded Quality Audit from 15 to 20 checklist items
- Expanded reference files from 13 to 15
- Total workflow steps: 13 (was 10 in v2, 5 in v1)

**v2 (March 28, 2026):**
- Added violation #9: Escrow overcharge / property tax exemption failure
- Added servicer counterargument + rebuttal framework to each violation
- Added VSO payment interference as a distinct harm multiplier
- Added damages assessment framework (Step 4)
- Added statute of limitations tracker (Step 5)
- Added post-foreclosure status assessment (Step 6)
- Added records request / evidence gathering guidance (Step 7)
- Added servicer enforcement history audit (Step 8)
- Added call recording analysis guidance
- Added low-spoon quick-start mode
- Added phone call delegation scripts concept
- Added NotebookLM integration guidance
- Added de-identification protocol for community release
- Added MCP server integration path for agentskills.legal
- Added multi-state adaptation plan for Phase 3
- Added target user list for community release
- Expanded Checkpoint B from 5 to 10 verification items
- Expanded Quality Audit from 9 to 15 checklist items
- Expanded reference files from 7 to 13
- Expanded build plan Phase 3 with specific distribution targets

---

*This scope document is a working draft. The skill itself should be built iteratively using Claude's skill-creator workflow with test cases drawn from the Ledford case documents.*
