# Claude Code Boilerplate

By [Songbird Digital](https://github.com/songbirddigital)

A production-ready boilerplate for Claude Code projects featuring guardian agents, self-annealing, and structured workflows.

## Features

- **9 Guardian Agents** — Specialized reviewers for security, TypeScript, architecture, testing, performance, docs, accessibility, API, and database
- **Self-Annealing** — Continuous improvement with human approval gates
- **Apprentice Mode** — Educational, contextual assistance for developers
- **Research-First** — Web search before recommendations when currency matters
- **Feature Completion Workflow** — Structured process from branch to merge
- **External Review Integration** — Codex and Gemini reviewer support

## Quick Start

```bash
# Copy to new project
cp -r claude-code-boilerplate/ my-project/
cd my-project/

# Initialize
git init
claude
/setup
```

See [SETUP.md](./SETUP.md) for detailed instructions.

## Structure

```
.claude/                    # Configuration
├── memory/                 # Domain memory (persistent state)
│   ├── features.json       # Machine-readable backlog
│   ├── progress.log        # Session history + handoff
│   ├── decisions.md        # Architectural Decision Records
│   └── issues.md           # Problem tracking
├── agents/                 # Agent protocols
│   ├── INITIALIZER.md      # Bootstrap domain memory
│   ├── PLANNER.md          # Feature planning
│   ├── IMPLEMENTER.md      # Worker protocol
│   ├── REVIEWER.md         # Pre-merge review orchestration
│   └── domains/            # Domain-specific agents
│       ├── security/       # Guardian + Specialist
│       ├── database/       # Guardian + Specialist
│       └── ...             # 9 domains total
├── skills/                 # Workflow orchestration
├── commands/               # Custom slash commands
├── templates/              # Feature spec templates
└── settings.json           # Hooks and guardian config

.ai/                        # Operations
├── feedback/               # Self-annealing observations
│   ├── guardians/
│   ├── skills/
│   ├── memory/             # Domain memory feedback
│   └── ...
├── annealing/              # Weekly review history
├── sessions/               # Session logs
├── context/                # World state
└── tasks/                  # Work assignments

CLAUDE.md                   # Entry point (~170 lines)
AGENTS.md                   # Codex reviewer touchpoint
GEMINI.md                   # Gemini reviewer touchpoint
SETUP.md                    # Setup instructions
```

## Guardian Agents

| Guardian | Model | Focus |
|----------|-------|-------|
| security | sonnet | OWASP, secrets, injection, tenant isolation |
| typescript | haiku | Types, strict mode, no `any` |
| architecture | sonnet | Patterns, modularity, SOLID |
| test | haiku | Coverage, quality, edge cases |
| performance | sonnet | N+1, complexity, memory |
| docs | haiku | Documentation currency |
| accessibility | sonnet | A11y, WCAG, ARIA |
| api | sonnet | REST conventions, versioning |
| database | sonnet | Schema, migrations, queries |

## Skills

| Skill | Description |
|-------|-------------|
| guardian-agents | Orchestrate parallel code review |
| feature-completion | Feature branch → merge workflow |
| full-codebase-review | Develop → main comprehensive review |
| weekly-annealing | Self-improvement cycle |
| apprentice-mode | Detailed teaching mode |
| guardian-builder | Create new guardians with TDD |
| boilerplate-sync | Sync improvements between instances |
| boilerplate-migrate | Add boilerplate to existing projects |

## Commands

| Command | Description |
|---------|-------------|
| /setup | Initialize new project with domain memory |
| /migrate | Add boilerplate to existing project |
| /status | Show current project status |
| /plan | Invoke PLANNER for feature planning |
| /review | Trigger guardian review + external reviewers |
| /complete-feature | Feature completion checklist |
| /feedback | Quick feedback capture |

## Self-Annealing

The boilerplate improves itself:

1. **Observe** — Track guardian accuracy, skill triggers, process friction
2. **Log** — Save to `.ai/feedback/`
3. **Analyze** — Weekly review identifies patterns
4. **Propose** — Suggest improvements with evidence
5. **Approve** — Human approves all changes (never auto-apply)
6. **Apply** — Changes applied with rollback capability

## Customization

### Add/Remove Guardians

Edit `.claude/settings.json`:
```json
"guardians": {
  "enabled": ["security", "typescript", "test"]
}
```

### Adjust Triggers

```json
"triggers": {
  "pre-commit": true,
  "pr-creation": false,
  "manual": true
}
```

### Create Custom Guardian

Use the `guardian-builder` skill with TDD:
1. Create test fixtures in `.ai/fixtures/[name]/`
2. Build guardian to detect issues
3. Test until 100% accuracy

## Philosophy

- **Lean CLAUDE.md** — Under 80 lines, link to details
- **Context on demand** — Load what's relevant, not everything
- **Human in the loop** — All self-annealing requires approval
- **Research first** — Search before recommending
- **Apprentice-friendly** — Explain why, use analogies

## Resources

- [Design Document](./docs/plans/2025-12-03-claude-code-boilerplate-design.md)
- [Setup Guide](./SETUP.md)
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Claude Code Docs](https://docs.claude.com/)

## Future Enhancements

Tracked for future implementation:

- [ ] SPO (Self-Prompt Optimization) for guardians
- [ ] Promptbreeder-style prompt evolution
- [ ] DSPy integration for automated optimization
- [ ] Automatic trust escalation
- [ ] Cross-project learning

---

## License

MIT License - see [LICENSE](./LICENSE)

---

Created by [Songbird Digital](https://github.com/songbirddigital)

Built with research from [VoltAgent](https://github.com/VoltAgent/awesome-claude-code-subagents), [wshobson/agents](https://github.com/wshobson/agents), [claude-flow](https://github.com/ruvnet/claude-flow), [obra/superpowers](https://github.com/obra/superpowers), and contractor-system patterns.
