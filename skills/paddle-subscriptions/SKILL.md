---
name: paddle-subscriptions
description: Implement or debug Paddle Billing subscription synchronization, application entitlements, authenticated customer self-service, and subscription lifecycle behavior.
---

# Synchronize subscriptions and entitlements

Use this skill for subscription lifecycle code, database synchronization, feature gating, customer billing settings, or server-side subscription changes.

1. Inspect the current auth model, database schema, webhook route, and entitlement checks. Reuse the app's user/customer mapping and migration conventions.
2. Identify which billing states the product needs to represent and what access means during trial, payment failure, pause, scheduled change, and cancellation. Ask when policy is missing; do not invent a grace period or access rule.
3. Consult current Paddle documentation for status semantics, event contracts, portal sessions, and update/proration fields. Use [official-sources.md](../../references/official-sources.md); don't rely on remembered SDK signatures.
4. Treat verified webhooks and server-side Paddle reads as billing evidence. Make event application replay-safe, preserve the current state model, and avoid granting durable access from checkout redirects alone.
5. For a customer portal, create the session server-side only after authenticating the user and checking ownership of the mapped Paddle customer. Do not expose a privileged session URL to another customer.
6. For a code-only change, do not require account access. For account reads or mutations, use only the MCP connected to the environment the user named. A live mutation needs clear live intent; a destructive live action needs a precise target and confirmation immediately before the call. Follow [paddle-account-access.md](../../references/paddle-account-access.md) if a tool is missing.
7. Verify the affected paths with the repository's relevant checks and sandbox scenarios. Report migration impact, state transitions, and any states that remain untested.
