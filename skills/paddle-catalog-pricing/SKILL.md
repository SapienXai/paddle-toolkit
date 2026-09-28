---
name: paddle-catalog-pricing
description: Design Paddle Billing products, prices, pricing tiers, and localized pricing pages, or create catalog resources when the user explicitly requests a Paddle account action. Do not use for non-Paddle billing catalogs.
---

# Design Paddle catalog and pricing

Use this skill for plan structure, product/price modeling, pricing-page behavior, or an explicitly requested account-side catalog operation.

1. Check whether the prompt or repository identifies Paddle Classic. If Classic appears and a Billing migration is not explicit, pause and ask whether to keep Classic-specific work, which this plugin does not cover, or migrate to Paddle Billing.
2. Inspect the current app and catalog references. Ask for missing business decisions that affect the result: plan names, included features, billing interval, currencies, trial or discount rules, and whether localization is needed. Do not invent commercial terms.
3. Distinguish product/price design from account mutation. For code or a proposal, work from the repository and clearly label assumptions. For an account action, require the user to name sandbox or live and the exact requested resources.
4. Consult current Paddle docs before using product/price fields, localization calls, or preview behavior. Start with [official-sources.md](../../references/official-sources.md); do not rely on remembered field names or SDK signatures.
5. Keep public pricing display, Paddle price identifiers, checkout inputs, and server-side entitlement policy aligned. Do not trust a browser-supplied price or customer identifier for authorization.
6. Prefer sandbox for test resources. Never send a sandbox request to live. A live create/update requires explicit live intent, exact values, and a direct Paddle live connection. Before an archive, deletion, or other hard-to-reverse live change, summarize the target and effect and wait for clear confirmation.
7. If the needed sandbox or live MCP tool is absent, follow [paddle-account-access.md](../../references/paddle-account-access.md). Never ask for an API key in chat, embed it in code, or claim that a product or price was created without a successful tool result.

When presenting a catalog, return a compact table of each proposed product, price, interval, currency, and user-provided versus assumed decisions. When implementing a pricing page, follow the application's existing UI and consult current docs for localized price display.
