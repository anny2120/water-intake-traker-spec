# TECH-003 — Main screen

Status: ready for implementation.
Source: MAIN-001–MAIN-007, SET-001, HIS-001.
Dependencies: TECH-002.

## Work

Create the main screen and connect it to the current daily record. Center the circle horizontally and vertically, with Settings at the top right and History at the top left.

## Acceptance criteria

- The screen background is `#F2DDC6`; the circle is white with a black border.
- The current intake is displayed in the center of the circle with the ml unit.
- The circle fills from bottom to top with `#add8e6` according to MAIN-003.
- Intake above the goal continues to be displayed up to 10000 ml; the circle remains fully filled.
- On launch, the stored intake for the current date is displayed, or 0 ml if no record exists.
- At 10000 ml, tapping the circle does not open the Add dialog.
- The cogwheel button opens full-screen Settings; the calendar button opens full-screen History.

## Validation

Check appearance and the 0, 1900, 2100, and 10000 ml states with a 2000 ml goal. Verify restoration after restart and navigation to the other screens.
