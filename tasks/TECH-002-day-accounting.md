# TECH-002 — Daily accounting and date changes

Status: ready for implementation.
Source: MAIN-003–MAIN-007, DAY-001–DAY-003, DAT-004, DAY-005, SET-007.
Dependencies: TECH-001.

## Work

Separate operations for determining the current day, calculating progress, and adding intake. Determine the day using the device's local date and timezone. Resolve the current date again when adding water so that crossing midnight does not modify yesterday's record.

Update the main screen when the local date changes while the application is running, when it opens, and when it returns from the background. Provide a controllable source of date and time for validation.

## Acceptance criteria

- Intake is 0 ml when the current date has no record.
- New intake equals `min(currentDailyIntake + addedIntake, 10000)`.
- Circle fill equals `min(todayWaterIntake / dailyGoal, 1) * 100`.
- With a 2000 ml goal, adding 200 ml to 1900 ml produces 2100 ml and 100% fill.
- Adding 200 ml to 9900 ml produces 10000 ml; opening the Add dialog through the circle is then blocked.
- After the date changes to the next day, adding 200 ml preserves yesterday's 1900 ml and creates today's 200 ml with the applicable goal.
- A date change without adding water switches the main screen to the new day's record; the same rules apply after returning from the background.
- Timezone changes affect determination of the current day but do not move old records to other dates.

## Validation

Check arithmetic boundaries and date transitions using a controllable clock. Separately verify screen updates while the application is active and after resuming. Manual changes to the device date are outside scope according to DAY-005.
