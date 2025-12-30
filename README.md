# Light Protocol

A lightweight project template for AI-assisted documentation and knowledge work.

## What is this?

Light Protocol is a simplified version of Layer3 Protocol, designed for **doc-heavy projects** that don't need the full architect/builder role separation.

Use this for:
- Personal knowledge bases
- Documentation projects
- Reference guides
- Process documentation

Use [Layer3 Protocol](https://github.com/marekgorski/layer3-protocol) instead for:
- Code projects with complex architecture
- Multi-contributor projects needing handoff
- Projects requiring design/implementation separation

## Quick Start

### 1. Clone this template

```bash
git clone https://github.com/marekgorski/light-protocol.git my-project
cd my-project
rm -rf .git && git init
```
#### or via SSH substitute for
```git clone git@github.com:marekgorski/light-protocol.git my-project```

### 2. Open in Claude Code

Claude will see the `[PLACEHOLDER]` markers and run the onboarding flow.

### 3. Answer discovery questions

Claude will ask about the project, users, problem, success criteria, and constraints.

### 4. Start working

Use the session commands:
- `..start` — Begin session, check for completed human tasks, see priorities
- `..end` — Verify, close session, update docs

## Task Ownership

Tasks use markers to indicate who can complete them:

| Marker | Meaning | Example |
|--------|---------|---------|
| `[C]` | Claude can complete | `[C] Write intro section` |
| `[M]` | Human must complete | `[M] Record demo video` |
| `[C→M]` | Claude prepares, human executes | `[C→M] Draft email template` |
| `[M→C]` | Human decides, Claude implements | `[M→C] Choose audience` |

**No marker = `[C]`** — Tasks without markers are assumed Claude-completable.

`[C]` tasks live in **TODO.md**. `[M]` tasks live in **MAREK.md**.

## Commands

| Command | Purpose |
|---------|---------|
| `..start` | Load context, check MAREK.md, show top `[C]` priority |
| `..end` | **Verify AC met**, update TODO/PROGRESS/MAREK, commit |
| `..hygiene` | Archive old entries when files grow large |

## File Structure

```
my-project/
├── CLAUDE.md      # Technical reference + protocol
├── TODO.md        # Prioritized task list (with AC)
├── PROGRESS.md    # Session-by-session log
├── MAREK.md       # Human-only tasks (rename to your name)
├── README.md      # This file (replace with your own)
└── _archive/      # Old entries (created by ..hygiene)
```

## Key Rules (v1.2)

### Acceptance Criteria Required

Every TODO item needs testable conditions:

```markdown
BAD:  - [ ] Write intro section
GOOD: - [ ] [C] Write intro section
        - AC: Explains problem in <100 words
        - AC: Includes one concrete example
```

### Task Ownership Markers

Use markers to prevent Claude from spinning on tasks it can't complete:

```markdown
TODO.md (Claude tasks):
- [ ] [C] Write documentation
  - AC: Covers all features

MAREK.md (Human tasks):
- [ ] [M] Record video → blocks landing page
- [ ] [M→C] Choose target audience → unblocks intro section
```

### Verify Before Marking Done

`..end` requires confirmation that acceptance criteria are met:
1. Check each AC explicitly
2. If not met: Note what's missing, do NOT mark complete
3. If met: Mark `[x]` and update PROGRESS.md

## Anti-Patterns to Avoid

| Anti-Pattern | Consequence | Prevention |
|--------------|-------------|------------|
| TODO without AC | "Done" but incomplete | Always include AC |
| No task markers | Claude attempts `[M]` tasks | Use ownership markers |
| `[M]` without blocker note | Unclear what's waiting | Note "Blocks: X" |
| Skipping `..end` | PROGRESS.md out of sync | Always run `..end` |
| Stale `[M]` tasks | Work stuck | `..start` flags >7 days |

## Philosophy

### Why fewer files than Layer3?

- **No PRFAQ/DECISIONS** — Doc projects don't need extensive architecture records
- **No role separation** — You're both planner and executor
- **Leaner context** — Less to read, faster to start

### Why session commands?

- **`..start`** ensures you know what's priority and checks for completed human tasks
- **`..end`** ensures progress is verified and captured before closing
- **Context fossilization** — Markdown files survive across sessions

## Changelog

- **v1.2** (Dec 28, 2025): Added task ownership markers, human/AI handoff system, MAREK.md structure
- **v1.1** (Dec 28, 2025): Added acceptance criteria requirements, verification steps, anti-patterns
- **v1.0** (Dec 2024): Initial release

## License

MIT — Use freely, modify as needed.

---

*Light Protocol v1.2 — December 28, 2025*
