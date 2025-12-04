---
name: weekly-annealing
description: Weekly review of accumulated feedback, propose improvements for human approval. Never auto-apply changes.
---

# Weekly Annealing Review

Aggregate feedback. Identify patterns. Propose refinements. ALL proposals require explicit human approval.

## Core Principle

```
NEVER auto-apply changes.
Observe → Log → Analyze → Propose → (Human Approves) → Apply
```

## When to Use

- Weekly scheduled review
- When feedback logs are substantial
- After multiple feature completions
- When patterns emerge from reviews

## Process

### Step 1: Gather Feedback

Read all `.ai/feedback/` logs from past week:

```
.ai/feedback/
├── guardians/          # False positives, missed issues
│   ├── security.md
│   ├── typescript.md
│   └── ...
├── skills/             # Invocation accuracy
├── process/            # Workflow friction, overrides
└── directives/         # CLAUDE.md suggestions
```

### Step 2: Pattern Analysis

For each category, identify:

- **Recurring issues**: Same problem appearing multiple times
- **Frequent overrides**: Gates overridden often → too strict?
- **Accuracy rates**: Guardian precision and recall
- **Trigger mismatches**: Skills invoked when not needed, or needed but not invoked

### Step 3: Metaprompting (Self-Review)

For agents/skills with issues:

```
1. Read current prompt
2. Read feedback about failures
3. Ask: "Why is this failing?"
4. Generate improved version
5. Explain reasoning
```

### Step 4: Propose Changes

Format each proposal clearly:

```markdown
## Proposal: [Title]

### What
[Specific file and change]

### Why
[Evidence from feedback logs]

### Evidence
- [Date]: [Issue]
- [Date]: [Issue]
- [Date]: [Issue]

### Impact
- Positive: [What improves]
- Risk: [What could break]

### Diff
\`\`\`diff
- Old line
+ New line
\`\`\`

### Recommendation
[APPLY / DEFER / INVESTIGATE MORE]
```

### Step 5: Human Decision

Present all proposals to human. For each:

- **Approved**: Apply change, log to `.ai/annealing/history/`
- **Rejected**: Note reasoning, don't re-propose without new evidence
- **Deferred**: Move to backlog for later consideration

### Step 6: Apply Approved Changes

For each approved change:

```
1. Make the change
2. Log to .ai/annealing/history/YYYY-MM-DD-applied.md:
   - What changed
   - Why (evidence)
   - Rollback instructions
3. Test if possible
4. Verify no regression
```

### Step 7: Skill Ecosystem Audit

Run skill-audit as part of annealing:

```
[ ] Check recommended skills for updates
[ ] Scan curated lists for new discoveries
[ ] Review TDD queue for boilerplate skills
[ ] Present findings for approval
```

Read `.ai/skills/recommended-skills.json` and:

1. **Updates Available**
   - Web search for updates to recommended skills
   - Present changelog/diff if found
   - Options: [Apply] [Skip] [Review]

2. **New Discoveries**
   - Check curated lists for skills not in recommended or rejected
   - Evaluate relevance to project
   - Options: [Add to recommended] [Reject] [Evaluate later]

3. **TDD Queue**
   - List boilerplate skills needing fixtures
   - Prioritize by impact and usage
   - Options: [Start TDD build] [Defer]

4. **Update Tracking**
   - Set last_audit timestamp
   - Log findings to .ai/feedback/skills/

### Step 8: Update Current World State

Review and update `.ai/context/current-world-state.md`:

```
[ ] Current date/year correct
[ ] AI model versions current
[ ] Tool versions current (Node, pnpm, etc.)
[ ] Any recent announcements relevant
```

## Rollback Protocol

If an annealing change causes problems:

```
1. Check .ai/annealing/history/ for rollback instructions
2. Revert the change
3. Log the failure to .ai/feedback/
4. Mark proposal as "failed" (don't re-propose)
```

## Output

Weekly summary to `.ai/annealing/weekly/YYYY-MM-DD-review.md`:

```markdown
# Weekly Annealing Review: YYYY-MM-DD

## Feedback Reviewed
- Guardian feedback: X entries
- Skill feedback: Y entries
- Process feedback: Z entries

## Proposals Made
1. [Title] — [APPROVED/REJECTED/DEFERRED]
2. [Title] — [APPROVED/REJECTED/DEFERRED]

## Changes Applied
- [List of applied changes]

## Rejected (with reasons)
- [Proposal]: [Reason]

## Observations
[Trends, concerns, notes for next week]
```

## Constraints

1. **NEVER auto-apply** — All changes require explicit approval
2. **NEVER re-propose rejected** — Unless new compelling evidence
3. **Always show evidence** — No proposals without logged feedback
4. **Maintain rollback** — Every change must be reversible
5. **One week minimum** — Don't propose changes on thin evidence
