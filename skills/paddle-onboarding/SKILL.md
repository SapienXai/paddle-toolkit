---
name: paddle-onboarding
description: Plan or begin a Paddle Billing integration in an existing application, including architecture, project discovery, and the implementation sequence. Do not use for unrelated payment work or assume Paddle Classic is Paddle Billing.
---

# Onboard a Paddle Billing project

Use this skill when the user wants Paddle Billing added to a codebase, asks for an integration plan, or needs the shape of an existing Paddle integration explained.

1. Inspect the repository before proposing a design. Identify the framework, authentication, persistence, background jobs, current billing flow, and existing conventions. Summarize relevant files and reuse working patterns.
2. Confirm whether the target is Paddle Billing. If the repository or prompt indicates Paddle Classic, pause before applying Billing-specific APIs and ask whether the user wants a Billing migration or Classic-specific work, which this plugin does not cover.
3. Map the end-to-end flow for this app: catalog and price identifiers, checkout, webhook verification and processing, customer/subscription persistence, entitlement rules, customer self-service, sandbox tests, and production cutover. Mark which parts already exist.
4. Ask only for decisions that change the implementation, such as plan design, access policy during past-due/cancellation states, or whether the user requests an account-side catalog change. State reasonable assumptions for reversible code work and keep moving.
5. Consult current Paddle documentation for exact SDK calls, fields, events, and defaults. Use [official-sources.md](../../references/official-sources.md) and [integration-architecture.md](../../references/integration-architecture.md). If current documentation cannot be checked, say so and do not invent API behavior.
6. Make development sandbox-first. Keep client-safe configuration separate from server secrets, keep sandbox and live identifiers distinct, and never add a secret to source, chat, or logs.
7. Code-only work does not need Paddle account access. If the user asks for account-side work, use only the explicitly named environment through the user's direct Paddle MCP connection. If it is missing, follow [paddle-account-access.md](../../references/paddle-account-access.md); do not claim an account change succeeded.

Return a project-specific plan or implementation with the verification performed, assumptions, and any decisions the user still needs to make.
