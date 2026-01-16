# PROGRESS

Session-by-session log for [PROJECT_NAME]. Newest entries at top.

---

## Session: 2026-01-17 — Protocol v2.3: Operational Refinements

### What Was Accomplished

**Architected and implemented v2.3 based on 10-day real-world feedback from fintech EA usage:**

**New commands added:**
1. `..gm` (Good Morning) — Morning briefing with priorities, risks, DMs to send
2. `..gn` (Good Night) — Enhanced close with deliverables check, NEWSFEED prep, commit

**New file templates created:**
1. `NEWSFEED.md` — Dynamic daily newspaper (separates from static README)
2. `CONSTRAINTS.md` — What we avoid (learned from failures)
3. `herd/STAKEHOLDER_TEMPLATE.md` — One file per stakeholder for relationship intelligence

**Core principles documented:**
1. Trust & Integrity over Fluffy & Entertaining
2. Proactive tool suggestion (Onyx pattern) — admit uncertainty, suggest searches
3. Link quality standards — inline narrative context required
4. Deliverables discipline — build daily, not Friday scrambles
5. Context awareness rules — check all .md files before updating

**Updates to existing files:**
1. `CLAUDE.md` — Added v2.3 commands, Trust & Integrity section, context awareness rules
2. `README.md` — Added v2.3 features, updated changelog
3. `PRINCIPLES.md` — Added operational learnings from feedback
4. `V2.3_RELEASE_NOTES.md` — Comprehensive changelog and migration guide

**New anti-patterns documented:**
- Friday scrambles (deliverables done retrospectively)
- Lazy linking (links without context)
- README bloat (mixed static + dynamic)
- Assumed completeness (false confidence)
- Stakeholder amnesia (lost relationship intelligence)
- Arbitrary file dumps (lost single source of truth)

### Files Created
- `V2.3_RELEASE_NOTES.md` — Complete changelog and migration guide
- `templates/NEWSFEED.md` — Daily newspaper template
- `templates/CONSTRAINTS.md` — Failure pattern tracking template
- `templates/herd/STAKEHOLDER_TEMPLATE.md` — Stakeholder file template

### Files Updated
- `CLAUDE.md` — v2.3 commands, principles, file structure, anti-patterns
- `README.md` — v2.3 features, changelog
- `PRINCIPLES.md` — Delegation and process principles with v2.3 learnings
- `PROGRESS.md` — This entry

### Verified
- All templates follow operational feedback patterns
- Commands (..gm, ..gn) enforce deliverables discipline
- Link quality standards documented with examples
- Context awareness rules prevent file duplication
- Trust & integrity principles guide all communication

### Key Insights from Feedback

**Validated patterns (keep & strengthen):**
- Herd files (one file per stakeholder) scales to 40+ people
- Immediate post-meeting updates prevent detail loss
- DM drafts in files reduce cognitive load
- Daily commits maintain trust

**Failed patterns (fixed in v2.3):**
- Weekly deliverables → Friday scrambles (now: daily building via ..gn)
- README bloat → mixed static/dynamic (now: NEWSFEED.md separation)
- Lazy linking → lost context (now: inline narrative required)
- Assumed completeness → false confidence (now: proactive tool suggestions)

### Next Session

**TOP PRIORITY:** Test v2.3 patterns in a new uno/ea project to validate implementation

---

## Session: 2025-12-28 — Task Ownership Handoff System (v1.2)

### What Was Accomplished

**Upgraded Light Protocol to v1.2 with handoff system:**

1. Added task ownership markers (`[C]`, `[M]`, `[C→M]`, `[M→C]`)
2. Updated MAREK.md with status sections:
   - ⏸️ Blocked (needs Marek action)
   - ✅ Ready for Marek (Claude prepared)
   - ❓ Waiting on Marek Decision
   - ✅ Completed
3. Updated `..start` to check MAREK.md for completed human tasks
4. Updated `..end` to handle `[C→M]` handoff
5. Added handoff protocol documentation
6. Updated anti-patterns with ownership markers

### Files Updated

- `CLAUDE.md` — v1.1 → v1.2, task ownership, handoff protocol
- `MAREK.md` — Restructured with status sections
- `README.md` — v1.1 → v1.2, task ownership section
- `PROGRESS.md` — This entry

---

## Session: 2025-12-28 — MAREK.md Template Added

### What Was Accomplished

**Added MAREK.md template for human-only tasks:**

1. Created MAREK.md with sections for:
   - Recording tasks (videos, audio)
   - Content tasks (case studies, testimonials)
   - Decision tasks (requiring external input)
2. Updated CLAUDE.md file structure to include MAREK.md
3. Updated README.md file structure

### Why This Matters

Separates tasks AI can do from tasks humans must do:
- AI doesn't spin on tasks it can't complete
- Blocked items are clearly visible
- Fun touch: rename to your own name (like adding Tom on MySpace)

### Files Updated

- `MAREK.md` — NEW (human-only tasks template)
- `CLAUDE.md` — Added to file structure
- `README.md` — Added to file structure
- `PROGRESS.md` — This entry

---

## Session: 2025-12-28 — Protocol v1.1 Update

### What Was Accomplished

**Updated Light Protocol to v1.1 based on learnings from Layer3/gym projects:**

1. Added acceptance criteria (AC) requirement for all TODO items
2. Added verification step to `..end` command
3. Added anti-patterns section to CLAUDE.md
4. Updated TODO.md with AC format examples
5. Updated README.md with v1.1 rules and changelog

### Key Changes

- `..end` now requires explicit AC verification before marking complete
- TODO format now requires `- AC:` lines for each task
- Anti-patterns table documents common mistakes and prevention

### Files Updated

- `README.md` — Added AC rules, anti-patterns, changelog, bumped to v1.1
- `CLAUDE.md` — Added AC format, verification to `..end`, anti-patterns section
- `TODO.md` — Added AC format reference and examples
- `PROGRESS.md` — This session entry

### Why This Matters

Previous protocol allowed "done" to be assumed without verification. This led to:
- Tasks marked complete that weren't actually done
- Quality issues discovered late
- Documentation out of sync with reality

v1.1 fixes this by making verification explicit.

---

## Template: Session Entry

Copy this for new sessions:

```markdown
## Session: [DATE] — [THEME]

### What Was Accomplished

**[Summary]:**

1. [Item]
2. [Item]

### Files Updated

- `[file]` — [what changed]

### Verified

- [How AC was confirmed for completed tasks]

### Next Session

**TOP PRIORITY:** [NEXT_TASK]
```

---

*Updated at end of each session.*
