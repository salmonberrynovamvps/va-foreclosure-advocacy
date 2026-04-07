# Post-Foreclosure Options & Status Assessment

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Step 7.

For cases where foreclosure has already occurred. Covers title status,
occupancy rights, Cash for Keys analysis, VA authority, and the
sign-vs-don't-sign decision tree.

---

## Table of Contents

1. [Title Status Assessment](#1-title-status-assessment)
2. [Occupancy Rights](#2-occupancy-rights)
3. [Cash for Keys Analysis](#3-cash-for-keys-analysis)
4. [VA Authority Under §3732](#4-va-authority-under-3732)
5. [Challenging the Foreclosure Sale](#5-challenging-the-foreclosure-sale)
6. [Decision Tree: Sign vs. Don't Sign](#6-decision-tree)

---

## 1. Title Status Assessment

**First question:** Who holds title right now?

| Title holder | What it means | Next steps |
|-------------|-------------|------------|
| **VA Secretary** | VA acquired the property through guaranty claim. VA is now the owner and controls disposition. | VA has authority under §3732 to sell, lease, or convey. Negotiate with VA/VRM. |
| **Servicer** | Servicer took title at foreclosure sale. Has not yet conveyed to VA. | Servicer is the immediate counterparty. May be in transition to VA. |
| **Third-party purchaser** | Someone else bought at the trustee sale. | Different legal posture — PTFA (Protecting Tenants at Foreclosure Act) may apply. Occupancy rights depend on purchaser's intent. |
| **Unclear** | Title chain is not yet resolved. | Check county recorder/auditor for the trustee deed. Identify the grantee. |

**How to check:** Search county auditor/recorder website for the property
address. Look for the most recent trustee deed recording.

---

## 2. Occupancy Rights

### Washington State (non-judicial foreclosure)

**RCW 61.24.060:** After a non-judicial foreclosure sale, the former
owner's occupancy rights depend on the new owner's actions.

- The purchaser must provide **written notice** to vacate
- Former owner is typically entitled to **20 days** after notice
  `[VERIFY current WA timeline — may vary]`
- If the former owner does not vacate, the purchaser must file an
  **unlawful detainer action** (eviction) — they cannot self-help evict

### Protecting Tenants at Foreclosure Act (PTFA)

If the property was rental (tenants, not owner-occupants):
- Tenants with a lease can stay until lease end
- Month-to-month tenants get 90 days notice
- New owner who intends to occupy can terminate with 90 days notice

**For owner-occupants:** PTFA generally does not apply (it protects
tenants, not former owners). The former owner's rights come from state
law.

### Key principle

**Eviction requires a court process.** The new owner cannot change locks,
shut off utilities, or remove belongings without a court order. Any
attempt to do so is an illegal self-help eviction.

---

## 3. Cash for Keys Analysis

**What it is:** An agreement where the new owner (usually VA via VRM)
pays the former owner a sum of money in exchange for vacating the
property voluntarily and in good condition.

### What signing typically does

- ✅ Provides relocation money (amount varies — typically $1,000-$5,000)
- ✅ Avoids formal eviction on your record
- ✅ Provides a specific move-out date (negotiable)
- ❌ **Releases all legal claims against the servicer and VA**
- ❌ **Waives right to challenge the foreclosure**
- ❌ **Waives right to sue for damages**
- ❌ **Waives right to assert any regulatory violations**

### What NOT signing preserves

- ✅ All legal claims remain intact
- ✅ Right to challenge the foreclosure sale
- ✅ Right to sue for RESPA, FCRA, CPA violations
- ✅ Right to negotiate from a position of leverage
- ✅ Ability to use the case for congressional/media advocacy
- ❌ Eviction proceedings will likely begin after deadline
- ❌ No relocation payment
- ❌ Eviction may appear on record (but can potentially be contested)

### Critical analysis questions

Before advising on Cash for Keys:

1. **Read the actual agreement.** What specifically does it release?
   Some agreements release only the current owner (VA/VRM). Others
   release the servicer too. The scope of the release is everything.

2. **What is the total value of preserved claims?** If RESPA, CPA,
   and FCRA claims are worth $50,000+ (see damages framework), a
   $3,000 Cash for Keys payment is trading dollars for pennies.

3. **Is the deadline real?** Cash for Keys deadlines are often
   negotiable. The new owner wants a clean property — they have
   incentive to extend if you're cooperating but need more time.

4. **Can you get a better deal?** If you have documented violations,
   the leverage goes both ways. VA doesn't want a foreclosure with
   documented regulatory violations on the public record.

---

## 4. VA Authority Under §3732

**38 U.S.C. §3732** gives VA broad authority over properties it acquires
through the guaranty program.

### What VA can do

| Action | Authority | Practical meaning |
|--------|----------|------------------|
| **Sell** the property | §3732(a) | VA can sell at market or below market |
| **Lease** the property | §3732(a) | VA can lease back to the former owner |
| **Convey** the property | §3732(a) | VA can transfer title |
| **Manage and maintain** | §3732(c) | VA is responsible while it holds title |
| **Set terms** | §3732(a) | VA has discretion on price, terms, conditions |

### The lease-back possibility

VA has the authority to lease the property back to the veteran. This
is rarely used but is legally authorized. Arguments for it:

- **Cost efficiency:** VA avoids REO disposition costs (~$72K)
- **Veteran stability:** Family stays housed, reducing downstream VA
  healthcare and homeless services costs
- **Clean resolution:** Avoids contested eviction and potential litigation

### Who to negotiate with

| Entity | Role | Contact channel |
|--------|------|----------------|
| **VRM (Veterans Real Estate Management)** | VA's property management contractor | Direct contact (Cash for Keys offer comes from them) |
| **VA Loan Guaranty Service** | VA internal — oversees the program | Congressional inquiry, VA OIG |
| **VA Regional Loan Center** | Regional VA office | Direct contact or congressional referral |

---

## 5. Challenging the Foreclosure Sale

### Grounds to challenge

| Ground | What to show | Likelihood of success |
|--------|-------------|----------------------|
| **Procedural defect** | Notice, recording, service, or timing requirements under state DTA were not met | Moderate — if defect is documented |
| **Unauthorized foreclosure** | Servicer did not obtain VA authorization via VALERI | Strong — if VALERI records confirm non-submission |
| **Dual tracking** | Foreclosure advanced while complete application was pending | Strong — if timeline documents overlap |
| **§3720(h) argument** | Mandatory mitigation sequence not completed because it doesn't exist yet | Novel — untested, high potential but no precedent |
| **Fraud** | Servicer made material misrepresentations | Requires clear evidence of intent |

### Practical considerations

- **Attorney required.** Challenging a completed foreclosure sale is
  litigation. This is not a pro se task.
- **Timing matters.** Challenges to sale validity must be brought
  promptly. Delay weakens the claim.
- **Lis pendens.** If litigation is filed, a lis pendens (notice of
  pending action) can be recorded against the property, clouding title
  and preventing resale.
- **Bond requirement.** Some jurisdictions require a bond to challenge
  a completed sale. `[VERIFY WA requirements]`

---

## 6. Decision Tree

### Sign Cash for Keys?

```
START: Do you have documented regulatory violations?
│
├── NO → Cash for Keys may be reasonable.
│         Negotiate the best amount and timeline.
│         Get everything in writing before signing.
│
└── YES → What are the violations worth?
          │
          ├── Claims total < Cash for Keys offer
          │   → Signing may be reasonable.
          │     But consult an attorney first —
          │     claims may be worth more than you think.
          │
          └── Claims total > Cash for Keys offer
              │
              ├── Do you have or can you get an attorney?
              │   │
              │   ├── YES → Do NOT sign until attorney reviews.
              │   │         The release likely waives claims
              │   │         worth more than the payment.
              │   │
              │   └── NO → This is the hardest situation.
              │             Options:
              │             1. Contact legal aid (Veterans
              │                Consortium, NVLSP, state legal aid)
              │             2. File complaints BEFORE signing
              │                (CFPB, OIG, state AG — filing
              │                preserves the record even if you
              │                later sign)
              │             3. Negotiate: ask for more money,
              │                more time, or a narrower release
              │             4. Congressional office may be able
              │                to pause the deadline while you
              │                seek counsel
              │
              └── Is the deadline imminent?
                  │
                  ├── YES → Priority: ask for an extension.
                  │         VRM/VA often extends if you're
                  │         communicating and cooperating.
                  │         File urgent complaints NOW.
                  │         Contact congressional office NOW.
                  │
                  └── NO → You have time. Use it to:
                           1. Complete the full violation analysis
                           2. File complaints
                           3. Secure legal representation
                           4. Build the advocacy case
                           5. THEN decide on Cash for Keys
```

### Key principles

- **Never sign under time pressure without understanding what you're
  releasing.** Ask for an extension. They almost always grant one.
- **Filing complaints preserves the record** even if you later sign
  Cash for Keys. The CFPB and OIG complaint exists independently.
- **The release scope is everything.** Some releases are narrow
  (just VA/VRM). Some are broad (servicer, VA, and all related
  parties). Read every word.
- **Signing is irreversible.** Once you sign, your legal claims are
  gone. There is no undo.
