# v1.0.2

Updates the plugin manifest and publisher-facing copy to Kazım Akgül and aligns the public product and privacy pages with that requested individual publisher. No Paddle integration behavior changes. The skills-only architecture, direct Paddle OAuth connection, sandbox/live separation, and Paddle non-endorsement statement remain documented.

# v1.0.1

Patch update clarifies the Paddle Classic boundary in checkout workflows so the plugin asks whether to keep a Classic-specific path or migrate to Paddle Billing before applying Billing APIs. Webhook guidance now requires the official five-second signature timestamp tolerance, exact raw bytes, and atomic ordering protection against stale event delivery. Submission test N3 now covers an ambiguous checkout request in a repository identified as Paddle Classic.

# v1.0.0

Initial Paddle Toolkit release by SapienX. Adds eight focused skills for Paddle Billing onboarding, catalog/pricing, checkout, webhooks, subscription synchronization and entitlements, sandbox testing, production audits/debugging, and direct Paddle live MCP use through OAuth. Includes the published Paddle Toolkit privacy policy. This skills-only package contains no Paddle API proxy, billing backend, or credential store.
