# Fork: Waveform-Analytics/spec-kit

> Fork of [github/spec-kit](https://github.com/github/spec-kit)

## What's Different

| Change | Rationale |
|--------|-----------|
| Installation URLs point to this repo | Required for fork to function |
| Removed release/docs badges from README | Don't apply to this fork |
| README tagline tweaked | Personal preference |

## Customizations

### Iterative implement workflow with review markers

Changed `/speckit.implement` default behavior to pause for human review after every file:

- Stops after each file is created, prompts user to review
- AI includes detailed comments in code to make review easier
- User can add inline markers:
  - `[Q: ...]` - Questions
  - `[C: ...]` - Comments/feedback
  - `[TODO: ...]` - Things to add

When processing markers, straightforward items are fixed immediately; complex ones are discussed first.

Automated mode available via "implement all" or "no review".

**Files changed:**

- `templates/commands/implement.md` - Added Review Workflow as default
- `templates/agent-file-template.md` - Added Review Workflow documentation

### Spec-first guideline

Added "Spec-first" guideline to agent-file-template.md: ensure a spec exists before implementing any feature.

### Roadmap template and command

Added roadmap support for tracking multi-feature projects:

- `/speckit.roadmap` command to create/update the roadmap
- Syncs status with existing specs automatically
- Commands: `add [feature]`, `update`, `status`

**Files added:**

- `templates/roadmap-template.md` - Template for roadmap
- `templates/commands/roadmap.md` - Slash command

### Test plan command

Added `/speckit.tests` command to generate reviewer-friendly test plans:

- Documents what behaviors will be tested in plain language
- Helps non-technical reviewers verify test coverage
- Maps spec requirements to tests for traceability
- Reconciles with existing tests, flags gaps and orphans

**Files added:**

- `templates/tests-template.md` - Template for test plans
- `templates/commands/tests.md` - Slash command

### AI instruction files during init

`specify init` now creates an AI-specific instruction file for the selected assistant:

| AI | Instruction File |
|----|------------------|
| Claude | `.claude/CLAUDE.md` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Cursor | `.cursor/rules/project.mdc` |
| Windsurf | `.windsurfrules` |
| Others | `instructions.md` (fallback) |

Features:
- If file exists, prompts: keep original / replace / append
- Cursor files include required MDC frontmatter
- Unsupported AIs offered generic `instructions.md` fallback

**Files changed:**
- `src/specify_cli/__init__.py` - Added `AI_INSTRUCTION_FILES`, `DEFAULT_AI_INSTRUCTIONS`, `setup_ai_instructions()`

## Versioning

This project uses [hatch-vcs](https://github.com/ofek/hatch-vcs) for dynamic versioning from git tags.

### How it works

- **Patch versions** (0.0.X) are created automatically by the release workflow on every push to `main`
- **Minor/major versions** require a manual tag

### To bump minor or major version

```bash
# Minor bump (new features)
git tag v0.1.0
git push --tags

# Major bump (breaking changes)
git tag v1.0.0
git push --tags
```

The workflow then continues auto-incrementing patches from your new tag.

### Version convention

| Bump | When | Example |
|------|------|---------|
| PATCH | Bug fixes, small tweaks | 0.0.1 → 0.0.2 |
| MINOR | New features, backward compatible | 0.0.5 → 0.1.0 |
| MAJOR | Breaking changes | 0.9.0 → 1.0.0 |

## Upstream Sync

**Based on:** github/spec-kit @ 9111699 (2026-01-16)

When syncing from upstream, note any merge decisions below.

---

<!-- Future sync notes go here -->