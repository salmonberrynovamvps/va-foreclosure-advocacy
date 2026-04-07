---
name: va-complaint-drafter
description: >
  Drafts ready-to-file complaints and records requests for VA mortgage
  foreclosure cases. Produces formatted narratives for CFPB complaints,
  VA OIG supplements, state AG complaints, credit bureau disputes, FOIA
  requests, and Qualified Written Requests. Use when someone says "draft
  my CFPB complaint," "file a complaint," "write a dispute letter,"
  "draft a FOIA," "write a QWR," or "help me file with [agency]." Also
  trigger when someone has completed a violation analysis and needs to
  convert findings into filings. Works standalone or as a companion to
  va-foreclosure-case-analyzer. Built for pro se advocates, veterans,
  case managers, and social workers — not corporate compliance.
metadata:
  author: Leann Ledford
  version: 1.0.0
  domain: veteran-housing-advocacy
  jurisdiction: US-federal, WA-state
  license: Apache-2.0
  companion-to: va-foreclosure-case-analyzer
---

# VA Complaint Drafter

Converts case analysis into ready-to-file complaints and records requests.
Companion skill to `va-foreclosure-case-analyzer`.

**Who this is for:** Veterans, military families, case managers, social
workers, and pro se advocates who need to turn identified violations
into actual filings.

**What it produces:** Copy-paste-ready narratives formatted for each
agency's specific requirements, with filing instructions.

**NOT LEGAL ADVICE.** These are advocacy drafts. Attorney review is
recommended before filing any legal document.

---

## Quick-Start Mode

If the user says "draft my CFPB complaint" or similar without a full
case analysis:

1. Ask: What is the servicer's name, your loan number, and the 1-2
   most important things they did wrong?
2. Draft a basic complaint narrative using only what's provided
3. Flag what's missing and would strengthen the filing
4. Offer to run the full analysis if the root skill is available

Do not require a complete case file to draft a basic complaint.
Something filed is better than a perfect document never filed.

---

## Supported Filing Types

| Filing | Agency/Target | Format | Character/page limits |
|--------|-------------|--------|----------------------|
| **CFPB complaint** | Consumer Financial Protection Bureau | Online narrative + attachments | ~10,000 characters for narrative `[VERIFY]` |
| **VA OIG complaint** | VA Office of Inspector General | Online form narrative | No hard limit; 2-3 pages recommended |
| **VA OIG supplement** | Same — adds to existing complaint | Letter format referencing existing case # | 1-2 pages |
| **State AG complaint** | State Attorney General (WA default) | Online form or letter | Varies by state |
| **Credit bureau dispute** | Equifax, Experian, TransUnion | Letter or online form | Per-item disputes; 1-2 pages per bureau |
| **FOIA request** | VA Regional Loan Center | Formal letter | 1-2 pages |
| **QWR** | Mortgage servicer | Certified letter | 1-2 pages |

---

## Drafting Workflow

### Step 1: Identify What to Draft

Ask the user or infer from context:

- Which filing(s) do you need right now?
- Has the root skill analysis been completed? (If yes, pull violations,
  evidence, damages, and enforcement history from that analysis)
- Any filing deadlines? (SOL, response windows, eviction timelines)
- Has anything already been filed? (Reference existing complaint numbers)

**Sequencing guidance** (from agency-filing-guide.md):
1. CFPB first (creates record, forces servicer response)
2. Credit disputes (30-day clock starts)
3. OIG supplement (if existing complaint)
4. Congressional inquiry (long timeline, start early)
5. State AG (reference CFPB complaint)
6. FOIA (20+ days, results feed everything)
7. QWR (30 days, may reveal new violations)

---

### Step 2: Gather Case Details

For any filing, collect these minimums:

**Required for all filings:**
- Borrower name(s) and contact information
- Servicer legal name
- Loan number
- Property address
- Brief description of what happened (chronological)

**Strengthens the filing (get if available):**
- Specific violation categories with dates
- Regulatory citations (from root skill analysis)
- Supporting documents (list what exists)
- Servicer's enforcement history
- Prior complaint numbers (OIG, CFPB, AG)
- Veteran disability rating and status
- Dollar amounts (damages, overcharges)

---

### Step 3: Draft the Filing

Use the appropriate template below. Output in **plain text** that
copies cleanly into web forms or word processors.

After each draft, provide:
- Where to file (URL or address)
- What to attach
- Expected response timeline
- What happens after filing

---

## CFPB Complaint Template

### Form fields (consumerfinance.gov/complaint)

Product: Mortgage
Sub-product: VA mortgage
Issue: [select closest match]
  - "Struggling to pay mortgage" for loss mitigation failures
  - "Trouble during payment process" for escrow/payment issues
  - "Closing on a mortgage" for modification terms issues
Company: [servicer legal name]

### Narrative structure

Draft in this exact order. Keep total narrative under 10,000 characters.

**Paragraph 1: Who we are (3-4 sentences)**
- Veteran status, disability rating, branch
- Loan type (VA-guaranteed), property address, original terms
- Current status (in home, foreclosed, displaced)
- Family composition if relevant (caregiver, children — de-identify minors)

**Paragraph 2: What the servicer did (chronological, 1-2 paragraphs)**
- Start with the first failure point
- Dates, specific actions, specific documents
- No adjectives — let the facts carry the weight
- Each sentence should be independently verifiable

**Paragraph 3: Specific violations (bulleted list)**
For each violation:
- Name the regulation
- State what it requires (one sentence)
- State what the servicer did instead (one sentence)
- State the evidence (document name or date)

**Paragraph 4: Harm (1 paragraph)**
- Financial: dollar amounts (overcharges, lost equity, costs)
- Housing: displacement, instability, loss of home
- Credit: false reporting, denied applications
- Health: if relevant and borrower consents
- Third-party rescue failures (VSO payments defeated)

**Paragraph 5: What we want (bulleted list)**
- Specific, actionable requests
- Investigation of servicer's pattern of conduct
- Referral to enforcement division
- Referral to Repeat Offenders Unit (if enforcement history supports)

**Paragraph 6: Pattern evidence (1-2 sentences, if available)**
- Total penalties from enforcement history
- Prior consent orders involving same conduct

### Closing
- Include contact information
- State willingness to provide additional documentation
- Reference any other pending complaints (OIG #, state AG)

---

## VA OIG Supplement Template

For adding new evidence to an existing OIG complaint.

TO: VA Office of Inspector General
RE: Supplemental Information — Case Reference [OIG number]
Date: [date]

Dear OIG Investigator:

I am writing to supplement my complaint filed [original date],
Reference Number [number], with the following new information:

NEW EVIDENCE:
[Numbered list — each item with date, description, and significance]

CONNECTION TO ORIGINAL COMPLAINT:
[1-2 sentences connecting new evidence to the oversight failures
identified in the original filing]

UPDATED REQUEST:
[What you want OIG to do with this new information]

Respectfully,
[Name, contact info, loan number]

---

## Filing Instructions Quick Reference

| Filing | Where | Method | Response time |
|--------|-------|--------|--------------|
| **CFPB** | consumerfinance.gov/complaint | Online form | 15 days (servicer must respond) |
| **VA OIG** | va.gov/oig/hotline | Online form | 6 weeks (initial review) |
| **WA AG** | atg.wa.gov/file-complaint | Online form | Varies |
| **Equifax** | equifax.com/personal/credit-report-services/credit-dispute | Online or mail | 30 days |
| **Experian** | experian.com/disputes | Online or mail | 30 days |
| **TransUnion** | transunion.com/credit-disputes | Online or mail | 30 days |
| **FOIA** | va.gov/foia | Mail to RLC | 20 business days |
| **QWR** | Servicer's designated address | **Certified mail only** | 30 business days |

---

## Guidelines

### Trauma-informed drafting
- Write in the borrower's voice, not a lawyer's voice
- Factual, not emotional — the facts ARE emotional enough
- No shame language, no "we failed to" — frame as servicer's actions
- If capacity is limited, draft the single highest-priority filing first

### When to stop and get an attorney
- If filing a lawsuit
- If negotiating a settlement with legal releases
- If the servicer responds to the CFPB complaint with a settlement offer
- If a bankruptcy stay is needed
- Draft the complaint, file it, and note "attorney review recommended
  for next steps" — don't let the need for an attorney prevent filing
  the complaint itself
