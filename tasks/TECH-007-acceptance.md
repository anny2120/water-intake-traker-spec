# TECH-007 — End-to-end acceptance checks for the local Android application

Status: to be performed after dependencies are implemented.
Source: Scope, MAIN-001–MAIN-007, ADD-001–ADD-004, SET-001–SET-007, HIS-001–HIS-006, DAY-001–DAY-003, DAT-004, DAY-005, NAV-001, ERR-001, Out of scope.
Dependencies: TECH-001–TECH-006.

## Work

Perform end-to-end checks of screen integration, local persistence, and the Android lifecycle. Reuse individual task checks without unnecessary duplication. Record results and any deviations from requirements.

## Acceptance criteria

- A fresh launch without an account or network displays 0 ml, a 2000 ml goal, and an empty history.
- Adding water, saving settings, and viewing history work entirely locally.
- After adding water and restarting, the day's intake and goal are preserved.
- Save changes the goal and today's progress; X and Back in Settings discard the draft.
- History for past dates uses their own goals; viewing it does not change data.
- Crossing midnight while the application is active or in the background displays the new day and preserves yesterday's data.
- Changing the timezone does not change old record dates.
- Intake is limited to 10000 ml, circle fill is capped at 100%, and addition through the circle is blocked at the limit.
- The release excludes functionality outside the current scope: authentication, cloud synchronization, history editing and deletion, reminders, and other units of measurement.
- All TECH-001–TECH-006 criteria are met, including the selected day's actual percentage below the calendar: 2100/2000 displays 105%, with a fully filled circle.

## Validation

Generate the native Android project and build a local debug APK using the documented commands. Run the automated TypeScript tests, then install and launch the APK on an Android emulator for end-to-end acceptance. Use application restarts and a controlled time source for reproducible date transitions. Record the environment, emulator configuration (including Android API level), commands, and results. Manual device date changes are excluded according to DAY-005.
