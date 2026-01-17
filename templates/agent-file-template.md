# [PROJECT NAME] Development Guidelines

Auto-generated from all feature plans. Last updated: [DATE]

## Active Technologies

[EXTRACTED FROM ALL PLAN.MD FILES]

## Project Structure

```text
[ACTUAL STRUCTURE FROM PLANS]
```

## Commands

[ONLY COMMANDS FOR ACTIVE TECHNOLOGIES]

## Code Style

[LANGUAGE-SPECIFIC, ONLY FOR LANGUAGES IN USE]

## Recent Changes

[LAST 3 FEATURES AND WHAT THEY ADDED]

## Guidelines

- **Spec-first**: Before implementing any feature, ensure a spec exists. If unclear, write/update the spec first.

## Review Workflow

For iterative development with human review, use inline markers in code:

- `[Q: ...]` - Question needing answer before proceeding
- `[C: ...]` - Comment or feedback on the approach
- `[TODO: ...]` - Something to add or implement

When you say "check my comments", the agent scans files for these markers and addresses each one.

Example:
```python
# [Q: Should we cache this result?]
result = expensive_computation()
# [TODO: Add error handling for timeout]
```

<!-- MANUAL ADDITIONS START -->
<!-- MANUAL ADDITIONS END -->
