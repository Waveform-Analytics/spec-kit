---
description: Generate a reviewer-friendly test plan documenting what behaviors will be verified for the feature.
handoffs:
  - label: Generate Tasks
    agent: speckit.tasks
    prompt: Generate implementation tasks including test tasks
    send: true
  - label: Analyze Consistency
    agent: speckit.analyze
    prompt: Check consistency across spec, plan, and tests
    send: true
---

## User Input

```text
$ARGUMENTS
```

You **MUST** consider the user input before proceeding (if not empty).

## Purpose

Generate a `tests.md` file that:

1. Documents what behaviors will be tested (for domain reviewers)
2. Provides implementation guidance (for developers/AI)
3. Ensures traceability from requirements to tests

The primary audience is **non-technical reviewers** who want to verify that
important requirements have test coverage. Technical details go in an appendix.

## Outline

1. **Setup**: Run `.specify/scripts/bash/check-prerequisites.sh --json` from repo root
   and parse FEATURE_DIR and AVAILABLE_DOCS list. All paths must be absolute.

2. **Load source documents**: Read from FEATURE_DIR:
   - **Required**: spec.md (user stories, acceptance scenarios, edge cases)
   - **Required**: plan.md (project structure, test file locations)
   - If spec.md doesn't exist, ERROR with message to run `/speckit.specify` first
   - If plan.md doesn't exist, ERROR with message to run `/speckit.plan` first

3. **Check for existing test artifacts**:
   - Check if tasks.md exists in FEATURE_DIR
   - Check if test files exist in locations specified by plan.md (e.g., `tests/unit/`)
   - Note what was found (will be used in step 7)

4. **Extract test requirements from spec.md**:
   - User stories with priorities (P1, P2, P3...)
   - Acceptance scenarios (Given/When/Then)
   - Edge cases section
   - Functional requirements (FR-001, FR-002...)
   - Success criteria

5. **Extract from plan.md**:
   - Project structure (test directory layout)
   - Testing framework
   - Technical context

6. **Generate tests.md** using `.specify/templates/tests-template.md`:
   - Fill feature name and branch from spec.md
   - Generate Test Summary with key behaviors (plain language)
   - Generate Behavior Coverage section for each user story
   - Map acceptance scenarios to test descriptions
   - Generate Edge Cases table from spec.md edge cases
   - Fill Coverage Checklist
   - Fill Implementation Notes with file paths and structure from plan.md

7. **Reconciliation** (if existing artifacts were found in step 3):
   - Compare generated tests.md against existing tasks.md and/or test files
   - Report discrepancies in a clear summary:
     - **Covered**: Spec requirements that have existing test coverage
     - **Gaps**: Spec requirements that lack test coverage
     - **Orphans**: Existing tests that don't map to spec requirements
   - For each gap, ask user: "Add to tasks?" or "Note as out-of-scope?"
   - For each orphan, ask user: "Missing from spec?" or "Remove test?"
   - Update tests.md to reflect decisions (mark covered items, note gaps)

8. **Report**: Output path to generated tests.md and summary:
   - Count of user stories covered
   - Count of edge cases covered
   - Count of acceptance scenarios mapped
   - Flag any gaps (user stories without tests, unmapped scenarios)

## Generation Rules

### Language Guidelines

**Primary sections (for reviewers)** - Use plain, non-technical language:

- "Load a configuration file and verify all values are accessible"
- "Attempt to save with missing required fields, confirm error message"
- NOT: "Assert model.field == expected using pytest fixture"
- NOT: "Mock the database connection and verify query parameters"

**Implementation Notes (for developers)** - Technical details allowed:

- File paths, test names, fixture locations
- Framework-specific patterns
- Directory structure

### Mapping Acceptance Scenarios

For each acceptance scenario in spec.md:

```text
Given [initial state], When [action], Then [expected outcome]
```

Create a test description:

```markdown
| Requirement | How It's Tested |
|-------------|-----------------|
| [Action] produces [outcome] | [Plain description of test] |
```

### Edge Case Coverage

For each edge case in spec.md, create a row:

```markdown
| Scenario | Expected Behavior | Covered |
|----------|-------------------|---------|
| [Edge case from spec] | [Expected handling] | [ ] |
```

### Handling Missing Information

- If spec.md has no edge cases section: Add placeholder row with TODO
- If acceptance scenarios are vague: Flag in Open Questions section
- If plan.md lacks test directory structure: Ask user to clarify before proceeding

### Coverage Checklist

Always include these standard checks:

- [ ] Every user story has test coverage defined
- [ ] All acceptance scenarios from spec.md are addressed
- [ ] Edge cases from spec.md are covered
- [ ] Invalid inputs produce clear error messages
- [ ] Each test maps back to a requirement

## Output Location

Write to: `FEATURE_DIR/tests.md`
