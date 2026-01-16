# Principles

> **Purpose:** Distilled wisdom from all decisions + implementation experience. Read in <2 minutes.
>
> **When to create:** After project onboarding, extract core principles from initial decisions.
>
> **When to update:** After major milestones or when pattern emerges across 3+ decisions.

---

## Mission

[Extract from project context — What is this delegation's core purpose?]

---

## Delegation Principles

**DP1: [Principle Name]**
[Brief description of how this guides task delegation]

**DP2: [Principle Name]**
[Brief description of how this guides task delegation]

**DP3: [Principle Name]**
[Brief description of how this guides task delegation]

<!-- Example from australia-trip (uno/pa):
**DP1: Proactive Research** — Surface options before being asked
**DP2: Constraint-Aware** — Remember dietary, budget, and preference constraints
**DP3: Decision-Ready** — Present comparison tables, not raw data
-->

---

## Process Principles

**PP1: [Principle Name]**
[Brief description of how work flows]

**PP2: [Principle Name]**
[Brief description of how work flows]

<!-- Example:
**PP1: Files ARE Memory** — Docs persist, conversations don't
**PP2: Verifiable Done** — AC must be testable, not assumed
-->

---

## The "Next Session Test"

**For every section in a context file, ask:**
> "Would Claude need this to start fresh next session?"

- ✅ **Keep:** Active tasks, current constraints, technical reference
- ❌ **Archive:** Historical narrative, completed research, "how we learned X"

---

## Token Budget Awareness

**Target:**
- **uno Mode:** ~5,000 tokens (10% of session budget)
  - Loads: CLAUDE, PERSONA, TODO, PROGRESS, MAREK

**Check monthly:**
```bash
wc -w *.md
```

**Thresholds:**
- ✅ **Good:** Total <10,000 words, no single file >3,000 words
- ⚠️ **Warning:** Total 10,000-15,000 words, or any file >3,000 words
- 🚨 **Critical:** Total >15,000 words, or any file >5,000 words

**When critical:** Run `..hygiene` to archive old content.

---

## Related Files

| File | Purpose | Relationship to PRINCIPLES.md |
|------|---------|------------------------------|
| **PERSONA.md** | User preferences, signals | Source of Delegation Principles |
| **TODO.md** | Task list with AC | Source of process patterns |
| **CLAUDE.md** | Technical reference | Source of Process Principles |

---

*This file is extracted from active decisions after patterns emerge. It replaces the need to read all historical context.*

*Template from uno Protocol v2.2*
