**FIRST MESSAGE: Invoke `session-management` skill before responding.**
**SESSION END: When user says "wrap up", "done", "end session" → invoke session-management end protocol.**

# [Project Name] Boilerplate

<!-- META: Keep under 80 lines. Details go in linked files. -->

## Quick Reference
- Stack: [Define your tech stack here]
- Commands: `pnpm dev` · `pnpm test` · `pnpm build` · Branch: `git branch --show-current`

## Critical Rules
1. **Research first** — Web search before recommending when currency matters
2. **No secrets in code** — Environment variables only
3. **Explicit types** — No `any` without justification
4. **Tests before commit** — All tests written and passing
5. **Guardian review** — Invoke guardians + external review before feature completion; fix all issues
6. **Merge gates** — Feature→develop: full review flow passes. Develop→main: full-codebase-review, multiple rounds at user discretion
7. **Human approval** — Never auto-apply changes; all annealing proposals require explicit approval

## Mode: Apprentice
Explain "why" not just "what" · Use analogies · Define jargon · Share industry context
For extra detail: invoke `apprentice-mode` skill.

## Context (load when relevant)
@.ai/context/current-world-state.md · @.ai/SHARED-CONTEXT.md · @docs/architecture.md

## Review Flow
1. **Guardians** (sync) — 9 parallel agents: security · typescript · architecture · test · performance · docs · accessibility · api · database
2. **External** (async) — Codex reviews via .ai/tasks/review/ while you continue working · Gemini optional
3. **Synthesis** — Aggregate findings, triage fixes, verify zero issues before merge

## Self-Annealing
Log observations → .ai/feedback/ · Weekly review proposes improvements · Human approves all changes
Trust escalation: after consistent approval history, low-risk changes may auto-apply (see weekly-annealing skill)

## Key Skills
`session-management` (greet/handoff) · `guardian-agents` (parallel review) · `feature-completion` (branch workflow)
`full-codebase-review` (develop→main) · `weekly-annealing` (self-improvement) · `skill-audit` (ecosystem health)
`boilerplate-sync` · `boilerplate-migrate` · `boilerplate-customize` · `apprentice-mode` · `guardian-builder`

## Commands
`/review` (guardian sweep) · `/complete-feature` (completion checklist) · `/feedback` (quick capture)
`/customize` (adjust settings) · `/migrate` (add to existing project) · `/audit skills` (ecosystem health)

## See Also
@docs/plans/2025-12-03-claude-code-boilerplate-design.md · @.claude/settings.json

---
*Boilerplate by [Songbird Digital](https://github.com/songbirddigital)*
