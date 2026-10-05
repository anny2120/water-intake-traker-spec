# TECH-000 — Bootstrap Android application

Status: ready for implementation.
Source: Scope (Android-only, entirely local application).
Architecture: [architecture.md](../../android/docs/architecture.md), [ADR-001 — Mobile application stack](../../android/adr/0001-app-stack.md).
Dependencies: none.

## Work

Create the Android application project using the stack selected in ADR-001: React Native as the mobile framework, TypeScript as the application language, Expo as the development toolchain, and SQLite accessed through `expo-sqlite` for persistent local storage. Configure the build and test infrastructure and define the basic project structure for UI, daily accounting, and local storage. Document configuration details outside product.md.

This task prepares the application foundation; feature behavior is covered by TECH-001–TECH-006.

Keep the application source, Expo configuration, and dependency lockfile in the repository. Generate the native Android project through Expo prebuild before building; do not commit the generated native project or its Gradle wrapper. Any configuration needed to regenerate the native project must be maintained in version-controlled application configuration or tooling.

Configure automated tests written in TypeScript. Native Android instrumentation tests are not required. Android runtime validation is performed on an emulator.

## Acceptance criteria

- The repository contains the application source and configuration required to generate the native Android project before building. The generated native project, including its Gradle wrapper, is excluded from version control.
- Native project generation and local debug APK build commands are documented and work from a clean checkout without a pre-existing native project.
- The project is configured to use React Native, TypeScript, Expo, and `expo-sqlite`, consistent with ADR-001.
- The stack configuration, Android SDK configuration, and basic project structure are documented in English.
- A local debug APK build succeeds, and the resulting APK is installed and launched on an Android emulator for acceptance.
- Automated tests written in TypeScript are configured, with documented commands and a minimal smoke check that verifies the test infrastructure runs.
- The project provides locations for UI, daily accounting, and storage code without requiring a server, account, or cloud service.

## Validation

From a clean checkout, install dependencies, generate the native Android project, and run the documented local debug APK build and TypeScript test commands. Install the resulting APK on an Android emulator and verify that the application launches successfully. Record the build and test environment, emulator configuration (including Android API level), commands, and results. Verify that generated native files are excluded from version control. An emulator launch check is required in addition to passing TypeScript tests.
