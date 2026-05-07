---
name: mobile-api-integration
description: Integrate React Native / Expo apps with existing backend APIs using a typed client, auth headers, refresh-token handling, feature-level query/mutation hooks, normalized errors, pagination, upload flows, and offline-aware caching. Use when connecting app features to REST/HTTP APIs or refactoring API access.
---

# Mobile API Integration

Use this skill when the app already has a backend API or needs a stable integration layer.

## Default architecture

Keep API code in 2 layers:

1. **shared client layer**
   - base URL
   - auth header injection
   - refresh / retry policy
   - request timeout / cancellation
   - normalized errors
   - upload helpers

2. **feature API layer**
   - one `api.ts` per feature
   - typed query/mutation hooks
   - query keys
   - feature DTO ↔ app model mapping

Prefer a structure like:

```text
src/
  lib/
    api-client.ts
    query-client.ts
    api-errors.ts
  features/
    users/api.ts
    orders/api.ts
    profile/api.ts
```

## Defaults

- Use one shared typed HTTP client boundary.
- Use TanStack Query for server state.
- Keep request/response schemas near the feature.
- Validate suspicious or unstable payloads with Zod when useful.
- Do not call the HTTP client directly from screen components.

## Auth integration

When the API needs authentication:

- inject bearer token in one place
- keep refresh-token logic centralized
- prevent duplicate concurrent refresh calls
- clear session and cached sensitive data on unrecoverable auth failure
- ensure query/mutation retries do not hide auth expiry bugs

## Error normalization

Map transport/backend errors into a predictable app shape.

At minimum normalize:

- network unavailable
- timeout
- unauthorized / expired session
- forbidden
- validation error
- not found
- rate limit
- unknown server error

UI should not parse raw backend payloads everywhere.

## Query + mutation rules

### Queries
- stable query keys
- feature-owned hooks
- select/transform data close to the hook when practical
- tune stale time intentionally
- support pull-to-refresh and empty/error states

### Mutations
- decide invalidate vs optimistic update explicitly
- expose pending state to disable double-submit
- map success/error feedback clearly
- rollback optimistic state safely

## Pagination, filters, search

For list endpoints:

- standardize query params
- keep filter objects serializable for query keys
- separate list query keys from detail query keys
- define reset behavior when filters/search change
- document cursor vs page-number assumptions

## Upload/download flows

For file or image upload:

- separate file picking from upload request logic
- send content type intentionally
- show progress or at least pending state for large uploads
- handle partial failure and retry copy
- verify auth + size limit errors surface cleanly

## Model mapping

Do not leak backend DTO shape everywhere.

Prefer:
- raw response type/schema
- mapper to app domain model
- hook returns mapped model used by screens

This keeps backend changes contained.

## Minimal done checklist

Before calling API integration done, verify:

- client boundary exists and is reused
- auth headers work
- refresh flow is either implemented or explicitly not needed
- query keys are stable
- loading/empty/error states render
- mutation failure path tested
- pagination/filter/search behavior is defined when relevant
- upload flow tested if present
