---
name: paddle-checkout
description: Implement or review Paddle Billing checkout in a web application, including the repository's client/server boundary and post-checkout flow. Do not use for unrelated checkout providers.
---

# Implement Paddle Checkout

Use this skill when the user asks to add, change, or debug Paddle Billing checkout code.

1. Inspect the actual app router/framework, authentication, pricing UI, and any existing Paddle.js setup. Follow local conventions and avoid replacing unrelated billing code.
2. Confirm the checkout shape the project needs (for example, existing price selection, customer context, or inline/overlay experience). Ask only for choices that materially change the implementation.
3. Check current Paddle docs for the exact Paddle.js initialization, checkout options, events, and SDK usage. Use [official-sources.md](../../references/official-sources.md). Do not guess event names, product fields, or framework APIs.
4. Keep secret server credentials on the server. Use a client token only in the places Paddle documents as client-safe. Create transactions or perform other server-side operations using the app's trusted user/session context; never authorize with a browser-provided customer ID alone.
5. Keep checkout presentation separate from durable billing state. Use the verified webhook/synchronization path for completed payment and entitlement decisions; use client events only for user experience.
6. Keep development sandbox-first, with explicit environment selection and environment-specific identifiers. If the user asks to create or inspect account resources, use a direct MCP tool only when connected to the named environment. If unavailable, explain the connection path in [paddle-account-access.md](../../references/paddle-account-access.md) and continue code-only work where possible.
7. Report the changed files, how the flow behaves, and which checkout or webhook paths were actually verified. Never claim a live account action without a successful Paddle tool result.
