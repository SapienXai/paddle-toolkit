---
name: paddle-production-audit-debug
description: Audit an existing Paddle Billing integration for release readiness or diagnose a concrete checkout, webhook, or subscription incident from repository and runtime evidence.
---

# Audit or diagnose a Paddle integration

Use this skill when the user asks why an existing Paddle Billing flow is failing or wants a production-readiness review. For routine feature implementation, use the focused integration skill.

1. Inspect the relevant source, configuration shape, tests, and user-provided error/log excerpt. Do not expose or repeat secrets or unnecessary customer data from logs.
2. Establish which environment and event/resource are involved. If the evidence is incomplete, ask a focused question; do not infer that sandbox and live IDs, webhook destinations, or credentials match.
3. Verify current Paddle behavior against the relevant source in [official-sources.md](../../references/official-sources.md). Trace from the failing request or event through signature verification, persistence, ownership mapping, and entitlement logic.
4. For an audit, use [production-review.md](../../references/production-review.md). Cite each finding to a concrete file or observed behavior and label severity, impact, and proposed fix. Distinguish confirmed blockers from assumptions.
5. Use a connected Paddle MCP only when account state is needed and the user clearly names the environment. For live account inspection or action, use the separate `paddle-live-operations` workflow. If the required MCP is absent, explain the direct connection path from [paddle-account-access.md](../../references/paddle-account-access.md); do not pretend to have inspected the account.
6. Do not mutate live billing resources while diagnosing. For any requested hard-to-reverse live action, first summarize the exact target and consequence and wait for clear confirmation immediately before calling the tool.

Return the most likely cause first, the evidence, the smallest safe remediation, and what was or was not verified. Do not call an integration production-ready when a critical path remains unverified.
