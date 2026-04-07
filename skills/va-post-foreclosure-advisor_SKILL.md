---
name: va-post-foreclosure-advisor
description: >
  Advises on post-foreclosure options for VA mortgage cases. Covers
  eviction defense, Cash for Keys analysis, occupancy rights, bankruptcy
  as emergency stay, court filing monitoring, and negotiation with VA/VRM.
  Use when someone says "I got an eviction notice," "should I sign Cash
  for Keys," "how long can I stay," "what are my rights after
  foreclosure," "VA owns my house now," or "how do I stop the eviction."
  Also trigger on uploaded eviction notices, UD filings, Cash for Keys
  offers, or post-sale notices. Works standalone or as a companion to
  va-foreclosure-case-analyzer. Built for pro se advocates, veterans,
  case managers, and social workers — not for corporate REO management.
metadata:
  author: Leann Ledford
  version: 1.0.0
  domain: veteran-housing-advocacy
  jurisdiction: US-federal, WA-state
  license: Apache-2.0
  companion-to: va-foreclosure-case-analyzer
---

# VA Post-Foreclosure Advisor

Guides veterans and advocates through post-foreclosure decisions:
eviction defense, Cash for Keys, occupancy rights, court monitoring,
and emergency options. Companion to `va-foreclosure-case-analyzer`.

**Who this is for:** Veterans and families who have already lost their
home to foreclosure and need to understand their options right now.

**What it produces:** Decision analysis, procedural checklists, timeline
calculations, document analysis, and emergency action plans.

**NOT LEGAL ADVICE.** An attorney should review before responding to
any court filing or signing any legal document.

---

## Quick-Start Mode

If the user says "I just got served" or signals immediate crisis:

1. **What did you receive?** — eviction notice, UD filing, Cash for Keys
   offer, or something else?
2. **When?** — date received, date on the document, any deadlines stated
3. **Immediate answer:** You cannot be removed without a court order.
   No one can change your locks, shut off your utilities, or remove
   your belongings without a judge signing off.
4. **Single next action:** Call legal aid / eviction defense hotline TODAY.

Do NOT run a full analysis in crisis mode. Give the emergency answer
and the single most important action.

---

## Post-Foreclosure Status Assessment

### Step 1: Who owns the property now?

| Title holder | How to verify | Implications |
|-------------|--------------|-------------|
| **Secretary of VA** | County recorder — trustee deed + subsequent deed | VA controls disposition. Negotiate with VRM. Congressional leverage applies. |
| **Servicer** | County recorder — trustee deed only, no subsequent transfer | Servicer is counterparty. May be in transition to VA. |
| **Third-party buyer** | County recorder — trustee deed to private party | PTFA may apply if you're a tenant. Different legal posture. |
| **Unknown** | County recorder search needed | Determine before any other analysis. |

### Step 2: What documents have been received?

| Document type | What it means | Urgency |
|--------------|-------------|---------|
| **VRM "Notice to Occupants"** | Informal — VRM identifying themselves as property manager. Not a legal notice to vacate. | Low — informational |
| **Cash for Keys offer** | Voluntary agreement: money for vacating + signing release. Has a deadline. | Medium — evaluate before deadline, DO NOT sign under pressure |
| **PTFA Notice** | Asks if you're a tenant/subtenant. Standard checklist before filing UD. Does not apply to former owners. | Low — save it, don't respond with lease docs you don't have |
| **RCW 61.24.060 Notice** (WA) | Formal post-sale notice citing the statute. States possession date. Pre-requisite to filing UD. | **High — this means UD filing is coming** |
| **Unlawful Detainer (UD) filing** | Court papers. The eviction lawsuit has been filed. | **CRITICAL — you have 20 days from SERVICE to respond** |
| **Writ of Restitution** | Court has ordered eviction. Sheriff will enforce. | **EMERGENCY — call attorney immediately** |

---

## Cash for Keys Decision Engine

### What signing does

**You get:**
- Relocation payment (typically $1,000-$5,000 — amount varies)
- Agreed move-out date (negotiable)
- Avoids formal eviction on record

**You lose:**
- All legal claims against the servicer (if release is broad)
- Right to challenge the foreclosure
- Right to sue for RESPA, FCRA, CPA violations
- Right to use the case for advocacy/media/congressional purposes
- Leverage in any ongoing investigation (OIG, CFPB)

### Decision framework

**Before advising, answer these questions:**

1. **Read the actual release language.** What specifically does it release?
   - Narrow release (VA/VRM only) = less harmful
   - Broad release (servicer + VA + "all related parties") = devastating

2. **What are the preserved claims worth?**
   Run the damages framework from the root skill. If claims total
   $50,000+ and the CFK offer is $3,000, that's trading dollars for
   pennies.

3. **Is there an attorney or active investigation?**
   - Active OIG investigation — signing may undermine the investigation
   - Attorney engaged — attorney must review before signing
   - NPR/media story — signing may eliminate the story's leverage

4. **Is the deadline real?**
   CFK deadlines are usually negotiable. Ask for an extension.
   They almost always grant one.

5. **What happens if you don't sign?**
   - UD filing (court process, takes weeks to months)
   - You remain in the home during the court process
   - No relocation payment
   - Eviction may appear on record (but can be contested)

### Decision tree

Do you have documented regulatory violations?

NO — CFK may be reasonable. Negotiate best amount and timeline.

YES — Are violations worth more than CFK offer?

  NO or UNCLEAR — Consult attorney before signing.

  YES —
    Do you have an attorney? — DO NOT SIGN until attorney reviews.
    Active OIG/congressional investigation? — DO NOT SIGN.
    No attorney, no investigation? — File complaints BEFORE signing
    (CFPB, credit disputes — preserves the record even if you later sign).
    Negotiate: more money, more time, or narrower release scope.

---

## Eviction Defense Checklist

### If UD has NOT been filed yet

- [ ] Save all documents received (scan, photograph, date-stamp)
- [ ] Check county court viewer daily for filings
- [ ] Confirm whether RCW 61.24.060 notice was properly served
- [ ] Contact legal aid / eviction defense hotline
- [ ] Notify congressional contacts that eviction process is advancing
- [ ] Evaluate bankruptcy as emergency option
- [ ] Do NOT sign Cash for Keys without attorney review

### If UD HAS been filed

- [ ] **Note the date of SERVICE** (not filing). 20-day response clock starts from service.
- [ ] **Call legal aid SAME DAY**
- [ ] **Call congressional office SAME DAY**
- [ ] **Evaluate emergency bankruptcy filing** — automatic stay stops the UD immediately
- [ ] **Do NOT ignore the filing.** Failure to respond = default judgment = writ of restitution.
- [ ] **Gather all eviction-defense documents**

---

## Bankruptcy as Emergency Stay

### What it does
Filing bankruptcy (any chapter) triggers an **automatic stay**
under 11 U.S.C. §362. This immediately stops:
- Eviction proceedings (UD)
- Any collection activity
- Any attempt to take possession

### What it does NOT do
- Does not get the house back (VA owns it)
- Does not address underlying violations
- Does not prevent eventual eviction once stay lifts
- Creates a bankruptcy on your record

### When to use it
- **Emergency brake** when UD is filed and you need time
- File AFTER the UD is filed but BEFORE judgment
- Stops the proceeding already in motion

### Practical considerations
- Chapter 7 is simpler and cheaper than Chapter 13
- VA disability income is exempt from means testing [VERIFY]
- An attorney should file this
- This is a one-time-use card — use it strategically

---

## VA Authority: What VA Can Do With the Property

VA has broad authority under 38 U.S.C. §3732 over properties it
acquires. This is leverage — VA doesn't HAVE to evict.

| VA option | Authority | What it means |
|-----------|----------|--------------|
| **Sell** | §3732(a) | VA can sell at or below market |
| **Lease** | §3732(a) | VA can lease back to the veteran |
| **Convey** | §3732(a) | VA can transfer title |
| **Hold** | §3732(c) | VA manages the property while deciding |

### The lease-back argument

VA has the authority to lease the property back to the veteran.
Arguments for it:
- Avoids REO disposition costs (~$72K)
- Veteran stays housed, reducing downstream VA healthcare costs
- Avoids contested eviction and litigation
- Clean resolution for all parties
- Congressional office can request this directly

---

## Occupancy Rights Quick Reference

### Washington State (non-judicial foreclosure)

| Your status | Your rights | Timeline |
|------------|------------|---------|
| **Former owner** | Purchaser entitled to possession on 20th day post-sale. Must file UD to remove you — no self-help eviction. | 20 days post-sale, then UD process |
| **Tenant with lease** | 90 days notice or lease term, whichever is longer (PTFA) | 90+ days from notice |
| **Month-to-month tenant** | 90 days notice (PTFA) | 90 days from notice |

### Universal rule
**No one can remove you without a court order.** Changing locks,
shutting off utilities, removing belongings, or threatening/
intimidating you into leaving is an illegal self-help eviction
regardless of your status.

---

## The institutional conflict of interest
VA is simultaneously:
- The agency whose oversight failures contributed to the foreclosure
- The property owner who can evict the family
- The agency being investigated by OIG for those failures
- The agency receiving congressional inquiries about the case

This conflict is a strategic asset. Name it in every congressional
communication. It is the single most compelling argument for why
VA should pause eviction proceedings.
