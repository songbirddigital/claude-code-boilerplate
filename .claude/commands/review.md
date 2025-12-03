---
description: Trigger manual guardian review on current changes or specified files
---

# Manual Guardian Review

Run a guardian sweep on demand.

## Usage

```
/review                    # Review uncommitted changes
/review src/api/           # Review specific directory
/review --full             # Full codebase review
```

## Process

1. Determine scope (changes, path, or full)
2. Detect applicable guardians based on files
3. Invoke `guardian-agents` skill
4. Report findings

## Quick Review (Default)

Reviews uncommitted changes:
- `git diff --name-only` for staged
- `git diff --name-only HEAD` for all changes

## Path Review

Reviews all files in specified path:
- Recursively processes directory
- Applies file detection rules

## Full Review

Invokes `full-codebase-review` skill:
- All guardians on all files
- Extended checks (coverage, deps, architecture)
- Generates health report

## Output

Findings reported in standard format:
```
## Review Results

### CRITICAL (X)
...

### HIGH (Y)
...

### Action Required
[What needs to be fixed before proceeding]
```
