# TECH-006 — History

Status: ready for implementation.
Source: HIS-001–HIS-006, NAV-001, SET-007, DAY-002.
Dependencies: TECH-001, TECH-002, TECH-003.

## Work

Create full-screen History with a calendar, date selection, and daily data display. Use the selected date's stored goal rather than the current setting. Provide read-only access to data.

## Acceptance criteria

- The current local date is selected on opening.
- Current and past dates can be selected; future dates are unavailable.
- Dates with data display only progress circles without numeric percentage labels.
- Numeric information for the selected day appears only below the calendar: intake, stored goal, and percentage rounded to an integer, according to HIS-002. This set of information is defined in HIS-002.
- A date without data displays the exact text `No available data for selected date`; no progress circle is shown.
- For past records [1500, 2000], [2000, 2000], [2100, 2000], and [1400, 2000], circle fills are 75%, 100%, 100%, and 70%, respectively, according to the HIS-006 example.
- Changing the overall goal does not recalculate stored goals for past days.
- X at the top right and Android Back close History.
- The screen does not allow editing history or deleting records.

## Specification references

- HIS-006 defines all four example records as past dates; SET-007 defines updates to the current day's goal.
- The numeric percentage below the calendar equals `waterIntake / storedDailyGoal * 100`, rounded to an integer without capping at 100%. For 2100/2000, it displays 105%, while the circle is fully filled.

## Validation

Check an empty date, a past record, the current date, the restriction on future dates, closing, and preservation of data after viewing. Verify that the calendar has no numeric percentage labels. Verify that 2100 ml with a 2000 ml goal displays 105% below the calendar while the circle is fully filled.
