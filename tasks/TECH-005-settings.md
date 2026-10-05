# TECH-005 — Daily goal settings

Status: ready for implementation.
Source: SET-001–SET-007, NAV-001.
Dependencies: TECH-001, TECH-002, TECH-003.

## Work

Create full-screen Settings with an editable copy of the current goal. Connect Save to local persistence of the setting and updating the goal of an existing current-day record. Changes must not be persisted before Save.

## Acceptance criteria

- The only field is a slider labeled Daily goal (ml).
- The default value is 2000 ml; the range is 100–5000 ml in 50 ml steps.
- Save is at the bottom right; X is at the top right.
- Save persists the goal and then closes the screen; the value survives restart.
- X and Android system Back close the screen and discard changes made since it was opened.
- The new goal applies to the current day and future days.
- If today's record exists, its saved goal is updated; past records retain their goals according to SET-007.
- After saving, main-screen progress is recalculated using the new goal.

## Validation

Check slider boundaries, Save, X, Back, reopening, and restart. Verify goal changes with and without today's record and preservation of past goals. Use the past-day example defined in HIS-006 to verify preservation of historical goals.
