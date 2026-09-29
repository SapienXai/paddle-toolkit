---
name: paddle-live-operations
description: Read or act on a user's Paddle live account when the request explicitly names live, production, or real customer data. Use the direct Paddle OAuth MCP connection; never use this for sandbox or code-only work.
---

# Use Paddle live account tools

This skill is only for explicit live account requests. The MCP server is Paddle's service at `https://mcp.paddle.com/mcp`; Paddle Toolkit and Kazım Akgül do not proxy the request or receive account credentials.

1. Check whether the prompt or repository identifies Paddle Classic. If Classic appears and a Billing migration is not explicit, pause and ask whether to keep Classic-specific work, which this plugin does not cover, or migrate to Paddle Billing.
2. Confirm the request clearly refers to Paddle live/production or real customer data. If the environment is unclear, ask before accessing account tools. Never infer live intent from urgency or from an absent sandbox connection.
3. Use the declared `paddle-live` dependency. On first use, allow the supported Paddle OAuth connection flow to authenticate directly with Paddle. Never ask the user to paste a key or OAuth code into chat. If the connection is missing or fails, explain the native connection step and stop before the account action.
4. Use the current Paddle docs MCP if already connected when exact API or account behavior needs clarification. Otherwise consult the current official Paddle documentation from [official-sources.md](../../references/official-sources.md); do not invent tool names, fields, permissions, or outcomes.
5. Read or preview the requested account state first when the tools support it. Keep every call scoped to the exact object and user request. Surface warnings and errors. Do not blindly retry a write after a timeout or ambiguous result.
6. Before a live create or update, verify the explicit live intent and exact object/value requested. Before a destructive or hard-to-reverse action, summarize the account, target, and effect and wait for clear confirmation immediately before the call.
7. If the user asks for sandbox work, do not call `paddle-live`. Explain that Paddle's sandbox MCP uses a separate API key and does not support OAuth; follow [paddle-account-access.md](../../references/paddle-account-access.md) for the direct sandbox setup path.
8. Report the exact tool result and environment. Never claim that a resource changed unless a successful live tool result confirms it.
