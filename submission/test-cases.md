# OpenAI Plugin Directory test cases

The current OpenAI submission guide calls for five positive and three negative cases. These are the exact cases prepared for the portal.

## Positive cases

### P1 — Add billing to an existing Next.js application

- **Prompt:** “Add Paddle Billing to this Next.js SaaS. Inspect the codebase first and propose a sandbox-first plan covering checkout, webhooks, subscription sync, and feature access.”
- **Expected behavior:** Activate onboarding and the relevant code skills; inspect the repository, reuse its architecture, identify decisions that materially affect billing policy, and consult current Paddle documentation for exact SDK/API details. No account MCP is required.
- **Expected result:** Repository-grounded implementation plan or patch, explicit assumptions, sandbox/live boundary, and verification status.
- **Fixture / account:** A small Next.js app with existing auth and database files; no Paddle account credentials required.

### P2 — Implement checkout

- **Prompt:** “Implement Paddle Checkout for the existing Starter and Pro plans using the current Paddle docs. Keep the secret on the server and use our existing login session.”
- **Expected behavior:** Activate checkout; inspect the current UI and server routes; verify current Paddle.js/API behavior; keep server credentials server-side and use authenticated application context.
- **Expected result:** Project-conventional code change, tests or checks run, and a note that browser return state alone does not grant durable entitlements.
- **Fixture / account:** Existing app checkout page and plan identifiers; no account mutation required.

### P3 — Verify webhook security

- **Prompt:** “Add a Paddle webhook route that verifies signatures and safely handles duplicate subscription events.”
- **Expected behavior:** Activate webhooks; inspect raw-body handling, current verifier, event mapping, idempotency, and queue behavior; consult current Paddle docs; do not disable verification.
- **Expected result:** Secure handler and focused validation cases for valid, invalid, stale-signature, duplicate/retry, and (where state is projected) out-of-order delivery. Older events must not overwrite newer subscription state.
- **Fixture / account:** Local route and test harness; a webhook secret may be represented by a test fixture, never requested in chat.

### P4 — Create a sandbox catalog with Paddle tooling

- **Prompt:** “Create Starter, Pro, and Business products with monthly prices in my Paddle sandbox using the connected official Paddle sandbox MCP. Do not touch live.”
- **Expected behavior:** Confirm sandbox, use only a connected official sandbox MCP, follow the user-specified catalog, and report exact tool results. If no sandbox tool is connected, explain the direct secure setup path and make no account change. Never use the declared live dependency as a substitute.
- **Expected result:** Successful tool output listing created sandbox resources, or an explicit connection-required state with no false success claim.
- **Fixture / account:** Reviewer-owned Paddle sandbox connection is needed to exercise the actual creation call. No credentials are included; without that connection, safe setup guidance is the expected result.

### P5 — Audit production readiness

- **Prompt:** “Audit this Paddle Billing integration before launch. Check signature verification, duplicate webhooks, subscription synchronization, entitlement rules, customer ownership, and sandbox/live separation.”
- **Expected behavior:** Activate the audit skill; inspect source and tests; consult current docs; tie every finding to evidence and identify unverified paths without mutating billing resources.
- **Expected result:** Prioritized findings with severity, file/behavior evidence, fixes, and a truthful go/no-go summary.
- **Fixture / account:** Sample integration repository with checkout and webhook code; no Paddle account needed unless the user separately requests a direct account read.

## Negative cases

### N1 — Unrelated Stripe work

- **Prompt:** “Add Stripe subscriptions to this Django app.”
- **Expected behavior:** Paddle Toolkit skills do not activate. Handle the Stripe request with the relevant Stripe workflow if available.
- **Why:** The task names a different billing provider.

### N2 — Unrelated React bug

- **Prompt:** “Fix the React dropdown so it closes when I click outside.”
- **Expected behavior:** Paddle Toolkit skills do not activate; solve it as ordinary frontend work.
- **Why:** No Paddle Billing behavior is involved.

### N3 — Paddle generation is unclear

- **Prompt:** “Update our Paddle checkout integration.”
- **Fixture context:** The repository README and implementation identify the existing integration as Paddle Classic.
- **Expected behavior:** Do not apply Paddle Billing instructions. Ask whether the user wants to keep a Classic-specific implementation, which this plugin does not cover, or migrate to Paddle Billing.
- **Why:** The skills target Paddle Billing and must not silently conflate the two products when the user's intent is unclear.
