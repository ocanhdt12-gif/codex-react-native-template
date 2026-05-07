---
name: expo-eas-pipeline
description: Configure Expo EAS build/release pipelines, app environments, secrets, profiles, and CI handoff for React Native / Expo apps. Use when setting up internal builds, preview/production profiles, OTA strategy, signing assumptions, or GitHub Actions release automation.
---

# Expo EAS Pipeline

## Use this for

- `eas.json` structure
- dev / preview / production profiles
- env and secrets strategy
- internal distribution
- store-ready release flow
- CI automation around builds and submissions

## Profile defaults

- `development` for local dev client work
- `preview` for QA/internal distribution
- `production` for store-ready builds

## Rules

- Keep environment names aligned across app config, CI, and backend.
- Separate public env vars from secret values.
- Document where each secret lives.
- Treat versioning/build numbers as release work, not an afterthought.
- Avoid release steps that only exist in someone’s memory.

## CI expectations

- typecheck/lint/test before expensive builds
- build profile selected intentionally
- artifact destination clear
- failure output discoverable

## OTA / updates

- Decide early whether a change is OTA-safe or requires a binary rebuild.
- Do not assume every JS change can ship safely without checking native/plugin impact.

## Recommended flow

- local simulator/emulator for fast dev feedback
- GitHub Actions quality gate on PR/push
- EAS preview build on `develop`
- manual EAS production build from `main`/release state

## Required secrets

At minimum document `EXPO_TOKEN`.
If the app needs third-party services, list release-critical secrets explicitly instead of assuming they exist.
