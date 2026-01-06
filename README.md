# uno — Delegate Protocol

A template for AI-assisted delegation — AI works FOR you.

Part of the [KayGee Protocol Family](https://github.com/marekgorski/admin/tree/main/protocol).

---

## The Protocol Family

```
uno (Delegate)          duo (Collaborate)       tre (Automate)
AI works FOR you        AI works WITH you       AI works AMONG systems
├── /ea (Executive)     └── /ab (Arch+Build)    ├── /qa (Quality)
├── /pa (Personal)                              ├── /rm (Risk)
└── /km (Knowledge)                             └── /cs (Customer)
```

**uno** is for clear delegation: you define WHAT, AI handles HOW.

Use **duo** ([protocol-duo](https://github.com/marekgorski/protocol-duo)) for code projects needing architect/builder separation.

---

## Extensions

uno comes with domain-specific extensions that customize behavior:

| Extension | Mode | Use Case | Creates |
|-----------|------|----------|---------|
| **ea** | Executive Assistant | Onboarding, projects with deadlines, stakeholder management | UPDATES.md, GLOSSARY.md, KNOWLEDGE.md, SYSTEMS.md |
| **pa** | Personal Assistant | Trip planning, events, moves, personal finance | ITINERARY.md, BOOKINGS.md, BUDGET.md, NOTES.md |
| **km** | Knowledge Manager | Documentation, archives, reference material | LOG.md, PLANNED.md |
| **none** | Base uno | Simple delegation without domain tracking | (core files only) |

Extension is selected during onboarding — Claude will ask which fits your project.

---

## Quick Start

### 1. Use this template

**GitHub Template:** Click "Use this template" on GitHub to create a new repo.

Or clone directly:

```bash
git clone https://github.com/marekgorski/protocol-uno.git my-project
cd my-project
rm -rf .git && git init
```

### 2. Open in Claude

Claude will see the `[PLACEHOLDER]` markers and run the onboarding flow:

1. **Extension selection** — ea, pa, km, or none
2. **Discovery questions** — What, who, problem, success, constraints
3. **File creation** — Extension-specific files generated
4. **Ready to work**

### 3. Use session commands

| Command | Purpose |
|---------|---------|
| `..start` | Daily briefing (extension-aware), priorities, blockers |
| `..end` | Verify AC met, update docs, commit |
| `..hygiene` | Archive old entries |

---

## Core Files

All uno projects have:

```
my-project/
├── CLAUDE.md      # Protocol + project reference
├── TODO.md        # Tasks with acceptance criteria
├── PROGRESS.md    # Session log
├── MAREK.md       # Human-only tasks
├── README.md      # Project description
└── _archive/      # Old entries
```

Extensions add domain-specific files (see above).

---

## Task Ownership

| Marker | Meaning | Lives In |
|--------|---------|----------|
| `[C]` | Claude can complete | TODO.md |
| `[M]` | Human must complete | MAREK.md |
| `[C→M]` | Claude prepares, human executes | TODO.md → MAREK.md |
| `[M→C]` | Human decides, Claude implements | MAREK.md → TODO.md |

**No marker = `[C]`**

---

## Philosophy

### Why Files Work

AI forgets everything between conversations. Start a new chat, and it's meeting you for the first time.

But files don't forget.

When you write what you learned in a file, AI reads it next session. When you track what's done, AI knows where you left off. When you log what needs a human, AI doesn't spin on work it can't complete.

**Your markdown files ARE the AI's memory:**

| File | What It Remembers |
|------|-------------------|
| TODO.md | What needs doing (with clear "done" criteria) |
| PROGRESS.md | What happened (so the next session knows) |
| MAREK.md | What only you can do (so AI doesn't waste time) |

Three files. That's all you need for persistent delegation.

---

## Key Rules

1. **AC is required** — Every TODO needs acceptance criteria
2. **Task ownership** — Use markers, don't let Claude spin on human tasks
3. **Verify before done** — `..end` checks AC explicitly
4. **Commit after each task** — Don't let work pile up

---

## Extension Behaviors

### uno/ea — Executive Assistant

`..start` produces a daily briefing:
- Status calculation (Day N/90, T-N countdown)
- Pace check (meetings/day, deliverables vs targets)
- Risk surface (what might slip?)
- Knowledge quiz (from GLOSSARY.md)
- Today's #1 priority

### uno/pa — Personal Assistant

`..start` produces a trip briefing:
- Timeline check (next 7 days)
- Booking deadlines (expiring, needs confirmation)
- Budget status (spent vs planned)
- Conditions check (weather, advisories)
- Today's logistics priority

### uno/km — Knowledge Manager

`..start` checks:
- Pending items in LOG.md
- Recurring tasks due in PLANNED.md
- Stale documentation (30+ days)
- Today's documentation priority

---

## Implementations

| Project | Extension | Description |
|---------|-----------|-------------|
| [uno-ea](https://github.com/marekgorski/uno-ea) | ea | 90-day onboarding tracker |
| [australia-trip](https://github.com/marekgorski/australia-trip) | pa | Family trip planning Feb-Mar 2026 |
| [admin](https://github.com/marekgorski/admin) | km | KayGee operations |

---

## Changelog

- **v2.0** (Jan 2, 2026): uno/pa validated with australia-trip implementation, refined NOTES.md template with research tables
- **v2.0** (Jan 1, 2026): Rebranded to uno, added extension system (ea, pa, km), extension-aware `..start`
- **v1.2** (Dec 28, 2025): Task ownership markers, handoff system
- **v1.1** (Dec 28, 2025): Acceptance criteria, verification
- **v1.0** (Dec 2024): Initial release

---

## License

MIT — Use freely, modify as needed.

---

*protocol-uno v2.0 — January 2, 2026*
