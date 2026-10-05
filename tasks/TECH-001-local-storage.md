# TECH-001 — Local storage and initialization

Status: ready for implementation after TECH-000.
Source: Scope, ERR-001, ADD-004, SET-006, SET-007, HIS-006, DAY-002.
Architecture: [architecture.md](../../android/docs/architecture.md), [ADR-001 — Mobile application stack](../../android/adr/0001-app-stack.md).
Dependencies: TECH-000.

## Work

Prepare local storage using SQLite accessed through `expo-sqlite`, as selected in ADR-001. Store settings and daily records in the same database, which is the persistent source of truth for local application data. Each daily record contains a fixed local date, total intake in ml, and the goal applicable to that day. Provide operations to read settings, a daily record, and history; save intake; and change the goal.

Changing the daily goal MUST be atomic from the application's point of view:

- The saved application setting contains the new goal.
- If a record for the current day exists, that record contains the new goal.
- If no current-day record exists, changing the goal MUST NOT create one.

The application MUST NOT expose a state in which only one of the required updates has been persisted. Use a SQLite transaction for the required updates to settings and the existing current-day record, preserving this guarantee after reopening storage following an interrupted update.

Do not create a placeholder water record for an empty day solely because the application is opened or a setting is saved. Reads of an empty date must have no persistent side effects. Do not recalculate stored record dates using a new timezone.

## Acceptance criteria

- Settings and daily records are persisted in the same SQLite database through `expo-sqlite`.
- When no data exists, the application initializes with a 2000 ml goal and an empty history.
- After successful addition, the day's intake and goal remain available after restart; the operation completes only after local persistence.
- The saved setting survives restart.
- Changing the goal updates the saved setting and the goal of an existing current-day record atomically according to SET-007; past dates' data remains unchanged.
- If no current-day record exists, changing the goal updates the setting without creating a daily record.
- After an interrupted goal update and reopening storage, the application exposes either the complete previous state or the complete new state, never a partially persisted update.
- Multiple reads of an empty date MUST NOT create or modify persistent data.
- Changing the timezone does not change existing record dates.
- Storage requires no account, network, or server.

## Validation

Run integration checks using SQLite through `expo-sqlite`: a fresh installation, writing and reopening storage, and changing the goal with and without a current-day record while past records are present. Verify that repeated reads of an empty date leave persistent data unchanged. Exercise an interrupted goal update and reopen storage to verify atomicity; check both the application setting and the current-day record. Use the past-day example defined in HIS-006 to verify preservation of historical goals.
