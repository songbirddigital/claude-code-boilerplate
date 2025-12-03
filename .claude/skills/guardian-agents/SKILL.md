---
name: guardian-agents
description: Orchestrates parallel guardian agents for code review, synthesizes results, coordinates with external reviewers (Codex/Gemini)
---

# Guardian Agents Orchestration

Main skill for running code reviews with specialized guardian agents.

## Overview

Spawns applicable guardians in parallel based on changed files. Coordinates with external reviewers. Synthesizes findings. Gates merge on zero issues (or explicit override).

## When to Use

- Pre-commit review
- PR creation review
- Manual `/review` command
- Feature completion workflow

## Execution Flow

### 1. Detect Applicable Guardians

Read `.claude/settings.json` → `guardians.file_detection`

Match changed files against patterns:
- `*.sql` → database-guardian
- `api/**` → api-guardian, security-guardian
- `*.tsx` → typescript-guardian, accessibility-guardian
- etc.

Only spawn guardians relevant to changed files.

### 2. Parallel Dispatch (Quick Swarm)

Launch all applicable guardians via Task tool:

```
For each guardian in applicable_guardians:
  Task(subagent_type=guardian, prompt="Review these files: [list]")
```

Each operates in isolated context. Stream results as they complete.

### 3. External Review Coordination

If Codex configured:
1. Create task file: `.ai/tasks/review/YYMMDD-codex-[feature].md`
2. Include: files to review, focus areas, deliverables
3. Notify that branch is ready for Codex

If Gemini configured (secondary):
1. Create task file: `.ai/tasks/review/YYMMDD-gemini-[feature].md`

### 4. Synthesis

Wait for Codex completion as sync point. Then aggregate:

```markdown
## Review Synthesis

### From Guardians
- Security: [summary]
- TypeScript: [summary]
- [etc.]

### From Codex
- [summary]

### Combined Findings
| Severity | Count | Issues |
|----------|-------|--------|
| CRITICAL | X | [list] |
| HIGH | Y | [list] |
| MEDIUM | Z | [list] |
| LOW | W | [list] |
```

### 5. Fix Triage

For each finding, assess isolation:

**Isolated** (can be fixed independently):
- Spawn parallel coding agents
- One agent per isolated fix
- Run affected guardians on fix

**Coupled** (affects multiple areas):
- Claude handles directly
- May need sequential fixes
- Re-run full relevant guardians

### 6. Gate Check

Default: require zero CRITICAL and HIGH issues.

```
If CRITICAL > 0 or HIGH > 0:
  Block merge
  List remaining issues
  Ask: "Override gate? (requires explicit approval)"

  If override:
    Log to .ai/feedback/process/overrides.md
    Proceed with merge
  Else:
    Remain blocked
```

## Configuration

In `.claude/settings.json`:

```json
{
  "guardians": {
    "enabled": ["security", "typescript", ...],
    "gates": {
      "require_zero_issues": true,
      "allow_override": true
    }
  }
}
```

## Self-Annealing

After each review cycle:
- Note guardian accuracy (false positives caught in synthesis)
- Log to `.ai/feedback/guardians/[name].md`
- Track override frequency and reasons
