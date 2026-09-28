---
name: paddle-sandbox-testing
description: Verify a Paddle Billing integration in sandbox with realistic checkout, webhook, and subscription lifecycle scenarios before a production rollout.
---

# Test a Paddle Billing integration in sandbox

Use this skill to plan or run tests against Paddle sandbox. Do not use it to exercise real customer data or to switch an unqualified request to live.

1. Inspect the application's environment selection, checkout configuration, webhook verifier, persistence, and test setup. Confirm the app is explicitly configured for Paddle sandbox before invoking any account tool.
2. Consult current Paddle documentation for sandbox credentials, test cards, webhook simulator behavior, and any test-specific caveats. Use [official-sources.md](../../references/official-sources.md); do not hard-code stale card numbers or assume sandbox and live resources are shared.
3. Cover the app's actual critical paths: successful checkout, rejected/failed payment where relevant, signed webhook delivery, invalid signature rejection, duplicate/retried delivery, subscription-state sync, entitlement change, and customer ownership checks.
4. Use Paddle's direct sandbox MCP only if it is connected and the user asks for account-side test setup. If absent, explain the direct client setup in [paddle-account-access.md](../../references/paddle-account-access.md). Sandbox access uses a key; never request it in chat, put it in a command, or add it to a file.
5. Keep every tool call and identifier in sandbox. Never use the live MCP as a substitute. Stop if environment identity is unclear.
6. Run the repository's relevant tests and record concrete results. Separate executed scenarios from suggested manual checks. Never say a checkout, event, or resource was tested unless evidence confirms it.

Finish with a scenario table showing expected behavior, evidence, pass/fail, and unresolved gaps. Do not recommend production cutover while signature verification, environment separation, or entitlement-critical paths are failing.
