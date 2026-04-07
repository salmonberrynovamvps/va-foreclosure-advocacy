# Violation Checklist for VA Mortgage Foreclosure Cases

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Step 2.

Covers all 9 violation categories. For each: the legal standard, elements
to prove, evidence to gather, what the servicer will argue, and why that
argument fails.

---

## Table of Contents

1. [Loss Mitigation Failure](#1-loss-mitigation-failure)
2. [RESPA NOE/RFI Non-Response](#2-respa-noerfi-non-response)
3. [Forbearance Breach](#3-forbearance-breach)
4. [Unauthorized Foreclosure](#4-unauthorized-foreclosure)
5. [False Credit Reporting](#5-false-credit-reporting)
6. [Dual Tracking](#6-dual-tracking)
7. [State Consumer Protection](#7-state-consumer-protection)
8. [Defective Foreclosure Notice](#8-defective-foreclosure-notice)
9. [Escrow Overcharge](#9-escrow-overcharge)

Cross-cutting topics:
- [VSO/Third-Party Interference](#vso-third-party-interference)
- [How to Use This Checklist](#how-to-use-this-checklist)

---

## How to Use This Checklist

For each violation category:

1. Read **"What the law requires"** to understand the standard
2. Walk through **"Elements to prove"** — check each one against your documents
3. Use **"Evidence checklist"** to identify what you have and what you still need
4. Read **"Servicer will argue"** before you write anything — anticipate the defense
5. Use **"Why that fails"** to build your rebuttal

**Mark everything:**
- ✅ Confirmed with evidence
- ⚠️ Likely but needs verification
- ❌ Not applicable or not present
- 📋 Evidence still needed

**Citation rule:** Mark all unverified legal citations with `[VERIFY]`.
Never invent case names or statutory provisions.

---

## 1. Loss Mitigation Failure

### What the law requires

**38 CFR 36.4319:** Servicers must evaluate all available loss mitigation
options before referring a VA loan to foreclosure.

**M26-4 Chapter 5:** Establishes a specific loss mitigation "waterfall" —
a sequence of options the servicer must evaluate in order:
- Repayment plan
- Special forbearance
- Loan modification (rate cap: existing rate + 1%)
- Compromise sale / short sale
- Deed in lieu of foreclosure
- Partial claim (under H.R. 1815, when implemented)

**Rate cap rule:** Any modification offered must not exceed the borrower's
existing note rate + 1%. This cap is set by M26-4 Chapter 5. `[VERIFY
current M26-4 language — chapter may be in draft/revision]`

### Elements to prove

- [ ] Servicer did not exhaust all waterfall options before foreclosure referral
- [ ] Modification offered at a rate exceeding existing + 1% (rate cap violation)
- [ ] VASP/partial claim was available but not evaluated
- [ ] Borrower was eligible for one or more options the servicer skipped
- [ ] Servicer did not submit the loan file to VALERI for VA review

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Original note/deed of trust | Original interest rate (the baseline for rate cap) | |
| Modification offer letter | Rate offered vs. rate cap (existing + 1%) | |
| VALERI records (via FOIA) | Whether servicer submitted loan for VA review | |
| Loss mitigation correspondence | Which options were offered/evaluated | |
| VA technician emails | VA's awareness of the case and servicer's actions | |
| VASP enrollment confirmation | Whether borrower was enrolled before VASP sunset | |
| Payment history | Whether borrower was current/delinquent and for how long | |

### Rate cap violation calculation

```
Original note rate:          ____%
M26-4 cap (existing + 1%):  ____%
Rate offered in modification: ____%
Violation amount:            ____ basis points over cap
PMMS rate week of mod offer: ____% (for context, not the cap)
```

The cap is **existing rate + 1%**, NOT the current market rate. A common
error is confusing the Freddie Mac PMMS rate with the M26-4 cap. The PMMS
rate provides context but does not set the cap.

### Servicer will argue

> "We offered a modification and the borrower declined it."

> "The borrower failed to return the modification agreement by the
> deadline."

> "We evaluated the borrower for all available options."

### Why that fails

- **If the offered rate exceeds the cap:** The modification was non-compliant
  on its face. A borrower cannot "decline" a modification they were never
  legally entitled to receive at those terms. The servicer violated M26-4
  by offering a rate above the cap.

- **If VALERI has no submission:** The servicer cannot claim they evaluated
  the borrower through VA channels if they never submitted the file. VA
  technician statements confirming non-submission are direct evidence.
  Request VALERI records via FOIA.

- **If the waterfall was skipped:** Check whether the servicer evaluated
  repayment plan, special forbearance, and compromise sale before jumping
  to modification or foreclosure. The waterfall is sequential — skipping
  steps is a violation.

- **"Deadline" defense:** Check whether the deadline was reasonable, whether
  the modification terms were themselves compliant, and whether the
  borrower communicated inability to accept the terms as offered.

---

## 2. RESPA NOE/RFI Non-Response

### What the law requires

**12 CFR §1024.35 (Notice of Error):** When a borrower sends a written
notice identifying a servicing error, the servicer must:
- **Acknowledge** within 5 business days
- **Investigate and respond** within 30 business days (extendable to 45)
- Either **correct the error** or explain why the servicer believes no error
  occurred

**12 CFR §1024.36 (Request for Information):** Same timeline structure.
Servicer must provide the requested information or explain why it cannot.

### Elements to prove

- [ ] Borrower sent a written NOE or RFI (with date and delivery confirmation)
- [ ] The request meets QWR requirements (borrower name/account + specific error or information request)
- [ ] Servicer failed to acknowledge within 5 business days
- [ ] Servicer failed to respond substantively within 30 business days
- [ ] Servicer's response (if any) did not address the specific errors raised
- [ ] Errors identified in the NOE remain uncorrected

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Copy of NOE/RFI sent | Content, date, delivery method | |
| Certified mail receipt or email confirmation | Proof of delivery | |
| Servicer's acknowledgment (if received) | Timeliness of response | |
| Servicer's substantive response (if received) | Whether errors were addressed | |
| Current account records | Whether identified errors were corrected | |

### Servicer will argue

> "We never received the letter."

> "The letter didn't qualify as a valid QWR."

> "We responded to the borrower's concerns."

### Why that fails

- **"Never received":** Certified mail receipt or email delivery confirmation
  defeats this. If sent to the address designated for qualified written
  requests (check servicer's website or loan documents), delivery is
  presumed.

- **"Not a valid QWR":** A QWR must include the borrower's name/account and
  a statement of the error or information requested. It does NOT need to
  use the phrase "qualified written request." If the letter identifies
  specific errors, it qualifies.

- **"We responded":** Compare the response to the specific errors raised.
  A generic form letter does not satisfy the requirement. Did the servicer
  address each identified error? Did they correct anything?

---

## 3. Forbearance Breach

### What the law requires

**CARES Act §4022:** For federally backed mortgage loans (including VA):
- Borrowers experiencing COVID-related hardship can request forbearance
  for up to 180 days, renewable for another 180 days
- Servicer cannot require documentation beyond the borrower's attestation
  of hardship
- Post-forbearance, the servicer must evaluate the borrower for loss
  mitigation options

**VA-specific forbearance:** VA forbearance programs (including VASP-era
forbearance) have specific terms. When programs sunset, servicers must
provide individual notice and transition borrowers to available alternatives.

### Elements to prove

- [ ] Borrower entered forbearance (date and terms)
- [ ] Forbearance program ended or was modified
- [ ] Servicer did not provide individual notice of program end
- [ ] Post-forbearance loss mitigation evaluation did not occur
- [ ] Servicer imposed requirements not authorized by the forbearance agreement
- [ ] Servicer treated forbearance exit as an immediate default trigger

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Forbearance agreement | Original terms, dates, conditions | |
| Servicer notices about program changes | Whether individual notice was given | |
| Post-forbearance correspondence | Whether loss mitigation was offered | |
| Payment history after forbearance | Whether payments were applied correctly | |
| VA circulars about program transitions | What servicers were required to do | |

### Servicer will argue

> "The program ended per its terms."

> "The borrower was notified through our general communications."

> "The borrower failed to engage with post-forbearance options."

### Why that fails

- **"Ended per its terms":** Check whether the original agreement specified
  an end date or was tied to a program that was later rescinded by VA.
  If the latter, the servicer had an obligation to transition the borrower.

- **"General communications":** Mass communications (website notices, form
  letters to all borrowers) do not satisfy individual notification
  requirements. Was the borrower specifically told their forbearance was
  ending and what options were available?

- **"Failed to engage":** Check the timeline. Was the borrower given a
  reasonable window to respond? Did the servicer actually offer options,
  or did they skip directly to foreclosure?

---

## 4. Unauthorized Foreclosure

### What the law requires

**38 CFR 36.4319:** Servicers must notify VA and receive authorization
before proceeding with foreclosure on a VA-guaranteed loan. This
notification is done through **VALERI** (VA's electronic loan management
system).

**The VALERI requirement:** The servicer must submit the loan file to VALERI,
documenting that all loss mitigation options have been exhausted. VA reviews
the submission and either authorizes or denies the foreclosure referral.

### Elements to prove

- [ ] Servicer referred loan to foreclosure (date)
- [ ] VALERI records show no submission by the servicer (the strongest evidence)
- [ ] VA technicians confirm non-submission in writing or by phone
- [ ] No VA authorization for foreclosure exists in the record
- [ ] Servicer proceeded to trustee sale without VA approval

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| VALERI records (via FOIA to VA) | Whether servicer submitted, what VA saw | |
| VA technician emails/call notes | VA's awareness and statements about submission status | |
| Foreclosure referral letter from servicer | Date of referral | |
| Trustee sale notice | Date of sale, whether VA was listed as party | |
| VA correspondence to servicer | Whether VA authorized or objected | |

### Servicer will argue

> "We followed standard procedure."

> "VA was informed of the foreclosure."

> "We submitted through our normal channels."

### Why that fails

- **VALERI audit is the kill shot.** If VALERI has no submission record,
  the servicer did not follow the required process — regardless of what
  they claim about "standard procedure" or "normal channels." The system
  is the system. No submission = no authorization.

- **"VA was informed":** Informing VA is not the same as receiving
  authorization. The regulation requires the servicer to submit through
  VALERI and receive approval. Sending a letter or making a phone call
  does not satisfy the electronic submission requirement.

- **VA technician statements** confirming that the servicer never submitted
  are powerful corroborating evidence. Document these carefully — dates,
  names, exact words used.

---

## 5. False Credit Reporting

### What the law requires

**FCRA §623 (15 U.S.C. §1681s-2):** Furnishers (including mortgage
servicers) must report accurate information to credit bureaus. Reporting
information the furnisher knows or should know is inaccurate violates
the FCRA.

**CARES Act credit reporting protections:** If a borrower is in a COVID-
related accommodation (forbearance, modification, deferral), the servicer
must report the account as "current" unless the account was already
delinquent before the accommodation. Backdating delinquencies into a
CARES-protected period is a per se violation.

### Elements to prove

- [ ] Credit report shows delinquencies during a CARES-protected forbearance period
- [ ] Delinquency reporting was backdated into a period when the loan was in forbearance
- [ ] Duplicate or phantom tradelines reporting on the same loan
- [ ] Servicer continued reporting delinquencies after the borrower disputed the accuracy
- [ ] Reported balance, payment history, or account status is factually inaccurate

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Credit reports (all 3 bureaus) | What's being reported, dates, status codes | |
| Forbearance agreement | Dates of protected period | |
| CARES Act attestation | When borrower entered forbearance | |
| Payment history from servicer | Actual payment dates vs. reported dates | |
| Prior credit dispute letters | Whether servicer was notified of inaccuracies | |
| Servicer's dispute responses | Whether corrections were made | |

### Servicer will argue

> "Reports reflected the actual loan status after forbearance ended."

> "The borrower was delinquent before entering forbearance."

> "We updated reporting after receiving the dispute."

### Why that fails

- **Backdating is the key issue.** If the credit report shows delinquencies
  during months when the loan was in active CARES forbearance, that's a
  violation regardless of what happened before or after.

- **"Delinquent before forbearance":** Check whether the borrower was
  current at forbearance entry. If so, the entire forbearance period must
  be reported as current. Even if the borrower was delinquent before, the
  servicer cannot report NEW delinquencies during the forbearance period.

- **"Updated after dispute":** Under FCRA, the servicer has 30 days to
  investigate a dispute. If they failed to investigate, or if the
  correction was incomplete, the violation continues.

---

## 6. Dual Tracking

### What the law requires

**12 CFR §1024.41(g) (RESPA Regulation X):** Once a borrower submits a
**complete** loss mitigation application, the servicer cannot:
- Move for foreclosure judgment or order of sale
- Conduct a foreclosure sale
- Advance any foreclosure proceeding

This prohibition applies for the duration of the review period.

### Elements to prove

- [ ] Borrower submitted a complete loss mitigation application (date)
- [ ] Servicer acknowledged the application as complete
- [ ] Servicer advanced foreclosure while the application was pending
- [ ] Application was never formally denied in writing before foreclosure referral
- [ ] Modification options were marked "Not Reviewed" while foreclosure proceeded

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Loss mitigation application | Date submitted | |
| Servicer letter confirming "complete" status | Date and language | |
| Foreclosure referral letter | Date — compare to application status | |
| Decision letter (if any) | Whether all options were actually reviewed | |
| "Not Reviewed" markings | Smoking gun — can't claim review and mark "Not Reviewed" | |
| Timeline overlap | Application pending + foreclosure advancing simultaneously | |

### The "smoking gun" pattern

The strongest dual-tracking evidence follows this sequence:
1. Servicer sends letter promising evaluation (e.g., VASP enrollment)
2. Days or weeks later, servicer sends decision marking options "Not Reviewed"
3. Foreclosure referral follows shortly after

This sequence proves the servicer was advancing foreclosure while
maintaining the appearance of loss mitigation review.

### Servicer will argue

> "No complete application was pending at the time of foreclosure referral."

> "The application was reviewed and denied before foreclosure."

> "The borrower didn't meet the requirements for a complete application."

### Why that fails

- **Check the servicer's own letters.** If they sent a letter acknowledging
  the application as "complete" or "under review," they cannot later
  claim no complete application was pending.

- **"Not Reviewed" defeats "reviewed and denied."** If the decision letter
  marks options as "Not Reviewed," the servicer is admitting they did not
  review. You can't simultaneously claim you reviewed and mark "Not
  Reviewed." These are contradictory positions.

- **Timeline is the evidence.** Map the exact dates: application submitted
  → acknowledged as complete → foreclosure referral → decision letter.
  If the foreclosure referral predates or overlaps with the pending
  application, dual tracking occurred.

---

## 7. State Consumer Protection

### What the law requires

**State consumer protection acts** (e.g., WA CPA, RCW 19.86) prohibit
unfair or deceptive acts or practices in trade or commerce. Mortgage
servicing is commerce.

Elements vary by state, but typically:
- An unfair or deceptive act or practice
- In trade or commerce
- Affecting the public interest
- Causing injury to the plaintiff

Some states allow **treble damages** and **attorney fee recovery**.

### Elements to prove

- [ ] Specific unfair or deceptive act(s) by the servicer
- [ ] Act occurred in trade or commerce (mortgage servicing qualifies)
- [ ] Public interest impact (pattern of similar conduct, not isolated incident)
- [ ] Injury (financial harm, credit damage, housing instability)
- [ ] Pattern evidence from servicer's enforcement history

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Servicer's CFPB enforcement history | Prior violations, consent orders, penalties | |
| State AG actions against the servicer | State-specific pattern evidence | |
| CFPB complaint database results | Similar complaints from other borrowers | |
| Servicer's HMDA data | Lending/servicing patterns by demographic | |
| BBB complaint history | Consumer complaints and responses | |
| Federal court filings (PACER) | Class actions, pattern litigation | |

### Servicer will argue

> "This was an isolated error, not a pattern."

> "We corrected the issue when it was brought to our attention."

### Why that fails

- **Enforcement history defeats "isolated."** If the CFPB, state AGs, or
  courts have documented the same conduct across multiple cases, the
  servicer cannot credibly claim this instance was isolated. Prior consent
  orders are especially powerful — they prove the servicer was already on
  notice about the conduct.

- **"Corrected when notified":** Check whether the correction actually
  happened. In many cases, servicers acknowledge errors without correcting
  them. Also check whether the NOE/RFI response was timely and complete
  (see Violation 2).

### State-specific notes

**Washington (RCW 19.86):**
- Treble damages up to $25,000 `[VERIFY current cap]`
- Attorney fee recovery available
- Private right of action — does not require AG filing
- WA CPA applies to mortgage servicing conduct

**Adapt for other states:** Replace RCW 19.86 with the applicable state CPA.
Common examples: TX DTPA, CA UCL/CLRA, FL FDUTPA. Check whether the state
CPA requires a demand letter before filing (TX DTPA requires 60-day notice).

---

## 8. Defective Foreclosure Notice

### What the law requires

State foreclosure statutes set specific procedural requirements for non-
judicial foreclosures. Any defect in notice, recording, or service can
be grounds to challenge the validity of the sale.

**Washington (RCW 61.24):**
- **RCW 61.24.030:** Notice of Default requirements — content, timing, service
- **RCW 61.24.040:** Notice of Trustee Sale requirements — recording,
  publication, posting, mailing
- **RCW 61.24.050(1):** Sale finality — but limited if procedure was defective

### Elements to prove

- [ ] Notice of Default recorded with county auditor (date)
- [ ] Notice of Trustee Sale recorded, published, posted, and mailed per statute
- [ ] All required content included in notices
- [ ] Service requirements met (certified mail, personal service, posting)
- [ ] Required waiting periods observed between notices and sale
- [ ] Proper parties named and notified

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| County auditor recording records | Whether and when notices were recorded | |
| Notice of Default | Content, date, service method | |
| Notice of Trustee Sale | Content, date, service method, publication | |
| Proof of service/mailing | Certified mail receipts, affidavits | |
| Trustee deed | Sale date, parties, recording | |
| Newspaper publication | Whether publication requirement met | |

### Servicer will argue

> "All procedural requirements were met."

### Why that fails

- **Verify independently.** Check county auditor records for recording dates.
  Check whether the statutory waiting periods were observed. Check whether
  all required parties were notified.

- **Any procedural defect** — even a technical one — can be grounds to
  challenge the sale's validity. Courts scrutinize non-judicial foreclosure
  procedures because the borrower has no day in court before losing the
  property.

### State-specific notes

**Washington:** Non-judicial foreclosure state. Key RCW 61.24 requirements
include 120-day waiting period between default and notice of sale, 90-day
minimum between notice of sale and sale date, and specific recording and
mailing requirements.

**Adapt for other states:** Replace RCW 61.24 with applicable state statute.
Judicial foreclosure states have different requirements (court filing,
service of process, judgment). Check whether the state has a right of
redemption after sale.

---

## 9. Escrow Overcharge

### What the law requires

**12 CFR §1024.17 (RESPA):** Servicers must:
- **(c)** Conduct an **annual escrow analysis** using the actual projected
  tax and insurance obligations for the property
- **(f)** Refund any escrow **surplus over $50** within 30 days
- Use the **actual tax amount** that will be assessed — not estimates,
  not prior-year amounts when a change is known

**12 CFR §1024.35:** Servicer must investigate and correct escrow errors
upon receiving a formal Notice of Error.

### Elements to prove

- [ ] Servicer used incorrect tax amount in escrow calculations
- [ ] Property tax exemption (e.g., disabled veteran) was approved but not reflected
- [ ] Exemption was a public county record accessible to the servicer
- [ ] Escrow surplus exceeded $50 and was not refunded
- [ ] Overcharge inflated the monthly payment
- [ ] Overcharge inflated the cumulative delinquency/reinstatement figure
- [ ] Third-party cure attempts were defeated by the inflated figure

### Evidence checklist

| Document | What it shows | Status |
|----------|-------------|--------|
| Escrow disclosure statement(s) | Tax amount used in calculations | |
| County property tax records | Actual tax assessed (exempt vs. non-exempt) | |
| Tax exemption approval | Date exemption was granted | |
| Servicer's annual escrow analysis | Whether it reflects the correct tax | |
| Reinstatement figures provided to VSOs | Whether the figure was inflated | |
| VSO correspondence | Whether payment attempts fell short of inflated target | |
| NOE sent to servicer about escrow error | Whether servicer was notified | |
| Servicer's response to NOE | Whether escrow was corrected | |

### Overcharge calculation

```
Non-exempt annual property tax:       $________
Actual exempt annual property tax:    $________
Annual overcharge:                    $________
Monthly overcharge:                   $________ (annual ÷ 12)
Months affected:                      ________
Total overcharge:                     $________
```

### The VSO interference multiplier

This violation has a unique downstream harm: **inflated escrow inflates
the reinstatement figure.** When third-party organizations (VSOs, nonprofits,
family members) attempt to cure the delinquency, they're paying against a
false target.

Document this chain:
1. Servicer applies wrong tax rate to escrow → monthly payment too high
2. Borrower falls behind on the inflated payment
3. Cumulative delinquency includes the inflated amount
4. VSO attempts to cure → their payment falls short of the inflated figure
5. Foreclosure proceeds despite external rescue attempt

This is a **harm multiplier** — the escrow error didn't just cost the borrower
money, it defeated the rescue. This is powerful in every advocacy context:
congressional (heartbreaking), media (infuriating), legal (consequential
damages), agency (pattern evidence if other borrowers experienced similar).

### Servicer will argue

> "We used the best available tax information."

> "The borrower didn't notify us of the exemption."

> "The escrow was adjusted when we became aware."

### Why that fails

- **Public record:** Property tax exemptions are recorded with the county.
  RESPA requires the servicer to use the actual tax amount — not borrower-
  reported data, not prior-year estimates. The servicer is responsible for
  checking county records as part of the annual escrow analysis.

- **"Didn't notify us":** The notification obligation runs to the servicer,
  not the borrower. 12 CFR §1024.17(c) requires the servicer to conduct
  the analysis using projected obligations. The exemption was public
  information.

- **"Adjusted when aware":** Check whether the adjustment actually happened.
  Check whether the surplus was refunded within 30 days per §1024.17(f).
  Check whether the reinstatement figure was corrected. In many cases,
  servicers acknowledge the error but don't fix the downstream effects.

---

## VSO/Third-Party Interference

This is not a standalone violation category but a **harm multiplier** that
strengthens damages claims and advocacy narratives across multiple
violation types.

### What to look for

- Third-party organization (VSO, nonprofit, family member) attempted to
  cure the delinquency
- The cure payment was calculated against a figure provided by the servicer
- That figure was inflated due to one or more servicer errors (escrow
  overcharge, improper fees, miscalculated interest)
- The cure payment fell short of the inflated target
- Foreclosure proceeded despite the external rescue attempt

### Why it matters

This pattern demonstrates that the servicer's errors had consequences
beyond the borrower — they defeated an organized rescue effort by a
credible third party. This transforms the narrative from "borrower
couldn't pay" to "the system failed despite multiple people trying to
make it work."

### Document the chain

| Step | What happened | Evidence |
|------|-------------|----------|
| Error | Servicer made a specific error (identify which violation) | |
| Inflation | Error inflated the payment/reinstatement amount | |
| Rescue attempt | Third party tried to cure (who, when, how much) | |
| Shortfall | Payment fell short of inflated figure (by how much) | |
| Outcome | Foreclosure proceeded despite rescue attempt | |

### Advocacy power

| Audience | Why this pattern is powerful |
|----------|---------------------------|
| Congressional | "Even nonprofits dedicated to helping veterans couldn't save this family — because the servicer's own error made the target unreachable" |
| Media | Human interest + systemic failure in one story |
| Legal | Consequential damages — the servicer's error caused a specific, quantifiable harm |
| Agency (CFPB/OIG) | Pattern evidence — are other borrowers experiencing the same inflation? |

---

## General Notes

### Anti-hallucination reminders

- Never invent statutory citations or case names
- Mark unverified citations with `[VERIFY]`
- When citing M26-4 Chapter 5, note the chapter may be in draft/revision
- When citing VA circulars, note they may have been superseded
- When citing state-specific statutes, verify applicability to the
  borrower's state

### Cross-referencing violations

Many cases involve multiple overlapping violations. Common clusters:

- **Loss mitigation failure + dual tracking + unauthorized foreclosure:**
  Servicer skipped the waterfall, advanced foreclosure while application
  was pending, and never submitted to VALERI. Three violations from one
  pattern of conduct.

- **Escrow overcharge + forbearance breach + VSO interference:**
  Wrong tax rate inflated escrow, borrower fell behind on inflated
  payment, entered forbearance, forbearance ended without proper
  transition, and the inflated reinstatement figure defeated rescue
  attempts.

- **False credit reporting + RESPA non-response:**
  Inaccurate credit reporting during forbearance, borrower sent NOE
  identifying the error, servicer never responded, reporting continues.

Document these clusters — they show a pattern of conduct, not isolated
incidents. Patterns are what elevate a complaint from "individual case"
to "enforcement priority."

### Adapting for other states

This checklist uses Washington state (RCW) as the default for state-
specific provisions. To adapt:

1. Replace RCW 61.24 with your state's foreclosure statute
2. Replace RCW 19.86 with your state's consumer protection act
3. Replace RCW 84.36.381 with your state's disabled veteran property
   tax exemption statute
4. Check whether your state is judicial or non-judicial foreclosure
5. Check whether your state has a right of redemption
6. Check whether your state CPA requires a pre-suit demand letter
