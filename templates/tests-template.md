---
description: "Test plan template for feature specification"
---

# Test Plan: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`
**Spec**: [`spec.md`](./spec.md)
**Status**: Draft

---

## About This Document

This test plan describes what behaviors will be verified by automated tests.
It helps reviewers confirm that important requirements have coverage before
implementation begins.

- **For reviewers**: Focus on "Behavior Coverage" sections to verify the right
  things are being tested. You don't need programming knowledge to review this.
- **For implementers**: See "Implementation Notes" at the end for technical details.

---

## Test Summary

**Coverage goal**: [e.g., All user stories and edge cases covered]

**Key behaviors being tested**:
- [Behavior 1 in plain language]
- [Behavior 2 in plain language]
- [Behavior 3 in plain language]

---

## Behavior Coverage by User Story

<!--
  For each user story from spec.md, describe what behaviors will be verified.
  Write in plain language - focus on WHAT is tested, not HOW.

  Example:
    Requirement: "Users can reset their password"
    How it's tested: "Attempt password reset, confirm new password works"
-->

### User Story 1 - [Title] (Priority: P1)

**What we're verifying**:

| Requirement | How It's Tested |
|-------------|-----------------|
| [Requirement from spec] | [Plain description of verification] |
| [Requirement from spec] | [Plain description of verification] |

**Specific checks**:
- [ ] [Plain description of what's checked]
- [ ] [Plain description of what's checked]

---

### User Story 2 - [Title] (Priority: P2)

**What we're verifying**:

| Requirement | How It's Tested |
|-------------|-----------------|
| [Requirement from spec] | [Plain description of verification] |

**Specific checks**:
- [ ] [Plain description]

---

<!--
  Repeat for each user story from spec.md.
  Match priority order (P1, P2, P3...) from the spec.
-->

---

## Edge Cases & Error Handling

<!--
  What boundary conditions and error scenarios are tested?
  Extract from "Edge Cases" section of spec.md.
-->

| Scenario | Expected Behavior | Covered |
|----------|-------------------|---------|
| [What could go wrong] | [How system should respond] | [ ] |
| [Unusual input or condition] | [Expected handling] | [ ] |
| [Boundary condition] | [Expected behavior] | [ ] |

---

## Coverage Checklist

<!--
  Checklist for reviewers to assess test completeness.
-->

**Requirements**
- [ ] Every user story has test coverage defined
- [ ] All acceptance scenarios from spec.md are addressed
- [ ] Edge cases from spec.md are covered

**Error Handling**
- [ ] Invalid inputs produce clear error messages
- [ ] Errors identify what went wrong and where

**Traceability**
- [ ] Each test maps back to a requirement or acceptance scenario

---

## Open Questions

<!--
  Flag items needing reviewer input before implementation.
-->

- [ ] [Question about test scope, priorities, or expected behavior]

---
---

# Implementation Notes

<!--
  Technical details for developers and AI assistants.
  Reviewers can skip this section.
-->

## Naming Convention

Use consistent test names following this pattern:

```
test_[component]_[behavior]_[scenario]
```

**Examples**:
- `test_loader_valid_input_succeeds`
- `test_loader_missing_field_returns_error`
- `test_validator_boundary_value_accepted`

## Test File Organization

```
tests/
├── unit/           # Isolated component tests
├── integration/    # Multi-component tests
└── fixtures/       # Sample data for tests
```

## Test Data

| File | Purpose |
|------|---------|
| `valid_minimal.[ext]` | Smallest valid input for basic tests |
| `valid_complete.[ext]` | Full-featured input covering all options |
| `invalid_*.[ext]` | Various invalid inputs for error tests |

## Story-to-File Mapping

| User Story | Test Location |
|------------|---------------|
| US1 | `tests/unit/test_[component].py` |
| US2 | `tests/unit/test_[component].py` |
| Integration | `tests/integration/test_[flow].py` |