# [Project Name] Boilerplate

<!-- META: Keep this file under 80 lines. Add details to linked files, not here. -->
<!-- If this file grows past 80 lines, refactor content to @ references. -->

## Quick Reference
- Stack: [Define your tech stack here]
- Commands: `pnpm dev`, `pnpm test`, `pnpm build`
- Branch: Check with `git branch --show-current`

## Critical Rules
1. **Research first** — Web search before recommending when currency matters
2. **No secrets in code** — Environment variables only
3. **Explicit types** — No `any` without justification
4. **Tests required** — Write tests before committing
5. **Guardian gates** — Zero issues required for merge (override with approval)

## Mode
Apprentice mode active:
- Explain "why" not just "what"
- Use analogies for new concepts
- Define jargon on first use
- Share relevant industry context

For extra-detailed teaching: invoke `apprentice-mode` skill.

## Context (load when relevant)
- Current state: @.ai/context/current-world-state.md
- Project context: @.ai/SHARED-CONTEXT.md
- Architecture: @docs/architecture.md

## Guardians
9 specialized agents configured in @.claude/settings.json:
- security, typescript, architecture, test, performance
- docs, accessibility, api, database

Triggers: pre-commit, PR creation, manual `/review`

Invoke via `guardian-agents` skill or `/review` command.

## External Review
- Primary: Codex (task files in .ai/tasks/review/)
- Secondary: Gemini (optional)

## Self-Annealing
- Feedback: Log observations to .ai/feedback/
- Weekly review: Aggregates feedback, proposes improvements
- All changes require human approval — never auto-apply

## Key Skills
- `session-management` — Greet on start, handoff on end
- `guardian-agents` — Parallel review orchestration
- `feature-completion` — Feature branch workflow
- `full-codebase-review` — Develop → main review
- `weekly-annealing` — Self-improvement cycle
- `boilerplate-sync` — Sync improvements across instances
- `boilerplate-migrate` — Add boilerplate to existing projects
- `boilerplate-customize` — Adjust boilerplate for your needs
- `skill-audit` — Check skill health, updates, TDD status

## Commands
- `/review` — Manual guardian sweep
- `/complete-feature` — Feature completion checklist
- `/feedback` — Quick feedback capture
- `/customize` — Adjust boilerplate settings
- `/migrate` — Add boilerplate to existing project
- `/audit skills` — Check skill ecosystem health

## See Also
- Design doc: @docs/plans/2025-12-03-claude-code-boilerplate-design.md
- Settings: @.claude/settings.json
