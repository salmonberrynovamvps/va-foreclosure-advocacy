# Statute of Limitations Tracker

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Step 6.

Track every identified violation against its SOL. Flag anything
approaching expiration as **URGENT**.

**Rule:** SOL urgency overrides all other sequencing considerations.
Never hold a time-sensitive filing for better political optics.

---

## SOL by Claim Type

| Claim | SOL Period | Clock starts when | Federal/State | Notes |
|-------|-----------|-------------------|--------------|-------|
| **RESPA §2605 — damages** | **1 year** | Date of violation | Federal | Shortest SOL — check first |
| **RESPA §2605 — pattern/practice** | **3 years** | Date of violation | Federal | Requires showing pattern, not just one incident |
| **FCRA — negligent violation** | **2 years** | Date borrower discovers (or should have discovered) the error | Federal | Discovery rule helps if error was hidden |
| **FCRA — willful violation** | **5 years** | Date of violation (not discovery) | Federal | Higher bar to prove willfulness |
| **CARES Act credit reporting** | **2 years** (via FCRA) | Discovery of false reporting during forbearance period | Federal | Treated as FCRA violation |
| **WA CPA (RCW 19.86)** | **4 years** | Date of violation | WA state | Private right of action |
| **WA DTA (RCW 61.24)** | **Varies** | Sale date (for challenging sale validity) | WA state | Procedural challenges must be timely |
| **38 CFR violations** | **No private SOL** | Administrative — no direct borrower lawsuit typically | Federal | Enforce through VA OIG, congressional inquiry, or CFPB referral |
| **Fair Housing Act** | **2 years** | Date of discriminatory act | Federal | If disparate impact claim is viable |
| **Common law fraud** | **3 years** (WA) | Discovery of fraud | WA state | `[VERIFY WA fraud SOL]` |
| **Breach of contract** | **6 years** (WA) | Date of breach | WA state | `[VERIFY — may vary by contract type]` |

---

## How to Use This Tracker

### Step 1: Fill in the dates

For each violation identified in Step 2, record:

```
Violation:           ________________________________
Date of violation:   ________________________________
Date discovered:     ________________________________
Applicable SOL:      ________________________________
Expiration date:     ________________________________
Days remaining:      ________________________________
Status:              🔴 URGENT / 🟡 APPROACHING / 🟢 OK
```

### Step 2: Sort by urgency

Arrange all claims from shortest remaining time to longest. Any claim
with less than 90 days remaining is **🔴 URGENT**.

### Step 3: Flag for calendar

Every SOL deadline should exist as a **Google Calendar event** with:
- 90-day warning reminder
- 30-day warning reminder
- 7-day warning reminder

This is the safety net. Calendar reminders push to the user's phone
even when they can't open Claude.

---

## Common Traps

### The RESPA 1-year trap

RESPA damages claims have a **1-year SOL from the date of violation** —
not from discovery. This is the shortest and most commonly missed.

If the NOE/RFI was sent more than 1 year ago and the servicer never
responded, the RESPA damages claim may be expiring. Check immediately.

**Workaround:** The 3-year SOL applies to pattern/practice claims. If
you can establish that the servicer's conduct is part of a pattern
(enforcement history audit, Step 9), the longer SOL may apply.

### Discovery rule vs. occurrence rule

- **Discovery rule** (FCRA, fraud): Clock starts when you discover or
  should have discovered the violation. Argue that hidden errors
  (unreported VALERI non-submission, undisclosed escrow miscalculation)
  were not discoverable until you obtained the records.

- **Occurrence rule** (RESPA damages): Clock starts when the violation
  occurs, regardless of when you discover it. This is harsher.

### Continuing violations

Some violations are **ongoing** — each month the escrow is miscalculated
is a new violation with its own SOL. Each month of false credit reporting
is a new violation. This can reset or extend the effective SOL window.

**Argument:** "The servicer's failure to correct the escrow error is not
a single violation from the date it began — it is a continuing violation
that recurs with each monthly escrow collection." `[VERIFY — courts vary
on continuing violation doctrine]`

---

## Tolling Possibilities

SOLs can sometimes be paused ("tolled") under certain circumstances.
These are case-specific and require attorney evaluation, but flag them
if present:

| Tolling basis | When it applies |
|--------------|----------------|
| **Equitable tolling** | Borrower was prevented from discovering the violation through no fault of their own (servicer concealment) |
| **Military tolling (SCRA)** | Active duty military service can toll certain SOLs |
| **Disability tolling** | Some states toll SOLs for individuals with disabilities `[VERIFY WA provisions]` |
| **Fraudulent concealment** | If the servicer actively concealed the violation, SOL may be tolled until discovery |
| **Bankruptcy stay** | Bankruptcy filing tolls many SOLs during the stay period |

---

## State-Specific SOL Notes

### Washington

| Claim type | SOL | Source |
|-----------|-----|--------|
| Written contract | 6 years | RCW 4.16.040 |
| Oral contract | 3 years | RCW 4.16.080 |
| Fraud | 3 years from discovery | RCW 4.16.080 |
| CPA (RCW 19.86) | 4 years | RCW 19.86.120 |
| Property damage | 3 years | RCW 4.16.080 |

### Adapting for other states

Replace WA SOLs with your state's limitations periods. Key statutes to
check:
- Contract claims (written and oral)
- Fraud
- State consumer protection act
- Property claims
- Tort claims

Federal SOLs (RESPA, FCRA, CARES Act, Fair Housing Act) are the same
in every state.

---

## Blank Tracking Template

Copy and fill for each case:

| # | Violation | Date occurred | Date discovered | SOL period | Expiration | Days left | Status |
|---|-----------|--------------|----------------|-----------|------------|-----------|--------|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |
| 4 | | | | | | | |
| 5 | | | | | | | |
| 6 | | | | | | | |
| 7 | | | | | | | |
| 8 | | | | | | | |
| 9 | | | | | | | |
