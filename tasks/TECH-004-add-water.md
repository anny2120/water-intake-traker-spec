# TECH-004 — Adding water

Status: ready for implementation.
Source: ADD-001–ADD-004, MAIN-005–MAIN-007, DAY-003.
Dependencies: TECH-002, TECH-003.

## Work

Create the Add dialog and connect it to the operation that persists intake for the current date. Complete addition after successful local persistence.

## Acceptance criteria

- Tapping an enabled circle opens a dialog with a slider, Add at the bottom right, and X at the top right.
- The initial value is 200 ml; allowed values range from 50 to 1000 ml in 50 ml steps.
- Add saves the selected intake subject to the 10000 ml limit, updates the main screen, and closes the dialog.
- X and tapping outside the dialog close it without changing saved intake.
- The result of a successful Add survives application restart.
- If the date changes between opening the dialog and tapping Add, water is added to the date current at the time of the operation according to DAY-003.

## Validation

Check the minimum, maximum, default value, both specified cancellation methods, exceeding the daily limit, and addition across midnight. NAV-001 does not define Android Back behavior for this dialog, and this task does not introduce a new requirement for it.
