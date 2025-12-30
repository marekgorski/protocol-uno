# CLAUDE.md

## First-Time Setup

**Claude:** If you see `[PLACEHOLDER]` markers, this project hasn't been initialized yet. Run the onboarding flow below.

---

### Onboarding Flow

**Step 1: Discovery Questions**

Ask conversationally, one at a time:

1. "What is this project? Give me the one-liner."
2. "Who is it for?"
3. "What problem does it solve?"
4. "What does success look like?"
5. "Any constraints I should know?"

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

Once confirmed, update:
- `CLAUDE.md` — Replace this section with project-specific reference
- `TODO.md` — Create prioritized task list **with acceptance criteria**
- `MAREK.md` — Add any human-only tasks identified
- `PROGRESS.md` — Log this initialization session
- `README.md` — Replace with project description

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

## Light Protocol (v1.2)

This project uses the **Light Protocol** for AI-assisted documentation and knowledge work.

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

1. Read `CLAUDE.md`, `TODO.md`, `MAREK.md`
2. Check MAREK.md "Completed" section for human tasks that unblock work
3. Flag stale `[M]` tasks (>7 days)
4. Report top `[C]` priority task (with acceptance criteria)

**Response format:**
```
"Context loaded.

**Top priority:** [TASK]
- AC: [criterion 1]
- AC: [criterion 2]

**Human tasks:** [any completed or stale items]

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

*Light Protocol v1.2 — December 28, 2025*
