# Call Recording Guide

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Step 3.

How to process, summarize, and use call recordings with servicers,
VA, and other parties for advocacy purposes.

---

## Before You Record

### State recording laws

**One-party consent states** (including Washington): Only one party to the
call needs to know it's being recorded. If you're on the call, you can
record it without telling the other party. `[VERIFY your state's law]`

**Two-party/all-party consent states** (California, Florida, Illinois,
others): ALL parties must consent. If the servicer is in a two-party
state, their recorded disclosure at the start ("this call may be
recorded") constitutes their consent — and yours. `[VERIFY]`

**Federal calls (VA):** Federal agencies typically disclose recording at
the start of calls. This constitutes their consent.

### Practical recording setup

- **Phone app:** Most smartphones have built-in recording (Samsung: Phone
  app → three dots → Settings → Record calls)
- **Speakerphone + external recorder:** Place phone on speaker, record
  with a second device
- **Otter.ai / TurboScribe:** Upload audio files for automated transcription

---

## What to Listen For

### Admissions against interest

These are statements by the servicer or VA that contradict their official
position or acknowledge errors. Flag any of these:

| Category | Example statements |
|----------|-------------------|
| **Acknowledging the error** | "I see there was a miscalculation..." "That shouldn't have happened..." "Let me look into why that was processed that way..." |
| **Contradicting official letters** | "I know the letter said X, but actually..." "That letter was generated automatically..." "That doesn't reflect what our records show..." |
| **Admitting non-compliance** | "We didn't get to review that yet..." "That wasn't submitted to the system..." "I don't see that in VALERI..." |
| **Blaming the system** | "The system generated that automatically..." "That's how the process works, I can't change it..." "That fell through the cracks..." |
| **Promising action not taken** | "I'll make sure that gets reviewed..." "I'm escalating this..." "Someone will call you back..." (and no one did) |
| **Confirming timeline facts** | Any statement that confirms or contradicts dates in the written record |

### VA-specific statements to flag

- VA technician confirming the servicer never submitted to VALERI
- VA stating they are "fighting for" the borrower
- VA acknowledging a gap in the system
- VA confirming they communicated with the servicer about loss mitigation

---

## Transcript Summary Format

Create a structured summary for each recording. This format is designed
to be usable in complaints, briefs, and attorney intake packages.

```
CALL RECORDING SUMMARY

Date:           [date of call]
Time:           [start time - end time]
Duration:       [minutes]
Participants:   [your name] and [other party name, title, organization]
Recorded by:    [who recorded]
Recording file: [filename]
Transcription:  [Otter.ai / TurboScribe / manual]

CONTEXT
[1-2 sentences: why you called, what was happening in the case at this point]

KEY STATEMENTS (with approximate timestamps)

[timestamp] [speaker]: [summary of statement]
  → SIGNIFICANCE: [why this matters — admission, contradiction, promise]

[timestamp] [speaker]: [summary of statement]
  → SIGNIFICANCE: [why this matters]

[continue for each key statement]

COMMITMENTS MADE
- [person] committed to [action] by [date/timeframe]
- [person] committed to [action] by [date/timeframe]

COMMITMENTS FULFILLED?
- [action]: YES / NO / UNKNOWN (as of [date])

CONTRADICTIONS WITH WRITTEN RECORD
- Statement: [what was said on the call]
  Written record: [what the letter/email says]
  Contradiction: [how they conflict]

OVERALL ASSESSMENT
[2-3 sentences: what this call proves or disproves for the case]
```

---

## Processing Workflow

### Step 1: Record

- Record every call with the servicer, VA, VRM, or any party to the case
- Save the recording immediately with this naming convention:
  `YYYYMMDD_[SOURCE]_RECORDING_[brief-description].m4a`

### Step 2: Transcribe

- Upload to **Otter.ai** or **TurboScribe** for automated transcription
- Review the transcript for accuracy — automated tools make errors,
  especially with names, loan numbers, and legal terms
- Save the transcript alongside the recording

### Step 3: Summarize

- Use the summary format above
- Focus on admissions, contradictions, and commitments
- Note timestamps for key statements so they can be verified

### Step 4: Flag for advocacy use

- Which statements support specific violations? (cross-reference with
  violation-checklist.md)
- Which statements contradict the servicer's written position?
- Which commitments were broken?
- Which statements would be powerful in a complaint narrative?

### Step 5: Store

- Raw recording → `08_RECORDINGS/Raw/`
- Transcript → `08_RECORDINGS/Transcripts/`
- Summary → `08_RECORDINGS/Summaries/`

---

## Legal Use Considerations

### What recordings can do

- **Corroborate** written evidence (VA technician on the phone confirming
  what's in the email)
- **Fill gaps** where no written record exists (verbal commitments,
  informal acknowledgments)
- **Contradict** the servicer's official position (recorded admission
  vs. form letter denial)
- **Establish timeline** when written records are incomplete

### What recordings cannot do (without attorney guidance)

- Serve as the sole basis for a legal claim (need corroborating evidence)
- Be submitted in court without authentication procedures
- Replace written documentation for RESPA/FCRA purposes

### Privilege considerations

- Recordings of your own calls are your property
- Share with your attorney under attorney-client privilege
- Share with reporters, congressional staff, or agencies at your discretion
- Do NOT share recordings that include conversations with your own attorney

---

## Quick Reference: What to Say on Calls

Before calling the servicer, VA, or VRM:

**Start with:**
- "I'm calling about loan number [number]"
- "Can I get your name and ID number for my records?"
- "I'd like to understand [specific issue]"

**During the call:**
- Take notes even if recording — write down names, times, key statements
- Ask: "Can you repeat that?" if they say something significant
- Ask: "Is that documented in the file?" for any claim they make
- Ask: "When will [action] be completed?" for any commitment

**End with:**
- "So to confirm, you're saying [restate key points]?"
- "And you committed to [action] by [date]?"
- "What's the best way to follow up if I don't hear back?"
- Note the time the call ended
