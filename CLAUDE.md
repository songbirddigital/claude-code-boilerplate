# [Project Name] Boilerplate

## Quick Reference
- Stack: [Define your tech stack here]
- Commands: `pnpm dev` · `pnpm test` · `pnpm build`
- Branch: `git branch --show-current`
- Memory: `.claude/memory/features.json`

---

## Session Protocol

**On start:**
1. Check `.claude/memory/features.json`
   - If exists → read it, show current feature/task/blockers, ask what to work on
   - If missing → prompt: "No domain memory found. Describe your project or say 'help me set up'."
2. Read tail of `.claude/memory/progress.log` for recent context
3. Announce status, ask what to work on

**Suggest initialization when:**
- features.json missing
- User describes new project or major feature
- User lists multiple things to build
- User seems uncertain what to work on
- Project has code but no features.json

**On end:**
1. Update features.json with progress
2. Append to progress.log (including handoff context)
3. Commit if appropriate

---

## Proactive Behaviors

**Follow IMPLEMENTER protocol when:**
- Working on any implementation task
- Orient → Plan → Implement → Verify → Update Memory

**Invoke PLANNER when:**
- Feature is in inception phase and needs planning
- User wants to break down a new feature

**Invoke guardians when:**
- Feature enters review phase
- User requests code review
- Before merge to develop/main

---

## Critical Rules
1. **Research first** — Web search before recommending when currency matters
2. **No secrets in code** — Environment variables only
3. **Explicit types** — No `any` without justification
4. **Tests before commit** — All tests written and passing
5. **Memory updates** — Always update features.json and progress.log at session end
6. **Human approval** — Never auto-apply changes; all proposals require explicit approval

---

## Mode: Apprentice
Explain "why" not just "what" · Use analogies · Define jargon · Share industry context
For extra detail: invoke `apprentice-mode` skill.

---

## Domain Memory

| File | Purpose |
|------|---------|
| `.claude/memory/features.json` | Machine-readable backlog with lifecycle |
| `.claude/memory/progress.log` | Append-only session history + handoff |
| `.claude/memory/decisions.md` | Architectural Decision Records |
| `.claude/memory/issues.md` | Problem tracking with resolutions |

---

## Agents

| Agent | Use When |
|-------|----------|
| `@.claude/agents/INITIALIZER.md` | Setting up a new project |
| `@.claude/agents/PLANNER.md` | Planning a new feature |
| `@.claude/agents/IMPLEMENTER.md` | Implementing tasks (default) |
| `@.claude/agents/REVIEWER.md` | Code review before merge |

### Domain Agents (guardians + specialists)
Located at `.claude/agents/domains/[domain]/guardian.md` and `specialist.md`

Domains: security · database · architecture · api · typescript · test · performance · accessibility · docs

---

## Review Flow
1. **Guardians** (parallel) — Domain-specific reviewers invoked by REVIEWER
2. **Codex** (async) — External review via `.ai/tasks/review/` (~15 min)
3. **Synthesis** — REVIEWER aggregates findings, gates merge on zero critical issues

---

## Commands
`/setup` (new project) · `/status` (current state) · `/plan` (feature planning)
`/review` (guardian + codex) · `/complete-feature` (completion checklist)
`/migrate` (add to existing project) · `/feedback` (quick capture)

---

## Self-Annealing
Log observations → `.ai/feedback/` · Weekly review proposes improvements
Memory feedback tracked in `.ai/feedback/memory/`

---

## Context (load when relevant)
@.ai/context/current-world-state.md · @.ai/SHARED-CONTEXT.md · @docs/ARCHITECTURE.md

---

## See Also
@docs/plans/2025-12-09-domain-memory-integration-design.md · @.claude/settings.json

---
*Boilerplate by [Songbird Digital](https://github.com/songbirddigital)*
