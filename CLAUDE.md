# CLAUDE.md

## First-Time Setup

**Claude:** If you see `[PLACEHOLDER]` markers, this project hasn't been initialized yet. Run the onboarding flow below.

---

### Onboarding Flow

**Step 0: Extension Selection**

This is a **uno** (Delegate) protocol — AI works FOR you.

Ask:

> "Which extension fits this project?
>
> **ea** — Executive Assistant
> Time-sensitive projects with deadlines, stakeholder management, knowledge acquisition.
> *Creates: UPDATES.md, GLOSSARY.md, KNOWLEDGE.md, SYSTEMS.md*
>
> **pa** — Personal Assistant
> Logistics and planning: trips, events, moves, personal finance.
> *Creates: ITINERARY.md, BOOKINGS.md, BUDGET.md, NOTES.md*
>
> **km** — Knowledge Manager
> Documentation, archives, reference material, recurring tasks.
> *Creates: LOG.md, PLANNED.md*
>
> **none** — Base uno
> Simple delegation without domain-specific tracking."

Once selected, create extension-specific files (see Extension File Templates below).

**Step 1: Discovery Questions**

Ask conversationally, one at a time:

1. "What is this project? Give me the one-liner."
2. "Who is it for?"
3. "What problem does it solve?"
4. "What does success look like?"
5. "Any constraints I should know?"

**For specific extensions, also ask:**

- **ea:** "What's the timeline? Key milestones? Stakeholders to meet?"
- **pa:** "What are the dates? Destinations/locations? Budget approach?"
- **km:** "What domains/topics? Any recurring tasks?"

**Step 2: Reflect Understanding**

```
"Let me make sure I understand:

**Project:** [What we're building]
**Users:** [Who it's for]
**Problem:** [What's broken today]
**Success:** [How we'll know it works]
**Constraints:** [Limits or requirements]

Does this capture it?"
```

**Step 3: Populate Docs**

Once confirmed:

1. **Create extension files** (if ea/pa/km selected — see templates below)
2. **Update core files:**
   - `CLAUDE.md` — Replace placeholder sections, set protocol header to `uno/[ext] v2.0`
   - `TODO.md` — Create prioritized task list **with acceptance criteria**
   - `MAREK.md` — Add any human-only tasks identified
   - `PROGRESS.md` — Log this initialization session
   - `README.md` — Replace with project description, add "What is uno/[ext]?" section

Remove all `[PLACEHOLDER]` markers when done.

**Step 4: Confirm Ready**

```
"Project initialized! Ready to work.

Use `..start` to begin a session."
```

**Step 5: Commit & Push**

```bash
git add -A && git commit -m "Initialize project: [PROJECT_NAME]" && git push
```

---

## protocol-uno v2.0

This project uses the **uno** (Delegate) protocol — AI works FOR you.

**uno = Delegate:** You define WHAT, AI handles HOW.

> Protocol source: [KayGee Protocol Family](https://github.com/marekgorski/admin/tree/main/protocol)

### Task Ownership Markers

Tasks use markers to indicate who can complete them:

| Marker | Meaning | Example |
|--------|---------|---------|
| `[C]` | Claude can complete | `[C] Write intro section` |
| `[M]` | Marek must complete | `[M] Record demo video` |
| `[C→M]` | Claude prepares, Marek executes | `[C→M] Draft email template` |
| `[M→C]` | Marek decides, Claude implements | `[M→C] Choose target audience` |

**No marker = `[C]`** — Tasks without markers are assumed Claude-completable.

`[C]` tasks live in **TODO.md**. `[M]` tasks live in **MAREK.md**.

---

### Commands

| Command | Purpose |
|---------|---------|
| `..start` | Load context, check MAREK.md for completed human tasks, show top priority |
| `..end` | **Verify AC**, update TODO/PROGRESS/MAREK, commit |
| `..hygiene` | Archive old entries when files grow large |

---

### `..start`

**Base behavior (all extensions):**
1. Read all .md files
2. Check MAREK.md "Completed" section for human tasks that unblock work
3. Flag stale `[M]` tasks (>7 days)
4. Report top `[C]` priority task (with acceptance criteria)

**Extension-specific additions:**

#### uno/ea (Executive Assistant)
```
1. Calculate status (T-N or Day N of timeline)
2. Check pace (meetings/day, deliverables vs targets)
3. Surface risks (what might slip at current pace?)
4. Check UPDATES.md (days until next update due)
5. Knowledge quiz (3-5 questions from GLOSSARY.md)
6. Today's #1 priority
```

#### uno/pa (Personal Assistant)
```
1. Timeline check (what's coming up in next 7 days?)
2. Booking deadlines (what expires soon? what needs confirmation?)
3. Budget status (spent vs planned, any overruns?)
4. Conditions check (weather, alerts, travel advisories if relevant)
5. Today's logistics priority
```

#### uno/km (Knowledge Manager)
```
1. Check LOG.md for pending items
2. Check PLANNED.md for recurring tasks due
3. Flag stale documentation (not updated in 30+ days)
4. Today's documentation priority
```

**Response format (base):**
```
"Context loaded.

**Top priority:** [TASK]
- AC: [criterion 1]
- AC: [criterion 2]

**Human tasks:** [any completed or stale items]

Ready to work."
```

**Response format (uno/ea):**
```
"## Daily Briefing — [Day N/Total or T-N]

**Status:** [Phase] | [Days left] | [Key metric pace]

### This Week
| Day | Priority | Deliverable Due |
|-----|----------|------------------|

### Pace Check
- [Metric]: [X/Y complete] — need [Z/day] to hit target

### Risks
- [Anything at risk of slipping]

### Knowledge Quiz
1. [Question]
2. [Question]
3. [Question]

### Today's #1 Priority
> [Single most important thing]

---
Ready to work."
```

**Response format (uno/pa):**
```
"## Trip Briefing — [Date]

**Timeline:** [Current leg/phase] | [Days until next transition]

### Coming Up (Next 7 Days)
| Date | Event/Activity | Status |
|------|----------------|--------|

### Action Required
- [Bookings expiring, confirmations needed]

### Budget
- Spent: [X] / Planned: [Y] | [On track / Over by Z]

### Today's Priority
> [Most important logistics task]

---
Ready to work."
```

---

### `..end`

**CRITICAL: Verify before marking complete.**

1. **For each task worked on:**
   - Check each acceptance criterion explicitly
   - If AC not met: Note what's missing, do NOT mark `[x]`
   - If AC met: Mark `[x]` in TODO.md
2. **For `[C→M]` tasks completed:**
   - Verify deliverable exists
   - Move to MAREK.md "Ready for Marek" section
3. Add session entry to `PROGRESS.md` (newest at top)
4. Commit: `git add -A && git commit -m "docs: [summary]" && git push`
5. Report next `[C]` priority

**Response format:**
```
"Session closed.

**Completed:** [TASKS with AC verified]
**Handed off:** [any C→M tasks moved to MAREK.md]
**Next priority:** [NEXT_TASK]

Changes committed and pushed."
```

**If AC not met:**
```
"Cannot mark complete — AC not met:

**Task:** [TASK]
**Missing:** [What's not done]

Options:
1. Continue working to meet AC
2. Close session without marking complete"
```

---

### `..hygiene`

Run when files grow large (PROGRESS.md > 30KB, TODO.md > 100 items):

1. Archive old PROGRESS entries (> 30 days) to `_archive/PROGRESS_[YYYY-MM].md`
2. Archive completed TODO items to `_archive/TODO_DONE_[YYYY-MM].md`
3. Archive completed MAREK.md items to `_archive/MAREK_DONE_[YYYY-MM].md`
4. Report what was archived

---

## Extension File Templates

Create these files during onboarding based on selected extension.

### uno/ea Files

**UPDATES.md:**
```markdown
# Updates

Weekly updates and stakeholder communications.

---

## Update Cadence

| Update | Audience | Frequency | Day |
|--------|----------|-----------|-----|
| [Name] | [Who] | Weekly | [Day] |

---

## Upcoming

### [Date] — [Update Name]

**Status:** Draft / Ready / Sent

**Key points:**
- [Point 1]
- [Point 2]

**Hypothesis to test this week:**
> [What we're trying to learn]

---

## Sent

(Move completed updates here)
```

**GLOSSARY.md:**
```markdown
# Glossary

Domain terms and acronyms to learn.

| Term | Definition | Learned |
|------|------------|------|
| [TERM] | [Definition] | [ ] |
```

**KNOWLEDGE.md:**
```markdown
# Knowledge

Quiz tracking and learning log.

---

## Quiz Log

| Date | Questions | Score | Notes |
|------|-----------|-------|-------|

---

## Key Learnings

(Document important insights here)
```

**SYSTEMS.md:**
```markdown
# Systems

Tools and access inventory.

| System | Purpose | Access | Status |
|--------|---------|--------|--------|
| [Tool] | [What it's for] | [URL/how] | ✅ / ❌ |
```

---

### uno/pa Files

**ITINERARY.md:**
```markdown
# Itinerary

Trip timeline and legs.

---

## Overview

| Leg | Dates | Location | Nights |
|-----|-------|----------|--------|
| 1 | [Start] - [End] | [City/Country] | [N] |

---

## Leg 1: [Location]

**Dates:** [Start] — [End]
**Accommodation:** [Hotel/Airbnb]
**Transport in:** [Flight/Train/Car]
**Transport out:** [Flight/Train/Car]

### Activities
- [ ] [Activity 1]
- [ ] [Activity 2]

### Notes
[Location-specific info, tips, reservations needed]
```

**BOOKINGS.md:**
```markdown
# Bookings

All reservations and confirmations.

---

## Flights

| Date | Route | Airline | Confirmation | Status |
|------|-------|---------|--------------|--------|
| [Date] | [From] → [To] | [Airline] | [Code] | ✅ Booked / ⏳ Pending |

---

## Accommodation

| Dates | Location | Property | Confirmation | Status |
|-------|----------|----------|--------------|--------|
| [Check-in] - [Check-out] | [City] | [Name] | [Code] | ✅ / ⏳ |

---

## Transport

| Date | Type | Details | Confirmation | Status |
|------|------|---------|--------------|--------|
| [Date] | Car rental / Train | [Details] | [Code] | ✅ / ⏳ |

---

## Activities

| Date | Activity | Location | Confirmation | Status |
|------|----------|----------|--------------|--------|
| [Date] | [Activity] | [Where] | [Code] | ✅ / ⏳ / Not yet booked |
```

**BUDGET.md:**
```markdown
# Budget

Trip cost tracking.

---

## Summary

| Category | Planned | Actual | Remaining |
|----------|---------|--------|----------|
| Flights | [X] | [Y] | [Z] |
| Accommodation | | | |
| Transport | | | |
| Activities | | | |
| Food | | | |
| Buffer | | | |
| **TOTAL** | | | |

---

## By Leg

### Leg 1: [Location]

| Item | Category | Planned | Actual | Notes |
|------|----------|---------|--------|-------|
| [Hotel Name] | Accommodation | [X] | [Y] | |

---

## Expenses Log

| Date | Item | Category | Amount | Notes |
|------|------|----------|--------|-------|
```

**NOTES.md:**
```markdown
# Notes

Research, ideas, and preferences.

---

## Research

### [Location/Topic]

**Context:** [What you need to know, constraints]

**Options:**

| Option | Location | Notes | Est. Price |
|--------|----------|-------|------------|
| **[Name]** | [Where] | [Key details] | [Price] |

**Recommendation:** [Best option and why]

---

## Preferences

- [Preference 1]
- [Preference 2]

---

## Ideas

- [ ] [Idea to explore]
```

---

### uno/km Files

**LOG.md:**
```markdown
# Log

Append-only audit trail.

---

| Date | Action | Details |
|------|--------|--------|
| [Date] | [What was done] | [Notes] |
```

**PLANNED.md:**
```markdown
# Planned

Recurring and scheduled tasks.

---

## Recurring

| Task | Frequency | Last Done | Next Due |
|------|-----------|-----------|----------|
| [Task] | Weekly/Monthly | [Date] | [Date] |

---

## Scheduled

| Task | Due Date | Status |
|------|----------|--------|
| [Task] | [Date] | Pending / Done |
```

---

## TODO Format (Required)

Every task needs acceptance criteria:

```markdown
- [ ] [C] Task description
  - AC: Specific testable condition
  - AC: Another condition (if needed)
```

**Examples:**

```markdown
BAD:  - [ ] Write intro section
GOOD: - [ ] [C] Write intro section
        - AC: Explains problem in <100 words
        - AC: Includes one concrete example
```

---

## MAREK.md Structure

Human-only tasks organized by status:

```markdown
## ⏸️ Blocked (needs Marek action)
- [ ] [M] Task → blocks [component]

## ✅ Ready for Marek (Claude prepared)
- [ ] [C→M] Deliverable ready → /drafts/file.md

## ❓ Waiting on Marek Decision
- [ ] [M→C] Decision question?
  - Options: A, B, C
  - Unblocks: [what Claude will do]

## ✅ Completed
- [x] [M] Task — Date
  - Output: [result]
  - Unblocks: [what's now ready]
```

---

## Handoff Protocol

### Claude completing [C→M] task
1. Create deliverable in appropriate location
2. Move task to MAREK.md "Ready for Marek"
3. Note in PROGRESS.md

### Marek completing [M] task
1. Mark complete in MAREK.md with output
2. Claude checks on next `..start` and unblocks dependent work

### Marek making [M→C] decision
1. Add decision to MAREK.md "Completed"
2. Claude picks up on next session

---

## Anti-Patterns to Avoid

| Anti-Pattern | Consequence | Prevention |
|--------------|-------------|------------|
| TODO without AC | "Done" but incomplete | Always include AC |
| No task markers | Claude attempts `[M]` tasks | Use ownership markers |
| `[M]` without blocker note | Unclear what's waiting | Note "Blocks: X" |
| Skipping `..end` | PROGRESS.md out of sync | Always run `..end` |
| Stale `[M]` tasks | Work stuck indefinitely | `..start` flags >7 days |

---

## Quick Rules

1. **AC is required** — Every TODO needs acceptance criteria
2. **Task ownership** — `[C]` in TODO.md, `[M]` in MAREK.md
3. **Verify before done** — Check AC explicitly, don't assume
4. **Docs are source of truth** — Update TODO/PROGRESS/MAREK after changes
5. **Commit after each task** — Don't let work pile up locally

---

## Environment Notes

Document tool-specific quirks and workarounds here.

| Tool/Integration | Known Behavior | Workaround |
|------------------|----------------|------------|
| [Your Tool] | [Behavior] | [Workaround] |

---

## Project Overview

> **Not yet initialized.** Run onboarding flow above.

**Project:** [PROJECT_NAME]

**One-liner:** [BRIEF_DESCRIPTION]

**Status:** Not started

---

## Structure

```
[PROJECT_NAME]/
├── CLAUDE.md      # Technical reference + protocol (this file)
├── TODO.md        # Prioritized task list (with AC)
├── PROGRESS.md    # Session-by-session log
├── MAREK.md       # Human-only tasks (rename to your name)
├── README.md      # User-facing documentation
└── _archive/      # Old entries (created by ..hygiene)
```

---

## Context

[PROJECT_SPECIFIC_INFORMATION]

---

## Conventions

[NAMING_PATTERNS_FILE_STRUCTURE_ETC]

---

*protocol-uno v2.0 — January 2, 2026*
