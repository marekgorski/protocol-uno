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
> *Creates: UPDATES.md, GLOSSARY.md, KNOWLEDGE.md, SYSTEMS.md, PERSONA.md*
>
> **pa** — Personal Assistant
> Logistics and planning: trips, events, moves, personal finance.
> *Creates: ITINERARY.md, BOOKINGS.md, BUDGET.md, NOTES.md, PERSONA.md*
>
> **km** — Knowledge Manager
> Documentation, archives, reference material, recurring tasks.
> *Creates: LOG.md, PLANNED.md, PERSONA.md*
>
> **none** — Base uno
> Simple delegation without domain-specific tracking."

Once selected, proceed to discovery questions.

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

**Step 3: Persona Configuration** (NEW — for ea/pa/km only)

After confirming project understanding, personalize the assistant:

```
"Now let's personalize how I work for you.

I'll ask a few questions about what you care about, how you make decisions,
and what signals matter. This shapes how I summarize and what I surface."
```

**For ea (Executive Assistant):**

Ask these one at a time:

1. **Decision Style**
   > "When you make decisions, what helps most?
   > - Bottom-line recommendation with reasoning
   > - Options with trade-offs (you choose)
   > - Data first, then implications
   > - Risks and downsides highlighted"

2. **Signal Watch**
   > "What signals should I always surface when I see them?
   >
   > Examples: 'budget concerns', 'executive pushback', 'timeline risk', 'competitor moves'"

3. **Noise Filter**
   > "What should I skip or minimize?
   >
   > Examples: 'technical implementation details', 'historical background'"

4. **Key Stakeholders**
   > "Who are the key people whose input I should always flag?
   >
   > Examples: CEO, direct manager, key client"

**For pa (Personal Assistant):**

Ask these one at a time:

1. **Planning Style**
   > "How do you approach planning?
   > - Detailed itineraries (hour by hour)
   > - Loose structure (key anchors only)
   > - Spontaneous (just logistics, no activities)
   > - Research-heavy (options for everything)"

2. **Priority Signals**
   > "What factors matter most in recommendations?
   >
   > Examples: cost/value, time efficiency, experience quality, convenience"

3. **Constraints**
   > "What constraints should I always factor in?
   >
   > Examples: 'dietary restrictions', 'budget ceiling', 'mobility needs', 'kid-friendly'"

4. **Interests**
   > "What are you drawn to? What should I surface?
   >
   > Examples: 'local food', 'hiking', 'live music', 'architecture'"

5. **Avoid**
   > "What should I filter out?
   >
   > Examples: 'tourist traps', 'long queues', 'expensive restaurants'"

**For km (Knowledge Manager):**

Ask these one at a time:

1. **Learning Style**
   > "How do you prefer to learn new material?
   > - Concepts first, then examples
   > - Examples first, then concepts
   > - Comparative (what's new vs. what I know)
   > - Problem-focused (what does this solve)"

2. **Depth Preference**
   > "What depth do you usually need?
   > - Surface (key points only)
   > - Working depth (enough to apply)
   > - Deep (full understanding with nuance)"

3. **Domain Focus**
   > "What domains or topics are you tracking?
   >
   > Examples: 'AI/ML', 'product management', 'industry news'"

**Step 4: Populate Docs**

Once confirmed:

1. **Create PERSONA.md** (if ea/pa/km selected — see template below)
2. **Create extension files** (see Extension File Templates below)
3. **Update core files:**
   - `CLAUDE.md` — Replace placeholder sections, set protocol header to `uno/[ext] v2.1`
   - `TODO.md` — Create prioritized task list **with acceptance criteria**
   - `MAREK.md` — Add any human-only tasks identified
   - `PROGRESS.md` — Log this initialization session
   - `README.md` — Replace with project description

Remove all `[PLACEHOLDER]` markers when done.

**Step 5: Confirm Ready**

```
"Project initialized! Ready to work.

Your assistant is personalized to:
- [Decision style / Planning style / Learning style]
- Surface: [Signal watch items / Interests]
- Filter out: [Noise filter items / Avoid items]

Use `..start` to begin a session. I'll apply your preferences automatically."
```

**Step 6: Commit & Push**

```bash
git add -A && git commit -m "Initialize project: [PROJECT_NAME]" && git push
```

---

## protocol-uno v2.1

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
| `..start` | Load context, apply persona filters, show personalized briefing |
| `..gm` | **Good morning** — Priorities, risks, DMs to send (ea extension) |
| `..end` | **Verify AC**, update TODO/PROGRESS/MAREK, commit |
| `..gn` | **Good night** — Deliverables check, commit, prep tomorrow (ea extension) |
| `..hygiene` | Archive old entries when files grow large |

---

### `..start`

**Base behavior (all extensions):**
1. Read all .md files including PERSONA.md
2. Check MAREK.md "Completed" section for human tasks that unblock work
3. Flag stale `[M]` tasks (>7 days)
4. Apply persona filters to all output
5. Report top `[C]` priority task (with acceptance criteria)

**Extension-specific additions with persona filtering:**

#### uno/ea (Executive Assistant)

Read PERSONA.md and apply:
- **Decision Style** → Structure recommendations accordingly
- **Signal Watch** → Surface matching items prominently
- **Noise Filter** → Minimize or skip matching items
- **Key Stakeholders** → Flag any mentions

```
"## Daily Briefing — [Day N/90 or T-N]

**Status:** [Phase] | [Days left] | [Key metric pace]

### Signals Detected
[Items matching Signal Watch from PERSONA.md]
⚠️ [Signal]: [Details]

### Decisions Needed
[Structured per Decision Style preference]
| Option | Trade-off | Risk |
|--------|-----------|------|

### This Week
| Day | Priority | Deliverable Due |
|-----|----------|------------------|

### Pace Check
- [Metric]: [X/Y complete] — need [Z/day] to hit target

### Filtered Out (per your preferences)
- [Count] items matching your noise filter

### Today's #1 Priority
> [Single most important thing]

---
Ready to work."
```

#### uno/pa (Personal Assistant)

Read PERSONA.md and apply:
- **Planning Style** → Structure itinerary accordingly
- **Priority Signals** → Weight recommendations
- **Constraints** → Filter and verify against all suggestions
- **Interests** → Surface matching opportunities
- **Avoid** → Filter out matching items

```
"## Trip Briefing — [Date]

**Timeline:** [Current leg/phase] | [Days until next transition]

### Matches Your Interests
[Items matching Interests from PERSONA.md]
🎵 [Venue] — [Why it matches]
📚 [Place] — [Why it matches]

### Coming Up (Next 7 Days)
| Date | Event/Activity | Status |
|------|----------------|--------|

### Action Required
- [Bookings expiring, confirmations needed]

### Constraints Check
[Verify against Constraints from PERSONA.md]
✓ [Constraint met]
⚠️ [Constraint at risk]

### Budget
- Spent: [X] / Planned: [Y] | [Status]

### Filtered Out
[Items matching Avoid from PERSONA.md]
- [Item] (reason filtered)

### Today's Priority
> [Most important logistics task]

---
Ready to work."
```

#### uno/km (Knowledge Manager)

Read PERSONA.md and apply:
- **Learning Style** → Structure content accordingly
- **Depth Preference** → Adjust detail level
- **Domain Focus** → Prioritize relevant items

```
"## Documentation Check — [Date]

### Priority Domains
[Filtered to Domain Focus from PERSONA.md]

### Pending in LOG.md
- [Items awaiting categorization]

### Learning Queue
[Structured per Learning Style preference]

### Recurring Tasks Due
[From PLANNED.md]

### Stale Documentation
- [Files not updated in 30+ days]

### Today's Priority
> [Based on depth preference and domain focus]

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

### `..gm` (Good Morning — ea extension)

**When to use:** Start of workday with uno/ea extension

**Purpose:** Morning briefing focused on today's execution

**Behavior:**
1. Read all .md files (PERSONA, NEWSFEED, TODO, PROGRESS, MAREK, herd/*)
2. Check NEWSFEED.md for yesterday's context
3. Check MAREK.md for completed tasks that unblock work
4. Surface today's priorities (filtered by PERSONA.md)
5. Flag risks and blockers
6. Suggest DMs to send (from herd/ files or MAREK.md drafts)

**Response format:**
```
"## Good Morning — [Date] — Day [N/90 or T-N]

**Yesterday's Context:**
[1-2 sentence summary from NEWSFEED.md]

**Today's Priorities:**
1. **[Task]** — [Why it matters] — [Estimated effort]
2. **[Task]** — [Why it matters] — [Estimated effort]
3. **[Task]** — [Why it matters] — [Estimated effort]

**Risks to Watch:**
⚠️ **[Risk]:** [Why it matters] — [From PERSONA Signal Watch]

**DMs to Send:**
- **[Person]** → [Draft ready in MAREK.md]
- **[Person]** → [Need to follow up on [topic]]

**Blockers:**
- [Blocker] → Waiting on [who/what]

**Ready to start with #1?**"
```

---

### `..gn` (Good Night — ea extension)

**When to use:** End of workday with uno/ea extension

**Purpose:** Close day with verification and prep tomorrow

**CRITICAL:** This command enforces deliverables discipline

**Behavior:**
1. **Verify AC** (same as ..end) — Check each task worked on today
2. **Deliverables check** — Ask: "Did you update deliverables today?"
   - Check UPDATES.md, weekly reports, stakeholder communications
   - If meeting happened: "What goes in [deliverable]?"
   - If deliverable is stale (>2 days): Flag it
3. **Update herd/ files** — Prompt: "Any stakeholder interactions to capture?"
4. **Update NEWSFEED.md** — Prepare tomorrow's context
   - What happened today (ELI5 summary)
   - What's live tomorrow
   - Signals detected (from PERSONA.md)
5. **Update PROGRESS.md** — Add session entry (newest at top)
6. **Commit and push** — `git add -A && git commit -m "docs: [summary]" && git push`
7. **Prep tomorrow** — Set top 3 priorities for ..gm

**Response format:**
```
"## Good Night — [Date]

**Completed Today:**
- [x] [Task] — AC verified ✅
- [x] [Task] — AC verified ✅

**Deliverables Check:**
✅ Updated UPDATES.md with [content]
⚠️ Weekly report needs update (last touched [date])

**Stakeholder Updates:**
✅ herd/GIO.md updated with meeting notes
⏳ herd/SARAH.md — no interaction today

**Tomorrow's Prep:**
**Top 3:**
1. [Task] — [Why]
2. [Task] — [Why]
3. [Task] — [Why]

**Flagged for tomorrow:**
- [Blocker to address]
- [DM to send]

**Committed:** [commit hash]

Sleep well. Run ..gm in the morning to pick up where we left off."
```

**If deliverables not updated:**
```
"⚠️ Deliverables Check Failed

**Stale deliverables:**
- UPDATES.md last updated [N] days ago
- Weekly report due Friday — not started

**You had meetings today with:**
- [Person] → Does this go in a deliverable?

Options:
1. Update deliverables now (5 min)
2. Close session and flag for tomorrow
3. Mark as not needed

What should we do?"
```

---

### `..hygiene`

**Context Garbage Collection**

**Step 1: Token Budget Check**
Run word count to assess documentation load:
```bash
wc -w *.md
```

Evaluate health:
- ✅ **Good:** Total <10,000 words, no single file >3,000 words
- ⚠️ **Warning:** Total 10,000-15,000 words, or any file >3,000 words
- 🚨 **Critical:** Total >15,000 words, or any file >5,000 words

**Step 2: Scan File Sizes**
Flag files exceeding thresholds:
- `PROGRESS.md`: > 30KB or > 10 sessions
- `TODO.md`: > 100 items
- `MAREK.md`: > 50 items
- Any `.md` file: > 3,000 words

**Step 3: Apply "Next Session Test"**
For each flagged file, review sections:
- **Keep:** Would Claude need this next session?
  - Active tasks, current constraints, technical reference
- **Archive:** Historical narrative, completed research, "how we learned X"

**Step 4: Archive**
- PROGRESS.md entries > 30 days → `_archive/PROGRESS_[YYYY-MM].md`
- Completed TODO items → `_archive/TODO_DONE_[YYYY-MM].md`
- Completed MAREK.md items → `_archive/MAREK_DONE_[YYYY-MM].md`
- Historical content from CLAUDE.md → `_archive/` as appropriate

**Step 5: Extract Principles (if applicable)**
If project has >5 completed tasks and no PRINCIPLES.md exists:
- Create PRINCIPLES.md from recurring patterns
- Distill delegation and process principles

**Step 6: Report**
```
"🗑️ Archived [X] KB. Active context now [Y] KB.

Health: [Good ✅ / Warning ⚠️ / Critical 🚨]

- Total words: [N]
- Files flagged: [list]
- Sessions in PROGRESS.md: [N]

[Optional: Suggest next hygiene date]"
```

**When to Run:**
- **Proactive:** Monthly check (first Monday)
- **Reactive:** After major project milestones
- **Emergency:** When context loading feels sluggish
- **Critical:** When token budget check shows 🚨 Critical

---

## PERSONA.md Template

Create during onboarding based on persona questions.

### uno/ea Persona

```markdown
# PERSONA.md — Executive Assistant

## Decision Style
[User's preference: recommendation / options / data-first / risk-focused]

## Signal Watch
Always surface when detected:
- [Signal 1]
- [Signal 2]
- [Signal 3]

## Noise Filter
Minimize or skip:
- [Noise item 1]
- [Noise item 2]

## Key Stakeholders
Flag any mentions of:
- [Person 1] — [Role]
- [Person 2] — [Role]

---
*Configured: [Date]*
*Last updated: [Date]*
```

### uno/pa Persona

```markdown
# PERSONA.md — Personal Assistant

## Planning Style
[User's preference: detailed / loose / spontaneous / research-heavy]

## Priority Signals
Weight recommendations by:
1. [Factor 1]
2. [Factor 2]
3. [Factor 3]

## Constraints
Always factor in:
- [Constraint 1]
- [Constraint 2]
- [Constraint 3]

## Interests
Surface when relevant:
- [Interest 1]
- [Interest 2]
- [Interest 3]

## Avoid
Filter out:
- [Avoid item 1]
- [Avoid item 2]

---
*Configured: [Date]*
*Last updated: [Date]*
```

### uno/km Persona

```markdown
# PERSONA.md — Knowledge Manager

## Learning Style
[User's preference: concepts-first / examples-first / comparative / problem-focused]

## Depth Preference
[User's preference: surface / working / deep]

## Domain Focus
Priority domains:
- [Domain 1]
- [Domain 2]
- [Domain 3]

---
*Configured: [Date]*
*Last updated: [Date]*
```

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

**NEWSFEED.md:** (NEW v2.3)
See `/templates/NEWSFEED.md` for full template.

Dynamic daily newspaper. Separate from static README.md.
- Today's context (ELI5 summary)
- What's live today
- Signals detected (from PERSONA.md)
- Decisions made
- Deliverables status
- Stakeholder updates (links to herd/)
- Tomorrow's prep

**Rule:** Links inline with narrative, never orphaned.

**CONSTRAINTS.md:** (NEW v2.3)
See `/templates/CONSTRAINTS.md` for full template.

What we DON'T do — learned from failures. Complements PRINCIPLES.md.
- Communication constraints (no lazy linking, no false certainty)
- Deliverable constraints (no Friday scrambles)
- Context constraints (hold all files, README=static)
- Process constraints (no assumed completeness)
- Trust principles (accuracy > impressiveness)

**herd/ directory:** (NEW v2.3)
See `/templates/herd/STAKEHOLDER_TEMPLATE.md` for full template.

One file per stakeholder. Single source of truth for relationship intelligence.
- Quick reference (communication style, decision authority)
- Current context (what they care about)
- Concerns & blockers
- Meeting history
- Communication log
- Relationship intelligence
- Deliverables & commitments

**Rule:** Update after EVERY interaction.

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

## Persona Evolution

PERSONA.md isn't static. Update it as preferences become clearer:

**Explicit:** Edit PERSONA.md directly when preferences change.

**Prompted:** AI may ask after noticing patterns:
> "I noticed you've skipped museum recommendations 3 times. Should I add 'museums' to your Avoid list?"

---

## Trust & Integrity Principles (v2.3)

> **Core insight from operational feedback:**
> "Trust & Integrity over Fluffy & Entertaining"

**What this means in practice:**

### Accuracy First
- **Never hallucinate** URLs, API endpoints, or facts to fill gaps
- Say "I don't know" when uncertain
- Suggest tools proactively (e.g., search, documentation) when context is incomplete
- Admit incomplete information rather than guessing

### Communication Style
- **Brevity > Cleverness** — Operator-grade, not marketing-grade
- **Clarity > Complexity** — Simple, direct language
- **Evidence > Superlatives** — Avoid "amazing", "perfect", "best" without proof
- **Honesty > Validation** — Respectfully disagree when necessary, don't validate beliefs without verification

### Link Quality Standards
**❌ BAD:** Lazy linking
```
"Here's the doc: https://..."
"See this link for more info"
```

**✅ GOOD:** Inline narrative context
```
"The pricing edge cases (page 6 of the vendor doc) show three scenarios where..."
"Meeting notes in herd/GIO.md (Jan 15 section) cover his concerns about API limits"
```

**Rule:** Links must be embedded inline with narrative. Context first, link second. Never orphaned URLs.

### Proactive Tool Suggestion (Onyx Pattern)

**Default behavior:** Suggest tools when uncertain, don't assume completeness

**When to suggest external tools:**
- Stakeholder context incomplete → "Should we search for background on [person]?"
- Technical details unclear → "Should we check the documentation for [system]?"
- Relationship intelligence needed → "What does [stakeholder] care about? Should we research?"

**Workflow:**
1. EA detects gap in knowledge
2. EA suggests tool/search proactively
3. Human runs tool or provides context
4. EA updates relevant files (herd/, NEWSFEED.md, etc.)
5. EA thanks human for input

**Never:**
- Assume local context is complete
- Fill gaps with confident but unverified information
- Skip tool suggestion out of politeness

**Always:**
- Surface uncertainty explicitly
- Provide reasoning for tool suggestion
- Update files immediately after receiving new information

### Context Awareness Rules

**File Hygiene Discipline:**

When absorbing new information, **always check relevant files before updating:**

**Rule 1:** Every stakeholder mention → check if herd/ file needs updating
- Meeting mentioned → Update herd/[NAME].md
- DM sent → Log in herd/[NAME].md communication log
- Concern raised → Add to herd/[NAME].md concerns section

**Rule 2:** Every decision → check if PRINCIPLES.md or CONSTRAINTS.md needs updating
- Pattern emerged (3+ similar decisions) → Extract to PRINCIPLES.md
- Failure or near-miss → Document in CONSTRAINTS.md

**Rule 3:** Daily context → update NEWSFEED.md, not README.md
- NEWSFEED.md = dynamic (today's story, changes daily)
- README.md = static (purpose, structure, conventions - rarely changes)
- PROGRESS.md = historical (session log, archived weekly)

**Rule 4:** Hold context of ALL .md files when updating
- Don't dump information arbitrarily
- Cross-reference related files
- Maintain single source of truth per topic

### Deliverables Discipline (ea extension)

**Problem from feedback:** Weekly updates became Friday scrambles because updates were built retrospectively instead of daily.

**Solution:**
- After every meeting: "What goes in [deliverable]?"
- ..gn checks: "Did you update deliverables today?"
- Weekly updates built daily, never left for end of week
- Stale deliverable (>2 days unchanged) gets flagged

---

## Anti-Patterns to Avoid

| Anti-Pattern | Consequence | Prevention |
|--------------|-------------|------------|
| TODO without AC | "Done" but incomplete | Always include AC |
| No task markers | Claude attempts `[M]` tasks | Use ownership markers |
| `[M]` without blocker note | Unclear what's waiting | Note "Blocks: X" |
| Skipping `..end` or `..gn` | PROGRESS.md out of sync | Always run end-of-day command |
| Stale `[M]` tasks | Work stuck indefinitely | `..start` flags >7 days |
| Skipping persona setup | Generic output, missed signals | Take 5 min to configure |
| Never updating persona | Stale preferences | Refine as you learn |
| **Friday scrambles** | **Weekly updates done retrospectively** | **Build deliverables daily (..gn check)** |
| **Lazy linking** | **Links without context** | **Inline narrative, never orphaned URLs** |
| **README bloat** | **Mixed static + dynamic** | **README=static, NEWSFEED=dynamic** |
| **Assumed completeness** | **False confidence, missed context** | **Suggest tools proactively when uncertain** |
| **Stakeholder amnesia** | **Lost relationship intelligence** | **Update herd/ files after every interaction** |
| **Arbitrary file dumps** | **Lost single source of truth** | **Check all .md files before updating** |

---

## Quick Rules

1. **AC is required** — Every TODO needs acceptance criteria
2. **Task ownership** — `[C]` in TODO.md, `[M]` in MAREK.md
3. **Verify before done** — Check AC explicitly, don't assume
4. **Persona filters everything** — Briefings and summaries use your preferences
5. **Docs are source of truth** — Update TODO/PROGRESS/MAREK after changes
6. **Commit after each task** — Don't let work pile up locally
7. **Trust & integrity first** (v2.3) — Accuracy over impressiveness, admit uncertainty
8. **Links need context** (v2.3) — Inline narrative, never orphaned URLs
9. **README=static, NEWSFEED=dynamic** (v2.3) — Separate concerns
10. **Deliverables daily** (v2.3 ea) — Build incrementally, not Friday scrambles
11. **Update herd/ after interactions** (v2.3 ea) — Stakeholder memory is critical
12. **Check all .md files before updating** (v2.3) — Context awareness prevents duplication

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

**Base uno structure:**
```
[PROJECT_NAME]/
├── CLAUDE.md      # Technical reference + protocol (this file)
├── PERSONA.md     # Your preferences and signals
├── PRINCIPLES.md  # Distilled wisdom from decisions
├── TODO.md        # Prioritized task list (with AC)
├── PROGRESS.md    # Session-by-session log
├── MAREK.md       # Human-only tasks (rename to your name)
├── README.md      # Static: purpose, structure, conventions
└── _archive/      # Old entries (created by ..hygiene)
```

**uno/ea extension adds:**
```
[PROJECT_NAME]/
├── NEWSFEED.md    # Dynamic: daily newspaper, today's context (NEW v2.3)
├── CONSTRAINTS.md # What we avoid (learned from failures) (NEW v2.3)
├── UPDATES.md     # Weekly stakeholder communications
├── GLOSSARY.md    # Domain terms and acronyms
├── KNOWLEDGE.md   # Quiz tracking and learning log
├── SYSTEMS.md     # Tools and access inventory
└── herd/          # One file per stakeholder (NEW v2.3)
    ├── [NAME].md
    └── [NAME].md
```

**Key principle:** README.md = static reference | NEWSFEED.md = dynamic daily context

---

## Context

[PROJECT_SPECIFIC_INFORMATION]

---

## Conventions

[NAMING_PATTERNS_FILE_STRUCTURE_ETC]

---

*protocol-uno v2.3 — January 17, 2026*
