# Paddle Billing integration architecture

Use this checklist while working in the user's actual repository. Choose names, database columns, and framework patterns from the project rather than imposing a starter template.

## Establish scope

1. Confirm the integration targets Paddle Billing. Paddle Classic needs a migration or explicitly Classic-specific plan; do not apply Billing examples to it.
2. Inspect the app framework, authentication, persistence, background jobs, billing UI, and existing payment integration before proposing changes.
3. Separate decisions the user must make (plans, access rules, cancellation policy, tax/proration expectations) from implementation details that can be inferred from the code.
4. Use sandbox for development and tests. Treat production as a separate environment with separate credentials, identifiers, notification destinations, and approvals.

## Keep responsibilities clear

- The client renders checkout and uses only credentials Paddle documents as safe for client use.
- The application server owns secrets, customer ownership checks, subscription changes, portal-session creation, and webhook signature verification.
- The database stores only the Paddle identifiers and state needed by the application. Keep an explicit mapping between the authenticated application user and the Paddle customer/subscription; never trust a browser-supplied customer ID as authorization.
- Webhooks reconcile durable billing state. Browser return events can improve the interface but should not independently grant durable access.
- Entitlements are application policy derived from synchronized billing state. Keep the policy explicit, testable, and consistent for upgrades, grace periods, pauses, and cancellation.

## Verify before implementing API details

For exact SDK initialization, checkout event names, webhook signatures, event payloads, subscription update fields, proration behavior, or portal URLs, consult the current Paddle source listed in [official-sources.md](official-sources.md) or a connected Paddle docs MCP. If current documentation is unavailable, state the limitation and avoid inventing a field, event, method, or default.
