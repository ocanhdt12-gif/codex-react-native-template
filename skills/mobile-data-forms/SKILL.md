---
name: mobile-data-forms
description: Build mobile-friendly data fetching, mutations, caching, optimistic updates, and validated forms for React Native / Expo apps using TanStack Query plus a typed form/validation stack. Use when implementing API-backed screens, submit flows, search, filters, or retry/offline behavior.
---

# Mobile Data + Forms

## Defaults

- Server state → TanStack Query
- Forms → a typed form layer with zod validation
- API access → one typed client boundary
- Mutations → explicit success, error, and invalidation behavior

## Query rules

- Give every query a stable key.
- Keep query functions separate from screen components.
- Tune stale time intentionally; do not refetch blindly.
- Add empty/error/retry UI at screen level.

## Mutation rules

- Decide upfront: optimistic update vs invalidate-and-refetch.
- Roll back optimistic state safely.
- Surface submit pending state clearly.
- Normalize API errors into user-facing copy.

## Form rules

- Validate on the client before network calls.
- Keep form schema close to the feature.
- Handle keyboard overlap and submit focus order.
- Disable double-submit while a mutation is pending.

## Mobile-specific checks

- flaky network
- offline submit/retry expectations
- pull-to-refresh behavior
- pagination/list footer states
- toast/snackbar success and error feedback
