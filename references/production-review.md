# Production review checklist

Review the complete flow in the repository and cite concrete files or behavior in the findings.

## Environment and credentials

- Sandbox and live configuration are separate and visibly selected; there is no silent environment fallback.
- Server-side API keys, webhook secrets, database credentials, and private customer data are not bundled in code or logs.
- Public client configuration contains only values Paddle documents as safe for client use.
- Live account access has least privilege and is connected directly to Paddle through its supported OAuth flow when available.

## Checkout and authorization

- Checkout uses current Paddle documentation and the existing framework's established patterns.
- Server operations verify the signed-in application user owns the related customer/subscription.
- Return URLs or client events do not grant durable entitlements by themselves.

## Webhooks and state

- The handler verifies the Paddle signature against the exact raw request body using a current documented verifier.
- Invalid signatures are rejected; secrets and unnecessary personal payloads are not logged.
- Delivery is idempotent, replay-safe, and tolerant of retries and out-of-order events according to the current event contract.
- Processing acknowledges promptly and moves slow work to the existing job/queue mechanism where appropriate.
- Subscription state and entitlements have explicit rules and are reconciled from trusted Paddle state.

## Evidence and launch decision

- Run the repository's relevant checks and Paddle sandbox scenarios; identify anything not actually exercised.
- Report each issue with severity, evidence, impact, and a specific fix.
- Separate confirmed blockers from assumptions and follow-up checks.
- Do not claim production readiness when signatures, ownership checks, environment separation, or critical event paths remain unverified.
