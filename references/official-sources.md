# Official source index

Use these primary sources when a task needs current Paddle or OpenAI behavior. Read the page relevant to the task; do not infer API fields or SDK calls from this index.

## OpenAI plugin and skill format

- [Build skills](https://developers.openai.com/plugins/build/skills) — skill structure and supported `agents/openai.yaml` MCP dependencies.
- [Package your plugin](https://developers.openai.com/plugins/build/plugins) — portable root `plugin.json`, `extensions.com.openai`, assets, and local marketplace workflow.
- [Submit plugins](https://developers.openai.com/plugins/deploy/submission) — submission types, publisher identity, prompts, test cases, and review flow.
- [Plugin submission errors](https://developers.openai.com/plugins/deploy/submission-errors) — exact field, URL, asset, image, and submission limits.
- [Authenticate users](https://developers.openai.com/plugins/build/auth) — OAuth and user authorization requirements for MCP integrations.
- [Connect and test your plugin](https://developers.openai.com/plugins/deploy/connect-chatgpt) — local installation and workflow testing.

## Paddle Billing and MCP

- [Paddle Developer Docs](https://developer.paddle.com/) — current Billing guides, API reference, and SDK documentation.
- [Build with AI tools](https://developer.paddle.com/get-started/ai/) — Paddle docs MCP, account MCP, and agent skills.
- [Paddle MCP server](https://developer.paddle.com/sdks/ai/paddle-mcp/) — live and sandbox endpoints, authentication, permissions, and client setup.
- [Paddle docs MCP server](https://developer.paddle.com/sdks/ai/docs-mcp/) — current docs MCP host, authentication, and setup.
- [Paddle live MCP OAuth](https://developer.paddle.com/changelog/2026/paddle-mcp-oauth/) — live OAuth support and environment split.
- [Paddle agent skills](https://github.com/PaddleHQ/paddle-agent-skills) — upstream integration skills and workflow reference.
- [Upstream Apache-2.0 license](https://github.com/PaddleHQ/paddle-agent-skills/blob/main/LICENSE) — licensing for any material derived from that repository.

## Working rule

Prefer current official Paddle documentation or the connected Paddle docs MCP for implementation details. Paddle's MCP servers perform account operations; the docs MCP searches documentation. Keep those roles separate.
