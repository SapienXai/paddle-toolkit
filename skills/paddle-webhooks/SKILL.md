---
name: paddle-webhooks
description: Implement, review, or debug Paddle Billing webhook signature verification, event handling, retries, and state reconciliation. Do not use for unrelated webhook providers.
---

# Build secure Paddle webhooks

Use this skill when adding or diagnosing a Paddle Billing notification destination or webhook handler.

1. Inspect the framework's request-body handling, current route, persistence, queue/job patterns, and existing event processing before editing.
2. Consult current Paddle documentation for signature format, SDK verifier, event payloads, retries, and response requirements. Use [official-sources.md](../../references/official-sources.md); never invent a signature header, event name, or payload field.
3. Verify the signature against the exact raw request bytes with Paddle's current documented verifier before trusting or parsing event data. Do not disable verification or substitute a hand-rolled check to make a failing test pass.
4. Make processing idempotent using a durable event or domain key consistent with the current Paddle contract. Design for retries and out-of-order delivery; acknowledge promptly and use the app's existing queue for slow work when appropriate.
5. Reconcile customer and subscription state using the project's authenticated ownership mapping. Avoid logging signing secrets or unnecessary customer payloads.
6. Test valid, invalid-signature, duplicate, retry, and relevant out-of-order scenarios in sandbox. Keep the webhook secret local and separate from API credentials; never ask the user to paste it in chat.
7. If a request also requires creating a notification destination in a Paddle account, use only the explicitly named environment through its direct MCP connection. If that tool is missing, explain the setup path in [paddle-account-access.md](../../references/paddle-account-access.md) and do not claim the destination exists.

Report the exact verification and replay behavior, including any paths that remain untested.
