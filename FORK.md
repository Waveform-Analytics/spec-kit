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

## Upstream Sync

**Based on:** github/spec-kit @ 9111699 (2026-01-16)

When syncing from upstream, note any merge decisions below.

---

<!-- Future sync notes go here -->