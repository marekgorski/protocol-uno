# NEWSFEED.md — Daily Context

**Purpose:** Dynamic daily newspaper — what's happening TODAY

**Rule:** NEWSFEED = today's story | PROGRESS = historical log | README = static reference

---

## [Date] — [Headline]

**Context in <2 min:**

[ELI5 summary that lets anyone understand current state without deep reading]

---

### What's Live Today

**Priority 1: [Focus Area]**

[Narrative with inline links - never orphaned]

Example: "Met with Bob about options pricing (see meeting notes in stakeholders/BOB.md, page 3 for edge cases). Key blocker: vendor API limits..."

**Priority 2: [Focus Area]**

[Narrative continues]

**Priority 3: [Focus Area]**

---

### Signals Detected

[From PERSONA.md Signal Watch list]

⚠️ **[Signal]:** [What was detected and why it matters]

Example:
⚠️ **Budget concern:** Engineering estimates 2x higher than planned (see UPDATES.md draft for Amy)

---

### Decisions Made Today

**[Decision Title]**
- **Context:** [Why this came up]
- **Chose:** [What we decided]
- **Trade-off:** [What we gave up]
- **Rationale:** [Why this choice]

[Move to CONSTRAINTS.md or PRINCIPLES.md if pattern emerges]

---

### Deliverables Status

| Deliverable | Due | Status | Updated Today? |
|-------------|-----|--------|----------------|
| Weekly Update #3 | Friday | Draft | ✅ Added Bob meeting |
| Budget Summary | Mon | Not started | ⏸️ Waiting on Engineering |

---

### Stakeholder Updates

[Who you interacted with today - links to stakeholders/ files]

- **Bob** — Options pricing discussion → Updated stakeholders/BOB.md with concerns
- **Amy** — Budget check-in → Drafted DM in TASKS/

---

### Tomorrow's Prep

**Top 3 Priorities:**
1. [Task] — [Why]
2. [Task] — [Why]
3. [Task] — [Why]

**Blockers to Clear:**
- [Blocker] → [Who can unblock]

---

## Link Quality Standard

❌ **BAD:** "Here's the link: https://..."

✅ **GOOD:** "The pricing edge cases (page 6) show three scenarios where..."

**Rule:** Links must be inline with narrative. Context first, link second.

---

## Archive Pattern

When NEWSFEED grows beyond current week:
- Move older entries to PROGRESS.md (historical log)
- Keep only current week in NEWSFEED
- Extract recurring patterns to PRINCIPLES.md or CONSTRAINTS.md

---

*Template from uno/ea*
