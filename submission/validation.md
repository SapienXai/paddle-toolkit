# Validation record

This file records checks required for a public skills-only submission. Replace pending entries with observed results before upload.

- [x] Validate root `plugin.json` against the Agent Plugins 1.0.0 schema and OpenAI directory limits.
- [x] Validate all eight skill manifests and their OpenAI interface/product/dependency metadata.
- [x] Check local references and declared image assets.
- [x] Check square SVG icon sizes and brand contrast requirements.
- [x] Build the SapienX site; verify the new policy in the output and live at the published URL.
- [x] Build and scan the final skills-only ZIP; 27 entries, eight skills, 30,391 bytes, secret-pattern scan clean.
- [x] Add and install the local marketplace plugin with the Codex CLI.
- [ ] Run all five positive and three negative activation cases in `test-cases.md`; P1 and N2 were exercised locally, while the rest remain unrun.
- [ ] Run the additional missing-MCP, sandbox/live, destructive-action, and secret-handling cases in `boundary-tests.md`.
- [ ] Record portal validation, publisher identity, submission ID, and review status in `portal-status.md`.

Local Codex note: The install succeeded and the P1 plan case loaded the relevant skill instructions. Codex CLI 0.158.0-alpha.2.1 logged that its `policy.products` parser expects `CHATGPT` where OpenAI's current plugin submission errors require `CHAT`. N2 did not load Paddle skill instructions. No Paddle account tool was connected, so no account-side case was run.
