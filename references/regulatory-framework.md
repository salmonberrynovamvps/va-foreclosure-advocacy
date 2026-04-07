# Regulatory Framework Reference

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Step 1.

Key provisions from each applicable law. Organized by framework.
Use this to identify which regulations apply and cite specific provisions.

---

## Table of Contents

1. [Federal Statutes](#federal-statutes)
2. [VA Regulations & Policy](#va-regulations--policy)
3. [RESPA / Regulation X](#respa--regulation-x)
4. [FCRA](#fcra)
5. [Washington State](#washington-state)
6. [Adapting for Other States](#adapting-for-other-states)

---

## Federal Statutes

### CARES Act §4022 (2020)

**What it does:** COVID-era mortgage protections for federally backed loans
(including VA-guaranteed).

**Key provisions:**
- Borrowers experiencing COVID-related hardship can request forbearance
  for up to 180 days, renewable once (total 360 days)
- Servicer must grant forbearance upon borrower attestation — no
  documentation required
- During forbearance, servicer must report the loan as **current** to
  credit bureaus (if loan was current at forbearance entry)
- No fees, penalties, or additional interest beyond scheduled amounts
  during forbearance
- Post-forbearance, servicer must evaluate borrower for loss mitigation

**Source:** congress.gov/bill/116th-congress/house-bill/748

---

### H.R. 1815 — VA Home Loan Program Reform Act (signed July 30, 2025)

**What it does:** Establishes permanent partial claim authority for VA loans.
Replaces the expired VASP and COVID-era partial claim programs.

**Key provisions:**

- **Partial claim program:** VA can advance funds to cover missed payments
  as a subordinate lien (0% interest junior lien). Borrower becomes current
  without refinancing or altering original loan terms.
- **Eligibility:** Borrowers in serious delinquency on VA-guaranteed loans.
  Up to 30% of unpaid principal for COVID-era cases.
- **§3720(h) — mandatory mitigation sequence:** Prohibits the Secretary
  from taking foreclosure-related actions before the veteran completes a
  mandatory loss mitigation sequence. `[VERIFY: implementing regulations
  may still be pending]`
- **Buyer agent compensation:** Permanent authorization for VA borrowers
  to pay buyer agent compensation.

**Critical implementation gap:** H.R. 1815 authorized the partial claim
program, but VA must prescribe implementing regulations under §3732(d).
As of March 2026, those regulations are not yet operational. This creates
a catch-22: foreclosure is arguably barred by §3720(h) because the
mandatory sequence the veteran must complete does not yet exist.
`[VERIFY current implementation status]`

**Source:** govinfo.gov — search H.R. 1815, 119th Congress

---

### 38 U.S.C. §3720(h) — Novel Legal Argument

**The argument (not yet raised publicly by any advocacy organization):**

New §3720(h) creates a de facto foreclosure moratorium because it
prohibits the Secretary from taking foreclosure-related actions before
the veteran completes a mandatory loss mitigation sequence — but the
Secretary has not yet prescribed that sequence under §3732(d).

**Supporting doctrinal pillars:**
- *Kingdomware Technologies v. United States* — "shall" is mandatory
- *Cox v. SNAP* — agencies cannot bypass statutory prerequisites
- *Dan-Harry v. PNC* — servicer must complete loss mitigation before
  foreclosure
- *Griffin v. Oceanic* — statutory conditions precedent must be met
- *Louisiana Public Service Commission v. FCC* — agencies cannot act
  beyond delegated authority

**Legislative history:** Predecessor bill H.R. 8647 used "may prescribe";
H.R. 1815 strengthened to "shall prescribe" — deliberate congressional
choice reinforcing mandatory duty.

**Strategic note:** This argument is a strategic asset. It has not been
raised publicly. Timing and placement matter — consider whether to
deploy in litigation, congressional testimony, or public comment.

---

## VA Regulations & Policy

### 38 CFR 36.4319 — VA Loss Mitigation Procedures

**What it requires:**
- Servicers must evaluate all available loss mitigation options before
  referring a VA-guaranteed loan to foreclosure
- Servicers must notify VA before proceeding with foreclosure
- Notification is done through **VALERI** (VA Loan Electronic Reporting
  Interface)

**Key implication:** If the servicer never submitted to VALERI, no VA
authorization was obtained. Foreclosure without VA authorization
violates this regulation.

**Source:** ecfr.gov/current/title-38/chapter-I/part-36/subpart-F/section-36.4319

---

### M26-4 Chapter 5 — Loss Mitigation Waterfall

**What it requires:** A sequential evaluation of loss mitigation options
before foreclosure referral.

**The waterfall (in order):**
1. Repayment plan
2. Special forbearance
3. Loan modification
4. Compromise sale / short sale
5. Deed in lieu of foreclosure
6. Partial claim (when implemented under H.R. 1815)

**Rate cap rule:** Any modification must not exceed the borrower's
**existing note rate + 1%**.

- The cap is the existing rate + 1%, NOT the current market rate
- The Freddie Mac PMMS rate provides context but does not set the cap
- A modification offered above this cap is non-compliant on its face

**Status:** Chapter 5 may be in draft/revision as of 2026. Check VA's
drafting table for the current version. `[VERIFY]`

**Source:** benefits.va.gov/WARMS/docs/admin26/m26_04/m26-4-chapter5-loss-mitigation.pdf

---

### VALERI (VA Loan Electronic Reporting Interface)

**What it is:** VA's electronic system for tracking loan status, loss
mitigation activity, and foreclosure authorization.

**Why it matters:**
- Servicers are required to submit loan events to VALERI
- VALERI is programmed to flag certain violations (e.g., "suspicious loan
  modification" for rate cap violations)
- If a servicer never submits to VALERI, the entire VA oversight system
  is bypassed — no events = no auto-infractions, no rate cap check, no
  EPD (early payment default) review

**The central structural gap:** The VA oversight framework is VALERI-
dependent. If a servicer does not submit, nothing in the system activates.
There is no mandatory submission timeframe, no automatic consequence for
non-submission, and no escalation pathway.

---

### Key VA Circulars

| Circular | Subject | Status |
|----------|---------|--------|
| 26-25-02 | VASP wind-down procedures | Active — check for updates |
| 26-24-16 | Waterfall implementation | Active — check for updates |

**Note:** VA circulars can be superseded without notice. Always verify
current status at benefits.va.gov/homeloans/circulars.asp

---

## RESPA / Regulation X

### 12 CFR §1024.17 — Escrow Accounts

- **(c) Annual analysis:** Servicer must conduct annual escrow analysis
  using actual projected tax and insurance obligations
- **(f) Surplus refund:** If escrow surplus exceeds $50, servicer must
  refund within 30 days
- Servicer must use the **actual tax amount** assessed on the property —
  not estimates, not prior-year amounts when a change is known

---

### 12 CFR §1024.35 — Notice of Error

- Servicer must **acknowledge** within 5 business days of receipt
- Servicer must **investigate and respond** within 30 business days
  (extendable to 45 with written notice)
- Response must either correct the error or explain why the servicer
  believes no error occurred
- Servicer must not charge fees or report negative credit based on the
  disputed amount during the investigation period

**Source:** ecfr.gov/current/title-12/chapter-X/part-1024/subpart-C/section-1024.35

---

### 12 CFR §1024.36 — Request for Information

- Same timeline as NOE (5 days to acknowledge, 30 days to respond)
- Servicer must provide the requested information or explain why it
  cannot be provided

**Source:** ecfr.gov/current/title-12/chapter-X/part-1024/subpart-C/section-1024.36

---

### 12 CFR §1024.41 — Loss Mitigation Procedures

- **(b)** Servicer must evaluate borrower for all available loss mitigation
  options upon receipt of a complete application
- **(c)** Servicer must provide written decision within 30 days
- **(g) Dual tracking prohibition:** Once a borrower submits a complete
  application, servicer cannot move for foreclosure judgment, conduct
  foreclosure sale, or advance foreclosure proceedings

**Source:** ecfr.gov/current/title-12/chapter-X/part-1024/subpart-C/section-1024.41

---

## FCRA

### 15 U.S.C. §1681s-2 — Furnisher Responsibilities

- **(a) Duty of accuracy:** Furnishers must not report information they
  know or should know is inaccurate
- **(b) Duty to investigate disputes:** Upon receiving notice of a dispute
  from a credit bureau, furnisher must investigate within 30 days,
  review all relevant information, and correct or delete inaccurate data
- **CARES Act interaction:** During COVID-related accommodation, account
  must be reported as current if it was current at accommodation entry

### Key credit reporting codes for VA loans

| Code | Meaning | When it's a problem |
|------|---------|-------------------|
| Current | Account in good standing | Should show during CARES forbearance |
| 30/60/90+ late | Delinquency markers | Violation if reported during CARES forbearance |
| Foreclosure | Foreclosure reported | Check whether foreclosure was authorized |
| Duplicate tradeline | Same loan reported twice | Common servicer error — inflates negative impact |

---

## Washington State

### RCW 61.24 — Deed of Trust Act (Non-Judicial Foreclosure)

**Key provisions:**
- **61.24.030:** Notice of Default requirements (content, service, recording)
- **61.24.040:** Notice of Trustee Sale requirements (90+ days before sale,
  recording with county auditor, publication, posting, mailing)
- **61.24.050(1):** Sale finality — but limited if procedure was defective
- **61.24.060:** Post-sale occupancy provisions

**Washington is a non-judicial foreclosure state.** The borrower has no
automatic day in court before the property is sold. This makes procedural
compliance critical — any defect is a potential ground to challenge the
sale.

---

### RCW 19.86 — Consumer Protection Act

- Prohibits unfair or deceptive acts in trade or commerce
- Private right of action (borrower can sue directly)
- Treble damages up to $25,000 `[VERIFY current cap]`
- Attorney fee recovery available
- Must show: unfair/deceptive act + in commerce + public interest impact
  + injury

---

### RCW 84.36.381 — Disabled Veteran Property Tax Exemption

- Qualifying disabled veterans receive reduced property tax assessment
  on primary residence
- Exemption is recorded with county assessor — public record
- Servicer must reflect the exempt rate in escrow calculations
- Failure to apply the exemption inflates escrow, monthly payment, and
  reinstatement figures

---

## Adapting for Other States

| Component | Washington | Replace with |
|-----------|-----------|-------------|
| Foreclosure statute | RCW 61.24 | Your state's foreclosure statute |
| Consumer protection | RCW 19.86 | Your state's CPA (TX DTPA, CA UCL, FL FDUTPA, etc.) |
| Property tax exemption | RCW 84.36.381 | Your state's disabled veteran exemption |
| Foreclosure type | Non-judicial | Check: judicial vs. non-judicial |
| Redemption rights | Generally none (non-judicial) | Check: your state's redemption period |
| Pre-suit demand | Not required for WA CPA | Check: TX DTPA requires 60 days, MA Ch. 93A requires 30 days |

**Federal provisions (RESPA, FCRA, CARES Act, 38 CFR, H.R. 1815) apply
in all states.** Only state-specific provisions need adaptation.
