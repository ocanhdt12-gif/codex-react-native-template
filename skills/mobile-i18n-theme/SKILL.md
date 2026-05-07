---
name: mobile-i18n-theme
description: Add localization, theme tokens, dark mode behavior, and consistent design primitives for React Native / Expo apps. Use when introducing multi-language UI, app-wide theming, theme persistence, copy structure, or reusable visual tokens.
---

# Mobile i18n + Theme

## Localization rules

- Keep user-facing copy out of screen logic when practical.
- Namespace translation keys by feature.
- Avoid string interpolation patterns that break grammar across languages.
- Test long strings and empty translations on small screens.

## Theme rules

- Centralize color, spacing, typography, and semantic tokens.
- Prefer semantic names (`surface`, `text-muted`, `danger`) over raw palette names in feature code.
- Persist theme choice only if product needs override beyond system theme.
- Verify contrast in both light and dark mode.

## Mobile-specific checks

- notched devices
- font scaling / accessibility text size
- RTL if the product may need it later
- truncation in tab bars, buttons, and modals

## Done means

- at least one non-default locale path still renders correctly
- theme switch does not cause unreadable states
- shared components consume tokens consistently
