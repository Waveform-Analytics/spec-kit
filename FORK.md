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

Changed `/speckit.implement` default behavior to pause for human review. After writing code, the agent notifies the user and reminds them they can add inline markers:
- `[Q: ...]` - Questions
- `[C: ...]` - Comments/feedback
- `[TODO: ...]` - Things to add

When processing markers, straightforward items are fixed immediately; complex ones are discussed first.

Automated mode available via "implement all" or "no review".

**Files changed:**
- `templates/commands/implement.md` - Added Review Workflow as default
- `templates/agent-file-template.md` - Added Review Workflow documentation

## Upstream Sync

**Based on:** github/spec-kit @ 9111699 (2026-01-16)

When syncing from upstream, note any merge decisions below.

---

<!-- Future sync notes go here -->