---
name: va-congressional-brief
description: >
  Drafts congressional advocacy documents for VA mortgage foreclosure
  cases. Produces one-page briefs, staffer emails, hearing testimony,
  public comments, and constituent inquiry packages. Calibrates framing
  to the target audience's political psychology (Republican fiscal,
  Democratic equity, bipartisan oversight). Use when someone says "draft
  a one-pager," "write a congressional brief," "email the staffer,"
  "prepare hearing testimony," "draft a public comment," or needs any
  document for a congressional office, committee staff, or legislative
  audience. Works standalone or as a companion to
  va-foreclosure-case-analyzer. Built for pro se advocates, veterans,
  case managers, VSO caseworkers, and social workers.
metadata:
  author: Leann Ledford
  version: 1.0.0
  domain: veteran-housing-advocacy
  jurisdiction: US-federal
  license: Apache-2.0
  companion-to: va-foreclosure-case-analyzer
---

# VA Congressional Brief Drafter

Converts case analysis into politically calibrated congressional
advocacy documents. Companion skill to `va-foreclosure-case-analyzer`.

**Who this is for:** Veterans, case managers, VSO caseworkers, and
advocates who need to communicate with congressional offices.

**What it produces:** One-pagers, staffer emails, testimony drafts,
public comments, and constituent inquiry packages — each calibrated
to the target audience's political incentives.

**NOT LEGAL ADVICE.** These are advocacy documents.

---

## Quick-Start Mode

If the user says "draft a one-pager for my congressman" without a
full analysis:

1. Ask: Who is the target (name/party/committee)? What's the single
   most important thing you need them to do?
2. Draft a basic one-pager with available facts
3. Flag what's missing
4. Offer to calibrate framing once target is identified

---

## Supported Document Types

| Document | Audience | Length | Purpose |
|----------|---------|--------|---------|
| **One-page brief** | Congressional office, first contact | 1 page strict | Get attention, establish the case, make the ask |
| **Staffer email** | Specific staffer (constituent services or policy) | 3-5 paragraphs | Follow up, provide update, make specific request |
| **Constituent inquiry package** | Congressional office submitting to VA | 1-page brief + privacy release + key docs | Get the office to submit a formal inquiry on your behalf |
| **Public comment** | Rulemaking docket (VA, CFPB) | Varies (often 5-15 pages) | Put your case on the official record of a regulatory proceeding |
| **Hearing testimony** | Committee hearing (written or oral) | 5 min oral / 5-10 pages written | Present your case to committee members on the record |
| **Committee staff memo** | Committee policy/oversight staff | 2-3 pages | Provide the analytical depth staff need to act |

---

## Partisan Framing Engine

**Core rule:** The facts never change. The frame does. Every document
must be factually identical regardless of audience — only the emphasis
and lead change.

### Step 1: Identify the target

| Info needed | Why it matters |
|------------|---------------|
| **Name** | Personalize the ask |
| **Party** | Sets the framing frame |
| **Committee(s)** | Determines jurisdiction and leverage |
| **Role** | Chair vs. ranking vs. member changes the ask |
| **State/district** | Local angle if applicable |
| **Prior statements** | Has this member spoken on VA housing? Quote them back. |

### Step 2: Select the frame

**Republican / Conservative:**
- Lead: Failed promise to a veteran. Government waste.
- Data: Fiscal cost ($72K per foreclosure vs. $0 partial claim).
  75% VA foreclosures go to REO. Total govt cost $195K+ per family.
- Language: "promise kept/broken," "taxpayer dollars wasted," "the
  system had the tools and didn't use them"
- Avoid leading with: racial disparity framing, "corporate greed"

**Democratic / Progressive:**
- Lead: Disparate impact on disabled veteran family. Corporate
  pattern. Housing equity failure.
- Data: Servicer enforcement history ($130M+ penalties). HMDA
  disparities if available. Equity impact statement.
- Language: "held accountable," "pattern of abuse," "protecting
  the most vulnerable"
- Avoid leading with: "government is the problem," anti-regulation

**Bipartisan / Moderate:**
- Lead: Oversight failure. System had the tools, didn't use them.
- Data: Both fiscal AND equity. OIG's own prior audit findings.
- Language: "accountability," "fixable problem," "this shouldn't
  happen to any veteran"
- Avoid: strongly partisan framing in either direction

### Step 3: Draft with the frame applied

Every document follows the same skeleton, but the lead and emphasis
shift based on the frame selected in Step 2.

---

## One-Page Brief Template

Strict 1-page constraint. Use Congressional Brief style if installed.

[HEADER: Veteran name, property, loan number, date]

ISSUE (2 sentences max)
[Frame-appropriate lead. State the core problem and the specific
failure in two sentences.]

KEY FACTS (bulleted, 5-7 bullets max)

VIOLATIONS IDENTIFIED (table or short list)
| Violation | Regulation | Evidence |

[FRAME-SPECIFIC SECTION — choose one:]

FOR REPUBLICAN TARGETS:
COST TO TAXPAYERS
- Foreclosure cost: ~$72K direct (Cohen testimony, 3/26/26 HVAC)
- Total 3-year govt cost: ~$195K+ per family
- Partial claim alternative: $0 immediate outlay

FOR DEMOCRATIC TARGETS:
EQUITY IMPACT
- Disability, household composition, protected class factors
- Servicer enforcement history — pattern evidence
- Disparate impact data if available

FOR BIPARTISAN TARGETS:
OVERSIGHT FAILURE
- What the system was supposed to do
- What the system actually did
- The specific, fixable gap

CURRENT STATUS (3-4 bullets)

THE ASK (numbered, 1-3 specific requests)

[FOOTER: Contact info, case identifiers]

---

## Staffer Email Template

Subject: [Veteran family / property address] — [specific request]

[Staffer first name],

[1 sentence: why you're writing]

[1 paragraph: the situation in 3-4 sentences. Frame-appropriate.
Include the single most compelling fact.]

[1 paragraph: what you're asking for. Specific, actionable.
Include timeline if there's a deadline.]

[1 sentence: what you're attaching or offering to provide.]

[Signature block with case identifiers]

---

## Constituent Inquiry Package

What to include when asking a congressional office to submit a
formal inquiry to VA on your behalf:

1. **One-page brief** (from template above)
2. **Signed privacy release** (the office provides their form)
3. **Key supporting documents** (3-5 maximum):
   - Modification offer showing rate cap violation
   - VASP promise then "Not Reviewed" decision sequence
   - NOE/RFI with no response
   - Most recent eviction/CFK notice
   - OIG complaint confirmation
4. **Document index** (one page listing what you're providing)

**Do NOT send the full case file unsolicited.** Staff are busy.
Send the brief and offer more on request.

---

## Public Comment Template

For VA rulemaking (M26-4 Chapter 5), CFPB proposed rules, etc.

COMMENT ON [DOCKET/CIRCULAR NUMBER]

Submitted by: [name]
Date: [date]
Re: [title of the proposed rule/circular]

I. COMMENTER BACKGROUND
II. SUMMARY OF COMMENT
III. SPECIFIC PROVISIONS
IV. REAL-WORLD IMPACT
V. RECOMMENDATIONS

---

## Hearing Testimony Template (Written)

WRITTEN TESTIMONY OF [NAME]
Before the [Committee name]
[Subcommittee name, if applicable]
[Hearing title]
[Date]

[OPENING — 1 paragraph, personal, frame-appropriate]
[THE STORY — 2-3 paragraphs, chronological, factual]
[THE SYSTEMIC ISSUE — 1-2 paragraphs]
[THE ASK — 1 paragraph]
[CLOSING — 2-3 sentences]

---

## Court Filing Scanner Protocol

**This is an automation task — belongs in Cowork/scheduled tasks.**

### Daily check protocol

**Frequency:** Every morning, 9:00 AM local time

**What to search:**

| Court | URL | Search term |
|-------|-----|------------|
| Superior Court (handles UD) | [county court viewer URL] | Borrower last name |
| Superior Court | Same | "Secretary of Veterans Affairs" |
| District Court (also handles evictions) | [county court viewer URL] | Borrower last name |

**If a filing appears:**
1. Screenshot/save immediately
2. Call legal aid (NJP, eviction defense line) SAME DAY
3. Call congressional office SAME DAY
4. Note: you have **20 days from SERVICE** (not filing) to respond
5. Evaluate emergency bankruptcy filing for automatic stay

---

## Post-Draft Checklist

- [ ] Target audience identified (party, committee, role)
- [ ] Frame applied consistently throughout
- [ ] All facts sourced or marked unverified
- [ ] One-pager fits on one page (print preview)
- [ ] Specific ask included with timeline
- [ ] Contact info and case identifiers in footer
- [ ] No legal jargon without plain-language explanation
- [ ] Minors de-identified
- [ ] Prior filings referenced (OIG #, CFPB #)
- [ ] Attachments listed
- [ ] NOT LEGAL ADVICE noted (for user, not in the document)

---

## Guidelines

### Tone calibration
- Congressional documents are formal but accessible
- Numbers over adjectives
- Specific over general
- Respectful of the office's time

### Timing awareness
- Session vs. recess affects responsiveness
- Hearing dates create urgency windows
- Election cycles affect willingness to engage
- SOL deadlines override political timing — always

### What congressional offices actually do
- Submit formal inquiry to VA (through OCLA)
- Request information from agencies
- Convene meetings between constituents and agencies
- Hold hearings (committee-level)
- Write letters to agency heads
- They do NOT litigate, file complaints, or represent you in court
