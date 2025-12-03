---
name: session-management
description: Start and end session protocols to maintain context and ensure proper handoff
---

# Session Management

Protocols for starting and ending coding sessions to maintain context continuity.

## Overview

Sessions have beginnings and endings. Proper management ensures:
- No context is lost between sessions
- Work is properly committed and documented
- Next session can pick up seamlessly

## Session Start Protocol

When starting a new session:

### 1. Orient to Current State

```
[ ] Check current branch: git branch --show-current
[ ] Check for uncommitted changes: git status
[ ] Review recent commits: git log --oneline -5
```

### 2. Load Context

```
[ ] Read CLAUDE.md (always)
[ ] Check .ai/sessions/ for recent session logs
[ ] Read .ai/SHARED-CONTEXT.md if exists
[ ] Load .ai/context/current-world-state.md
```

### 3. Review Pending Work

```
[ ] Check .ai/tasks/backlog/ for pending items
[ ] Check .ai/tasks/parallel/ for ongoing work
[ ] Review any open PRs or reviews
```

### 4. Confirm Direction

Ask user:
- "What are we working on today?"
- "Any context I should know about?"

### 5. Log Session Start

Append to `.ai/sessions/session.log`:
```
---
Session Start: YYYY-MM-DD HH:MM
Branch: [current-branch]
Focus: [user-stated or inferred focus]
```

## Session End Protocol

When ending a session:

### 1. Commit Work

```
[ ] Stage relevant changes: git add [files]
[ ] Commit with clear message
[ ] Push to remote (if appropriate)
```

### 2. Document Session

Create `.ai/sessions/YYYY-MM-DD-[topic].md`:

```markdown
# Session: [Topic]

**Date:** YYYY-MM-DD
**Duration:** ~X hours
**Branch:** [branch-name]

## Summary
[2-3 sentences on what was accomplished]

## Completed
- [Task 1]
- [Task 2]

## In Progress
- [Task being worked on]
- [State it's in]

## Blocked / Needs Attention
- [Any blockers]
- [Things to investigate]

## Next Steps
1. [Immediate next action]
2. [Following action]

## Files Changed
- [List significant files]

## Notes
[Anything useful for next session]
```

### 3. Update Shared Context

If significant progress:
```
[ ] Update .ai/SHARED-CONTEXT.md
[ ] Update .ai/context/current-world-state.md if needed
[ ] Move completed tasks to .ai/tasks/completed/
```

### 4. Log Session End

Append to `.ai/sessions/session.log`:
```
Session End: YYYY-MM-DD HH:MM
Summary: [one-line summary]
Next: [what to do next]
---
```

### 5. Feedback Capture

If any observations during session:
```
[ ] Log to appropriate .ai/feedback/ file
[ ] Note any process friction
[ ] Note any tool issues
```

## Long Session Break

For mid-session breaks:

```
[ ] Commit current work (even if WIP)
[ ] Add TODO comment in code if mid-task
[ ] Note in session.log: "Break: [reason], resuming [when]"
```

## Context Recovery

If context is lost (crash, new chat, etc.):

1. Read `.ai/sessions/session.log` for recent activity
2. Read most recent `.ai/sessions/YYYY-MM-DD-*.md`
3. Check git log for recent commits
4. Check git status for uncommitted work
5. Ask user to confirm current task

## Self-Annealing

Track handoff quality:

```
.ai/feedback/process/session-management.md

### YYYY-MM-DD
**Issue:** [context lost / unclear handoff / etc.]
**Cause:** [what went wrong]
**Improvement:** [what would help]
```
