# MAREK.md - Human Tasks

**Purpose:** Tasks only humans can do (recording, content creation, external decisions)  
**Last Updated:** [DATE]

---

## ⏸️ Blocked (needs Marek action)

Tasks that only Marek can complete. Note what they block.

```
- [ ] [M] Task description
  - AC: Acceptance criteria
  - Blocks: [what's waiting on this]
```

<!-- Example:
- [ ] [M] Record explainer video
  - AC: 2-min video uploaded
  - AC: URL provided below
  - Blocks: Documentation landing page
-->

---

## ✅ Ready for Marek (Claude prepared)

Claude completed the prep work. Marek reviews and executes.

```
- [ ] [C→M] Task description
  - Deliverable: /path/to/file.md
  - Action needed: [what Marek does with it]
```

<!-- Example:
- [ ] [C→M] Blog post draft
  - Deliverable: /drafts/blog-post.md
  - Action needed: Review, edit, publish
-->

---

## ❓ Waiting on Marek Decision

Claude needs a decision before proceeding.

```
- [ ] [M→C] Decision question?
  - Options: A, B, C
  - Context: [why this matters]
  - Unblocks: [what Claude will do after]
```

<!-- Example:
- [ ] [M→C] Which audience to target?
  - Options: Developers, Product Managers, Both
  - Context: Affects tone and examples used
  - Unblocks: Claude writes intro section
-->

---

## ✅ Completed

Mark tasks complete with output and date.

```
- [x] [M] Task — Date
  - Output: [URL, decision, file path]
  - Unblocks: [what's now ready for Claude]
```

<!-- Example:
- [x] [M] Record demo — Dec 28, 2025
  - Output: https://youtube.com/watch?v=abc123
  - Unblocks: Embed in landing page
-->

---

## Quick Reference

| Task | Type | Blocks | Priority |
|------|------|--------|----------|
| [Task] | [M]/[C→M]/[M→C] | [What] | HIGH/MED/LOW |

---

## Not In This File

These stay in TODO.md (Claude can do them):
- `[C]` Documentation writing
- `[C]` Research compilation
- `[C]` File organization

---

**Workflow:**
1. Claude adds `[M]` tasks here during onboarding or when blocked
2. Claude moves `[C→M]` tasks here after completing prep work
3. Marek completes tasks and adds output
4. Claude picks up completed tasks on next `..start`

---

*Rename this file to match your name (e.g., SARAH.md, TEAM.md)*
