# PROGRESS

Session-by-session log for [PROJECT_NAME]. Newest entries at top.

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
