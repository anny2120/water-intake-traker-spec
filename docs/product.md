# Water Intake Tracker

The application allows users to track their daily water intake.

Users can record the water intake during the day,
monitor progress toward a configurable daily goal, and review
their intake history.

## Goal

Help users keep track of how much water they have consumed during a day.

## Product principles

The application should remain minimal and focused on water intake tracking.

It should not include:
- advertisements;
- sponsored content;
- educational articles;
- gamification;
- social features;
- unrelated wellness functionality.

New features should only be added if they directly support water intake tracking.

## Scope

The first version of the application supports Android only and works entirely locally on the user's device.

- No user authorization is required.
- No cloud synchronization is implemented.
- All application data is stored locally on the device.

## Features
### 1. Main screen
#### MAIN-001
 On the main screen in the center of the screen (vertically and horizontally) placed a white circle with black border. In the center of circle is displayed current day water intake in milliliters (with ml). The main screen background color MUST be #F2DDC6.

#### MAIN-002
 The circle must be filled in with blue color ( #add8e6) from bottom to top as new water intake is added. The blue colored part must reflect percentage of current day water intake comparing to established in settings daily goal water intake (by default 2,000 ml). If added water is more then daily goal water intake the circle is completely filled but numbers increases up untill 10,000 ml.

#### MAIN-003

 The fill percentage MUST be calculated as:

 min(todayWaterIntake / dailyGoal, 1) * 100

#### MAIN-004
 When the application is opened, the main screen MUST display the stored water intake for the current local date.
 If no water intake exists for the current date, 0 ml MUST be displayed.

#### MAIN-005
Given:
- today's intake is 1900 ml;
- daily goal is 2000 ml;

When:
- the user adds 200 ml;

Then:
- today's intake is 2100 ml;
- displayed progress is 100%;
- the displayed current daily intake is 2100 ml.

#### MAIN-006
The daily water intake MUST NOT exceed 10,000 ml.
When water is added, the resulting value MUST be calculated as:
min(currentDailyIntake + addedIntake, 10,000)

#### MAIN-007
Given:
- today's intake is 9,900 ml;

When:
- the user adds 200 ml;

Then:
- today's intake is 10,000 ml;
- displayed progress is 100%;
- the displayed current daily intake is 10,000 ml;
- tapping on the circle to add new water intake is blocked.

### 2. Adding water
#### ADD-001
 User can add water intake by tapping the circle. After tap new dialog appears with slider field to select water intake to add and with button Add in bottom right corner and close button with X icon in the top right corner.

#### ADD-002
 Default value for adding water intake is 200 milliliters. Minimum value for the input is 50 milliliters, maximum is 1,000ml. Step for slider is 50 ml.

#### ADD-003
 If user taps on Add button the selected water intake adds to the current daily intake and the dialog is closing. If user taps on Close button the dialog is closing without adding new water intake. If user taps outside of dialog the dialog should be closed as if user taps on close button.

#### ADD-004
After the user taps Add, the updated daily water intake MUST be
persisted locally before the operation is considered complete.

The value MUST survive application restarts.

### 3. Settings
#### SET-001
 In the right top corner of main screen located settings button in shape of cogwheel. Tapping the Settings button opens the full-screen Settings screen.

#### SET-002
 Settings are shown as input fields with labels. In the right bottom corner of dialog located Save button. In the top right corner located close X button.

#### SET-003
 Currently there is only one setting:
 - Daily goal (ml) - slider field

#### SET-004
 By default daily goal is 2,000 ml. User can change it between 100 and 5,000 ml, step - 50 ml.

#### SET-005
Tapping Save persists the changed settings and closes the Settings screen.

Tapping Close discards all changes made since the Settings screen was opened and closes the screen.

#### SET-006
 Settings MUST be persisted locally on the device after the user taps Save.
 Persisted settings MUST survive application restarts.

#### SET-007

Changing the daily goal applies to the current day and future days.

If the current day already contains recorded water intake, its stored daily goal MUST be updated to the new value.

Daily goals stored for previous dates MUST NOT be changed.

### 4. History
#### HIS-001
 In the top left corner of main screen located History button with calendar icon. Tapping the History button opens the full-screen History screen. Dialog should fill the whole screen.

#### HIS-002
 In the dialog is shown calendar with circle of progress on each date. Under calendar is shown water intake, goal and percentage of completion for selected day (rounded to integer value). By default selected current date.
 
#### HIS-003
 User is able to select current date and previous days. Future days are not allowed to select. If there is no data for the selected date, under calendar should be shown "No available data for selected date". There should be no circle of progress on dates without data.

#### HIS-004
 Close X button is in the top right corner of history dialog. Tapping on it closes dialog.

#### HIS-005
 In the history dialog user can only watch information and cannot edit it

#### HIS-006
For each day with recorded water intake, the application MUST persist:
- the total water intake;
- the daily goal applicable to that day.

Given:
- user used application for 4 days and have history of 4 days with default daily goal 2,000 ml;
- they have stored values: [1,500, 2,000], [2,000, 2,000], [2,100, 2,000], [1,400, 2,000].

When:
- user changes daily goal in settings to 2,200 ml;

Then:
- history circles with progress displayed as it was previously: 75% for 1st day, 100% for next, 100% and 70%;
- new values should be saved with new goal value - 2,200 ml;
- percentage for new values will be calculated with this new goal.

### 5. Day and timezone rules

#### DAY-001
 A user's day is determined using the timezone of the user's device

#### DAY-002
 Changing the device timezone MUST NOT change the date assigned to previously recorded water intake entries.

#### DAY-003
Given:
- today's intake is 1900 ml;
- user date changes to the next;

When:
- the user adds 200 ml;

Then:
- yesterday's intake is still 1900 ml;
- today's intake is 200 ml;
- displayed progress is min(200 / dailyGoal, 1) * 100.

#### DAT-004
When the current local date changes while the application is running,
the main screen MUST switch to the water intake record for the new date.

The same check MUST be performed whenever the application is opened
or resumed from the background.

#### DAY-005
The application relies on the device local date and time.

Behavior caused by manually changing the device date is outside
the scope of the first version.

### 6. Android navigation
#### NAV-001
On the Settings and History screens, Android system Back behaves the same as tapping the Close button.

### 7. Error handling
#### ERR-001
 If no persisted application data exists, the application MUST initialize itself with default settings and an empty water intake history.

### 8. Out of scope
The first version does not support:
- iOS;
- web application;
- manually editing historical records;
- deleting water entries;
- reminders;
- multiple units;
- units other than milliliters.