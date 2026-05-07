---
name: mobile-testing-release
description: Test and release React Native / Expo apps with a practical pyramid: unit tests, integration checks, device verification, and mobile E2E smoke coverage. Use when adding tests, validating a feature before merge, preparing internal builds, or deciding release readiness.
---

# Mobile Testing + Release

## Test pyramid

- Unit: hooks, utilities, reducers, mappers
- Integration: screen behavior, form flows, query/mutation behavior
- E2E smoke: onboarding, auth, core CRUD, logout, one risky device flow

## Defaults

- Jest + React Native Testing Library for unit/integration
- Maestro for pragmatic mobile E2E smoke tests
- Manual device checklist for permissions, notifications, camera, biometrics, or background cases

## Before saying “done”

Check:

- tests added or updated where the behavior changed
- happy path verified on simulator/emulator
- at least one failure path verified
- loading/empty/error states still render
- navigation still works after success and failure

## Release gate

Before internal or production release:

1. run unit/integration tests
2. run smoke E2E flows
3. verify environment/build profile
4. verify app icon/name/version/build number changes if relevant
5. verify crash/monitoring hooks are active
6. note remaining manual QA risks
