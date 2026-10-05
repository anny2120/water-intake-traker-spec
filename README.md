# Water Intake Tracker specification

This repository defines the product requirements and implementation tasks for
Water Intake Tracker, an Android application for recording daily water intake,
monitoring progress toward a configurable daily goal, and reviewing history.

## Project status

Early development. Implementation begins with TECH-000.

## Current scope

The first version targets Android only and works entirely locally on the device.
It requires no account, authentication, backend API, server, or cloud
synchronization. Settings and water intake history are persisted locally.

## Documentation

- [Product requirements](docs/product.md)
- [Implementation tasks and dependencies](tasks/README.md)
- [Future roadmap](docs/roadmap.md)

## Architecture ownership

Architecture documentation and architectural decision records are defined and
maintained in separate implementation repositories. This repository owns product
behavior and system-level specifications; tasks reference the architectural
decisions applicable to their implementation.

For Android, see the [architecture documentation](../android/docs/architecture.md)
and [ADR-001 — Mobile application stack](../android/adr/0001-app-stack.md) in the
Android repository. The selected stack is React Native, TypeScript, Expo, and
SQLite accessed through `expo-sqlite`.

## Development and validation

Implementation code, setup instructions, and build and test commands belong in
the Android repository. [TECH-000](tasks/TECH-000-bootstrap-android.md) establishes
that foundation and documents the environment needed to build and run the app.

The native Android project is generated before building and is excluded from
version control. Automated tests are written in TypeScript. Acceptance requires
installing and launching a locally built debug APK on an Android emulator;
[TECH-007](tasks/TECH-007-acceptance.md) defines end-to-end feature checks.

The current version requires no server deployment. Account and cloud features
appear only in the future roadmap.
