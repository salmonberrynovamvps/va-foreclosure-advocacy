# NotebookLM Integration Guide

Reference file for `va-foreclosure-case-analyzer` SKILL.md, Guidelines.

How to use Claude and NotebookLM as a dual-tool system.
Claude builds arguments. NotebookLM finds facts with citations.
The verification loop prevents errors.

---

## Who Does What

| Task | Best tool | Why |
|------|----------|-----|
| **Searching your documents for specific facts** | NotebookLM | Cites exact source with page/paragraph reference |
| **Building timelines from source documents** | NotebookLM | Grounds every date in a specific document |
| **Finding contradictions between documents** | NotebookLM | Compares across sources with citations |
| **Strategic analysis and argument development** | Claude | Connects facts to legal frameworks, builds advocacy |
| **Drafting emails, complaints, briefs** | Claude | Produces formatted, audience-calibrated outputs |
| **Researching regulations, enforcement history** | Claude | Web search, regulatory databases |
| **Political strategy and framing** | Claude | Audience calibration, partisan analysis |
| **Absorbing case complexity passively** | NotebookLM | Audio Overview feature — listen while doing other things |

---

## The Workflow Loop

1. NotebookLM finds the facts (with citations)
2. You paste findings into Claude
3. Claude builds the argument / draft
4. You verify Claude's output against NotebookLM
5. Correct any errors — repeat if needed

**Why the loop matters:** Claude can hallucinate legal citations.
NotebookLM can miss context. Together, they cover each other's
weaknesses.

---

## Recommended Notebook Structure

### 7-notebook hub-and-spoke model

| # | Notebook | Purpose | Key sources |
|---|----------|---------|------------|
| 1 | **[LEGAL] Servicer Violations** | All servicer correspondence, modification docs | FM letters, mod agreement, escrow statements, payment history |
| 2 | **[LEGAL] VA Communications** | All VA correspondence, VALERI-related docs | VA letters, technician emails, OIG filings, VA circulars |
| 3 | **[LEGAL] Financial Records** | Loan docs, escrow, tax records, fee itemization | Note/deed of trust, escrow disclosures, county tax records |
| 4 | **[CONGRESS] Advocacy** | Hearing transcripts, legislation, congressional correspondence | HVAC hearing videos (YouTube URLs), H.R. 1815 text, staffer emails |
| 5 | **[MEDIA] Press** | Reporter correspondence, published articles, background memos | NPR emails, shared docs, published articles |
| 6 | **[POLICY] Enforcement History** | Servicer's enforcement record, consent orders, CFPB data | Enforcement actions, consent orders, CFPB complaint data |
| 7 | **[MASTER] Hub** | Summaries from notebooks 1-6 + legal timeline | Generated summaries, comprehensive timeline |

### Setup order (by urgency)

1. Most urgent notebook first — whichever supports your next deadline
2. Don't try to set up all 7 at once — 2-3 per session is realistic
3. The MASTER hub comes last (it needs summaries from the others)

---

## Starter Prompts by Notebook

### Notebook 1: Servicer Violations

- "Build a complete timeline of every communication from [servicer name],
  with exact dates and the source document for each."
- "Find any contradictions between different [servicer] letters."
- "What escrow amounts are documented? Do any reflect property tax
  charges that should have been exempt?"
- "What modification terms were offered? List every offer with the rate,
  payment amount, and date."

### Notebook 2: VA Communications

- "What did VA technicians say about the status of this loan at each
  point in the timeline?"
- "According to VA's own regulations in M26-4 Chapter 5, what steps was
  the servicer required to complete before foreclosure? Which steps were
  skipped?"
- "Compare VA's statement that [servicer] never submitted to VALERI
  against [servicer's] claim they offered modifications."

### Notebook 3: Financial Records

- "Calculate the total property taxes paid from escrow for each year.
  If exemption should have been applied starting [date], what is the
  total overcharge?"
- "What fees has [servicer] charged? Itemize every fee type with dates
  and amounts."
- "What reinstatement figures were provided to third parties (VSOs,
  nonprofits)? Were they consistent with the actual balance?"

### Notebook 4: Congressional Advocacy

- "Summarize the key testimony from the [date] hearing. Who testified?
  What did they say about [specific topic]?"
- "Did any member of Congress make specific requests or demands of VA
  during this hearing?"
- "What data was presented about VA foreclosure rates, REO disposition,
  or partial claim implementation?"

### Notebook 7: Master Hub

- "Based on all available evidence, what are the five strongest legal
  claims in this case, ranked by strength of evidence?"
- "What gaps exist in the documentation? What evidence do I still need?"
- "Draft a one-page case summary suitable for a congressional staffer."

---

## Bringing NotebookLM Findings to Claude

When pasting NotebookLM output into Claude:

1. **Copy the full output** including citation numbers
2. **Tell Claude which notebook** it came from
3. **State what you need Claude to do** with the findings

**Example prompt:**

"Here are findings from my NotebookLM [LEGAL] Servicer Violations
notebook. NotebookLM found contradictions between FM's January 15
and February 3 letters. Use these findings to draft the dual-tracking
section of the CFPB complaint narrative."

---

## Tips

- **Select specific sources** before each query — don't leave all
  sources checked. Narrow = better results.
- **Rename sources** after uploading. Change auto-generated titles to
  descriptive names.
- **Save valuable responses as Notes** (pin icon). Back up to Google Docs.
- **Audio Overviews** — generate a "Deep Dive" and listen while doing
  other tasks. It surfaces connections you miss while reading.
- **YouTube videos** — NotebookLM pulls captions/transcripts automatically.
  Add hearing video URLs directly as sources.

---

## Privacy Note

NotebookLM uses your Google account. If using a personal (not Workspace)
account, Google's privacy terms allow human review of uploaded content
if you provide feedback.

**Recommendations:**
- Use Google Workspace account for sensitive documents if available
- Redact SSN, account numbers, medical details before uploading
- Don't upload the most sensitive documents — use summaries instead
- Google Drive documents added as sources stay within your existing
  Google security framework
