# Migrate to Boilerplate

Invoke the `boilerplate-migrate` skill to add boilerplate structure to this project.

## Usage

This command should be run in a project that doesn't yet have the boilerplate structure.

## Process

1. Run pre-flight checks
2. Create backup branch
3. Fetch boilerplate source
4. Create directory structure
5. Merge or create CLAUDE.md
6. Merge settings.json
7. Copy boilerplate components
8. Create .boilerplate.json
9. Initialize .ai/ structure
10. Register instance
11. Show summary

## Options

You can specify a mode:

- `/migrate init` — Full interactive migration (default)
- `/migrate check` — Dry run, show what would change
- `/migrate update` — Update existing migration to latest

## After Migration

1. Review merged CLAUDE.md
2. Customize .ai/SHARED-CONTEXT.md with project details
3. Run `sync status` to verify boilerplate connection
4. Start new session to test the greeting

## Rollback

If needed: `git checkout pre-boilerplate-backup`
