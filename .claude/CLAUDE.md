# Project Instructions

## Fork Documentation

This is a fork of [github/spec-kit](https://github.com/github/spec-kit). When making changes:

1. **Update FORK.md** for any user-facing changes:
   - New features or commands
   - Changed default behaviors
   - Modified templates
   - CLI changes

2. **Follow the existing format** in FORK.md:
   - Add under "Customizations" section
   - Include rationale and files changed
   - Keep descriptions concise

3. **Don't document** internal refactors, dependency updates, or changes that don't affect user behavior.

## Development

- Use `uv` for all Python operations
- Test CLI changes with `uv tool install --force .` then run `specify` commands
- This project uses hatch-vcs for versioning from git tags

## Review Workflow

After creating or significantly editing a file, pause for review.

I'll use these markers:
- `[Q: ...]` - question
- `[C: ...]` - comment/feedback
- `[TODO: ...]` - something to add

When I say "check my comments", scan files for these markers and address them.
