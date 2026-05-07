---
name: mobile-auth-state
description: Design and implement authentication, session persistence, secure token storage, and auth-gated navigation for React Native / Expo apps. Use when building login, logout, signup, refresh-token flows, protected routes, or persisted user/session state.
---

# Mobile Auth State

## Goals

Build auth that survives relaunches, protects sensitive tokens, and keeps navigation state predictable.

## Defaults

- Use Zustand or a thin auth store for client session state.
- Persist secrets with SecureStore or an approved secure wrapper.
- Keep refresh logic in one place.
- Let route guards depend on a resolved auth bootstrap state, not a guessed initial value.

## Flow shape

1. Bootstrap auth state on app start.
2. Read persisted credentials securely.
3. Validate/refresh if needed.
4. Expose one of: `loading`, `authenticated`, `anonymous`.
5. Route accordingly.

## Rules

- Never store raw tokens in plain AsyncStorage.
- Separate `session loading` from `logged out`.
- Handle expired refresh tokens as a first-class case.
- Clear persisted state on logout and auth failure.
- Keep API client auth headers in sync with store updates.

## Minimum states

- bootstrap/loading
- signed out
- signing in
- signed in
- refreshing
- auth error

## Edge cases

- app relaunch during expired session
- logout from deep nested screen
- two concurrent refresh attempts
- offline launch with stale token
- partially restored user profile
