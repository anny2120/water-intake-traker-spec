# Technical tasks: local Android application

Source: [product.md](../docs/product.md). These tasks cover the current version. Authentication, accounts, a server, and synchronization are outside the scope.

The implementation stack is already selected: React Native, TypeScript, Expo, and SQLite accessed through `expo-sqlite`. The decision and rationale are documented in [ADR-001 — Mobile application stack](../../android/adr/0001-app-stack.md); [architecture.md](../../android/docs/architecture.md) defines the current architecture. TECH-000 configures the project using this stack.

Architecture documentation is maintained in the separate implementation repositories. The Android repository owns the Android architecture and ADRs; this specification repository defines product behavior and tasks that reference those decisions.

The native Android project is generated before building and is not stored in version control. Automated tests are written in TypeScript; native Android instrumentation tests are not required. Acceptance includes installing and launching a locally built debug APK on an Android emulator, followed by the feature checks defined in these tasks.

| Task | Dependencies |
| --- | --- |
| [TECH-000 — Bootstrap Android application](TECH-000-bootstrap-android.md) | None |
| [TECH-001 — Local storage and initialization](TECH-001-local-storage.md) | TECH-000 |
| [TECH-002 — Daily accounting and date changes](TECH-002-day-accounting.md) | TECH-001 |
| [TECH-003 — Main screen](TECH-003-main-screen.md) | TECH-002 |
| [TECH-004 — Adding water](TECH-004-add-water.md) | TECH-002, TECH-003 |
| [TECH-005 — Daily goal settings](TECH-005-settings.md) | TECH-001, TECH-002, TECH-003 |
| [TECH-006 — History](TECH-006-history.md) | TECH-001, TECH-002, TECH-003 |
| [TECH-007 — End-to-end Android acceptance checks](TECH-007-acceptance.md) | TECH-001–TECH-006 |

Implementation tasks are ready to begin once their dependencies are complete; end-to-end checks follow their completion. Dependencies define integration order and do not prevent preparation of independent parts.

## Specification references

- **HIS-006 and SET-007:** product.md defines all four days in the history example as past dates and requires updates to the current day's goal.
- **HIS-002 — Calendar:** Dates display progress circles without numeric progress labels. Numeric information for the selected date appears below the calendar.
- **HIS-002 — Selected day details:** Intake, goal, and percentage remain below the calendar, as specified in HIS-002.
- **HIS-002 — Percentage:** The selected day's actual percentage appears below the calendar, rounded to an integer without capping at 100%. For example, 2100/2000 is 105%; the circle remains fully filled. There are no remaining open questions about history.

The identifier `DAT-004` is preserved as written in the source specification. These tasks do not change product requirements. User-facing behavior for write failures and corrupted data, and Android Back behavior in the Add dialog, remain unspecified. TECH-001 requires atomic persistence for goal changes without defining an error message or recovery UI.
