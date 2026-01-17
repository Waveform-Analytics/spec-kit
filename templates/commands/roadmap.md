---
description: Create or update the project feature roadmap, syncing status with existing specs.
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty).

## Outline

Manage the project roadmap at `/memory/roadmap.md`.

### If roadmap doesn't exist:

1. Copy template from `/templates/roadmap-template.md` to `/memory/roadmap.md`
2. Ask user about project phases and initial features to track
3. Fill in the template with provided information

### If roadmap exists:

1. Load `/memory/roadmap.md`
2. Scan `/specs/` directory for existing specifications
3. Update the Progress Summary table:
   - Match features to spec directories
   - Update Status based on what exists:
     - Spec exists with plan.md → "Spec done"
     - Spec exists with tasks.md → "Implementing"
     - Spec exists with completed tasks → "Done"
   - Update Spec column with paths to existing specs
4. If user provided input, add new features or update existing ones
5. Report changes made

### User commands:

- `add [feature]` - Add a new feature to track
- `update` - Sync status with existing specs (default if no args)
- `status` - Show current progress summary