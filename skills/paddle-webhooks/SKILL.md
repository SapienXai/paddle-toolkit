---
name: paddle-webhooks
description: Implement, review, or debug Paddle Billing webhook signature verification, event handling, retries, and state reconciliation. Do not use for unrelated webhook providers.
---

# Build secure Paddle webhooks

Use this skill when adding or diagnosing a Paddle Billing notification destination or webhook handler.

1. Check whether the prompt or repository identifies Paddle Classic. If Classic appears and a Billing migration is not explicit, pause and ask whether to keep Classic-specific work, which this plugin does not cover, or migrate to Paddle Billing.
2. Inspect the framework's request-body handling, current route, persistence, queue/job patterns, and existing event processing before editing.
3. Consult current Paddle documentation for signature format, SDK verifier, event payloads, retries, and response requirements. Use [official-sources.md](../../references/official-sources.md); never invent a signature header, event name, or payload field.
4. Preserve the exact raw request bytes and verify them before parsing event data. Prefer Paddle's official SDK verifier when one exists for the project's language. If no SDK is available, follow Paddle's manual verification example exactly, including its five-second timestamp tolerance, supported signature rotation, and constant-time comparison; do not broaden the tolerance or recreate the signed body from parsed JSON.
5. Make processing idempotent using a durable event or domain key consistent with the current Paddle contract. For state projections, persist Paddle's event occurrence time or another authoritative version and compare it atomically before applying an update; an older delivery must not overwrite newer state. If the repository cannot establish ordering safely, use its reconciliation path or leave the state unchanged and report the gap. Design for retries; acknowledge promptly and use the app's existing queue for slow work when appropriate.
6. Reconcile customer and subscription state using the project's authenticated ownership mapping. Avoid logging signing secrets or unnecessary customer payloads.
7. Add focused tests for valid, invalid, stale-signature, duplicate, retry, and relevant out-of-order scenarios in the repository's existing test framework. If none exists, add a small local test using the available runtime or report why no test could run. Use Paddle sandbox only for account-side deliveries. Keep the webhook secret local and separate from API credentials; never ask the user to paste it in chat.
8. If a request also requires creating a notification destination in a Paddle account, use only the explicitly named environment through its direct MCP connection. If that tool is missing, explain the setup path in [paddle-account-access.md](../../references/paddle-account-access.md) and do not claim the destination exists.

Report the exact verification and replay behavior, including any paths that remain untested.
