# De-Identification Guide for Community Release

Reference file for Phase 3 community release.

How to strip case-specific identifying information while preserving the
skill's analytical framework for other users.

---

## What to Replace

| Category | Examples | Replace with |
|----------|---------|-------------|
| **Names** | Borrower, spouse, children, VA technicians, congressional staffers, reporters, VSO contacts | `[BORROWER]`, `[VETERAN]`, `[SPOUSE]`, `[VA TECHNICIAN]`, `[STAFFER]` |
| **Loan numbers** | VA loan number, reference numbers | `[LOAN NUMBER]`, `[OIG REF]` |
| **Addresses** | Property address, mailing addresses | `[PROPERTY ADDRESS]`, `[CITY, STATE ZIP]` |
| **Phone numbers** | Personal, office | `[PHONE]` |
| **Email addresses** | Personal, work | `[EMAIL]` |
| **Specific dates** | Dates tied to the individual case | Keep date FORMAT but replace: `[DATE: forbearance entry]`, `[DATE: mod offer]` |
| **Dollar amounts** | Specific to the individual case | Keep the CALCULATION METHOD, replace the numbers: `$[MONTHLY OVERCHARGE]` |
| **Servicer name** | Only if releasing a generic version | Keep servicer name — the enforcement history is public record. Or use `[SERVICER]` for fully generic version. |
| **Disability rating** | Specific percentage | `[DISABILITY RATING]%` |
| **Medical details** | Specific conditions | `[SERVICE-CONNECTED CONDITIONS]` |
| **Case-specific evidence** | Specific exhibit references | `[EXHIBIT: description]` |

---

## What to Keep

These elements are NOT identifying and should remain intact:

- **Regulatory citations** — 38 CFR 36.4319, 12 CFR §1024.41, RCW 61.24, etc.
- **Violation framework** — all 9 categories, elements, counterarguments
- **Calculation methods** — escrow overcharge formula, damages framework
- **Process steps** — the full 13-step workflow
- **Agency filing instructions** — URLs, required fields, template structures
- **Political strategy framework** — partisan framing matrices, timing guidance
- **Equity assessment framework** — protected class factors, data sources
- **Phone scripts** — structure and approach (replace specific names/numbers)
- **Style files** — these are universal

---

## State Adaptation for Other Jurisdictions

The skill defaults to Washington state for state-specific provisions.
For community release, provide adaptation instructions:

### Minimum adaptation needed

1. **Replace RCW 61.24** with your state's foreclosure statute
   - Judicial states: different process entirely (court filing required)
   - Non-judicial states: different notice/timeline requirements
2. **Replace RCW 19.86** with your state's consumer protection act
3. **Replace RCW 84.36.381** with your state's disabled veteran property
   tax exemption
4. **Check pre-suit demand requirements** — some states require a demand
   letter before filing CPA claims
5. **Check SOL differences** — state SOLs vary significantly
6. **Check recording laws** — one-party vs. two-party consent

### Priority states for pre-built adaptations

| State | Why | VA foreclosure volume |
|-------|-----|----------------------|
| **Texas** | High VA population, DTPA has strong protections, 60-day pre-suit demand | High |
| **California** | High VA population, UCL/CLRA protections, two-party recording consent | High |
| **Florida** | High VA population, active foreclosure market, two-party consent | High |
| **Virginia** | Near military bases, high VA population | High |
| **North Carolina** | Near military bases, Camp Lejeune/Bragg | Medium |
| **Georgia** | Near military bases, non-judicial foreclosure | Medium |

---

## Release Package Structure

```
va-foreclosure-advocacy/
├── README.md                 # Install guide, overview, disclaimers
├── LICENSE                   # Apache 2.0 or AGPL-3.0
├── SKILL.md                  # Root skill (already de-identified)
├── references/               # All reference files (de-identified)
├── styles/                   # All 4 style files (universal)
├── examples/                 # NEW for release
│   ├── sample-analysis.md    # Fictional case walkthrough
│   └── sample-dashboard.md   # What the dashboard looks like
└── state-adaptations/        # NEW for release
    ├── washington.md          # Default (built-in)
    ├── texas.md               # TX DTPA, TX foreclosure statute
    ├── california.md          # CA UCL/CLRA, CA foreclosure
    └── florida.md             # FL FDUTPA, FL foreclosure
```

---

## README Template for GitHub

```markdown
# VA Foreclosure Advocacy Skill

**The first borrower-side legal advocacy skill for Claude.**

Analyzes VA mortgage foreclosure cases for regulatory violations and
builds advocacy strategies from the veteran's perspective.

## Who This Is For

- Veterans and military families facing foreclosure
- VSO caseworkers (WWP, DAV, VFW, American Legion)
- Legal aid attorneys (NVLSP, Veterans Consortium, NJP)
- Congressional constituent services staff
- Social workers and MSW students
- Investigative journalists
- State AG consumer protection divisions

## What It Does

- Identifies 9 categories of servicer violations with evidence checklists
- Anticipates servicer counterarguments and builds rebuttals
- Assesses equitable impact on protected populations
- Calibrates advocacy framing by political audience
- Tracks statutes of limitations
- Generates prioritized next-action lists
- Includes pre-built Claude styles for accessible formatting

## Quick Start

1. Download this repository
2. Upload `SKILL.md` to Claude: Settings → Capabilities → Skills → Add
3. Install the Field Manual style: copy description from
   `styles/field-manual.md` → Settings → Style → Create style
4. Upload your case documents and say: "Analyze this VA foreclosure case"

## What Makes This Different

- Built from the borrower's perspective, not the lender's
- Designed for crisis-context use with zero-decision-point philosophy
- Ships with 4 pre-built Claude styles for accessible formatting
- Includes trauma-informed language guidance
- Low-spoon quick-start mode for limited capacity sessions
- Political strategy layer with partisan framing matrices
- Equitable impact assessment for enforcement prioritization

## Important

**NOT LEGAL ADVICE.** This skill produces advocacy analysis. Attorney
review is required before filing any legal document.

## License

[Apache 2.0 / AGPL-3.0 — decision pending]

## Credits

Created by Leann Ledford — social worker, WA State Certified Victim
Advocate, MSW graduate student, 2022 Elizabeth Dole Foundation Fellow,
and USMC disabled veteran spouse and caregiver.

Built from lived experience navigating a wrongful VA foreclosure.
```

---

## Checklist Before Release

- [ ] All personal names replaced with placeholders
- [ ] All loan/reference numbers replaced
- [ ] All addresses replaced
- [ ] All phone numbers and emails replaced
- [ ] Case-specific dates replaced with descriptive placeholders
- [ ] Dollar amounts replaced with calculation methods
- [ ] Medical details removed or generalized
- [ ] State-specific provisions clearly marked for adaptation
- [ ] README written with install instructions
- [ ] License file included
- [ ] Sample analysis with fictional case included
- [ ] Tested by someone who is NOT the author (fresh eyes)
- [ ] NOT LEGAL ADVICE disclaimer in README, SKILL.md, and every
  reference file
