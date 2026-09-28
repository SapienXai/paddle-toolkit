# Paddle Toolkit

**Paddle billing workflows from SapienX.** Build, test, debug, and operate Paddle Billing integrations with focused skills for ChatGPT and Codex.

Paddle Toolkit packages developer guidance and workflow orchestration. It does not provide a billing backend, proxy Paddle API, or store Paddle credentials. It is independently published by **SapienX** and is not affiliated with or endorsed by Paddle.

## What it helps with

- Plan Paddle Billing architecture for an existing application.
- Design products, prices, and pricing pages.
- Implement checkout and secure webhook handling.
- Synchronize subscriptions and build entitlements or customer self-service.
- Test against Paddle sandbox and prepare a production-readiness review.
- Debug an existing integration from repository evidence and current Paddle documentation.
- Connect to Paddle's live MCP directly with Paddle OAuth when a live account action is requested.

## Install

After approval and publication, find **Paddle Toolkit** in the shared Plugins Directory for ChatGPT or Codex and install it there.

For local development in Codex, add the repository as a plugin marketplace, then install Paddle Toolkit from the local Plugins Directory:

```sh
codex plugin marketplace add SapienXai/paddle-toolkit
codex plugin add paddle-toolkit@paddle-toolkit-local
```

The repository also includes `.agents/plugins/marketplace.json` for the local plugin workflow described in the [OpenAI plugin packaging guide](https://developers.openai.com/plugins/build/plugins).

## Use it

Start with a concrete goal, for example:

- “Add Paddle Billing to this Next.js SaaS. Inspect the app first and propose a sandbox-first implementation.”
- “Implement Paddle Checkout using the current Paddle docs and the conventions already in this repository.”
- “Verify our Paddle webhook signature and make duplicate deliveries safe.”
- “Create Starter, Pro, and Business products in my Paddle sandbox.”
- “Audit this Paddle integration before production and give me a prioritized fix list.”
- “Why is this subscription not updating after checkout?”

The skills work on repository and code tasks without Paddle account access. They inspect the actual project, identify missing decisions, and check current Paddle documentation before relying on API or SDK details.

## Included skills

| Skill | Use it for |
|---|---|
| `paddle-onboarding` | Project discovery and integration architecture |
| `paddle-catalog-pricing` | Catalog modeling, pricing, and localization |
| `paddle-checkout` | Web checkout implementation |
| `paddle-webhooks` | Signature verification and event processing |
| `paddle-subscriptions` | Subscription sync, entitlements, and customer portal |
| `paddle-sandbox-testing` | Sandbox setup and end-to-end verification |
| `paddle-production-audit-debug` | Integration diagnosis and release readiness |
| `paddle-live-operations` | Paddle live account access through Paddle's MCP and OAuth |

## Paddle MCP and account access

Account tools connect directly to Paddle. SapienX does not receive Paddle credentials or relay account requests.

- **Live:** the `paddle-live-operations` skill declares a supported MCP dependency on Paddle's `https://mcp.paddle.com/mcp` endpoint. On first use, the client can offer Paddle's OAuth flow. Access is governed by the connected Paddle user's permissions. The skill never silently switches a sandbox request to live.
- **Sandbox:** Paddle's `https://sandbox-mcp.paddle.com/mcp` endpoint currently authenticates with a sandbox API key and does not support OAuth. Use an existing official sandbox connection or configure it through the MCP client's secure credential mechanism, following [Paddle's MCP setup guide](https://developer.paddle.com/sdks/ai/paddle-mcp/). The skill does not request the key in chat or package it in this repository.
- **Documentation:** Paddle's docs MCP is hosted by Kapa.ai at `https://paddlehq.mcp.kapa.ai` and requires Google or GitHub sign-in for rate limiting. It is optional; code workflows can use Paddle's public developer documentation directly. See [Paddle's docs MCP guide](https://developer.paddle.com/sdks/ai/docs-mcp/).

If the required server is not connected, the skill explains the direct official connection path and stops before claiming an account action succeeded. It never routes a live request to sandbox or a sandbox request to live. Before a consequential or destructive live action, it summarizes the exact target and effect and requires clear authorization.

## Security

- Development and test workflows default to sandbox.
- Never paste Paddle API keys or webhook secrets into chat, source code, screenshots, or commits. Keep secrets in the runtime's protected environment or credential store.
- Keep Paddle server-side API keys on the server. Treat client-side tokens as public configuration only where Paddle documents that use.
- Verify webhook signatures with Paddle's current SDK or documented verifier. Do not disable verification to make a test pass.
- Make webhook processing idempotent and authorize customer-owned subscription operations on the server.
- Treat browser redirects as presentation, not authoritative proof that a payment or entitlement is complete.
- Do not create, change, archive, or cancel live billing resources without explicit live intent and enough detail to identify the exact resource and effect.
- Do not claim that a Paddle tool ran unless its result confirms the action.

## Troubleshooting

- **Stale or uncertain API details:** consult the current Paddle docs MCP if connected, or follow the links in [the source index](references/official-sources.md). Do not invent fields or SDK methods.
- **Sandbox authentication fails:** confirm that the endpoint is the sandbox endpoint and the configured credential is a sandbox key. Keep it out of chat and files.
- **Live MCP is unavailable:** use the Paddle OAuth connection flow from the official live endpoint. Do not substitute an API key in chat or silently use sandbox.
- **No account tool is connected:** code-only workflows can still proceed; account operations must wait for the user's direct Paddle connection.
- **Paddle Classic project:** these skills target Paddle Billing. Confirm whether the user wants a migration plan before applying Billing-specific code.

## Publisher, support, and licensing

Publisher: **SapienX** · Website: [sapienx.app](https://sapienx.app/) · Support: [GitHub Issues](https://github.com/SapienXai/paddle-toolkit/issues)

Privacy: [Paddle Toolkit Privacy Policy](https://sapienx.app/paddle-toolkit/privacy-policy/). The plugin package contains skills and no SapienX backend; ChatGPT/Codex and any directly connected Paddle or optional documentation MCP process requests under their own privacy terms.

Paddle Toolkit is licensed under Apache-2.0. The upstream `PaddleHQ/paddle-agent-skills` project is also Apache-2.0; its license and attribution are preserved in [licenses/](licenses/) and [NOTICE](NOTICE). Paddle's product names are used only to identify the integration target.

This is a skills-only package. Its published listing supplies the existing SapienX website and repository issue tracker, plus a Paddle Toolkit-specific privacy policy. Terms of service are omitted because this plugin does not operate a separate service or backend.
