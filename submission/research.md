# Standards and upstream research

Research checked on 2026-09-29 against current primary documentation.

## OpenAI

- Portable Agent Plugins packages use a root `plugin.json` with schema `https://agent-plugins.org/schemas/1.0.0/plugin.schema.json`; skills live in root `skills/`; OpenAI-specific listing metadata belongs under `extensions.com.openai.interface`.
- OpenAI documents MCP dependencies for skills in `skills/<name>/agents/openai.yaml` under `dependencies.tools`, including an external Streamable HTTP URL. That confirms a public skills-only package can declare an external MCP dependency using the native mechanism.
- The skill dependency carries workflow tool availability; it is not a proxy or bundled MCP implementation. OpenAI's MCP authentication guidance calls for OAuth 2.1 for authenticated user data/actions and requires the server to enforce its own authorization.
- Current submission documentation requires a verified developer/business identity, five positive and three negative test cases, and review attestations. Submission starts review; public publication occurs only after approval and a separate publish action.
- Current submission error guidance makes listing URLs optional for skills-only ZIP submissions; remote MCP submissions have stronger URL, scan, domain-verification, and review requirements.
- OpenAI's app guidelines separately require a clear, published privacy policy. The Paddle Toolkit-specific policy is hosted on sapienx.app and identifies Kazım Akgül as the individual publisher; the manifest links to it. A separate terms page is not required for this skills-only package.
- OpenAI's submission metadata requires the `CHAT` and `CODEX` product identifiers for broad coverage. The installed local Codex CLI 0.158.0-alpha.2.1 instead reports that it expects `CHATGPT` and `CODEX`; this local parser warning does not match the current upload guide, so the package follows the directory submission contract and records the local compatibility gap.

## Paddle

- Paddle's current MCP documentation lists `https://sandbox-mcp.paddle.com/mcp` with sandbox API-key Bearer authentication and `https://mcp.paddle.com/mcp` with OAuth (or optional API key). It explicitly states sandbox does not support OAuth and environment keys/objects are separate.
- Paddle's docs MCP is `https://paddlehq.mcp.kapa.ai`, hosted by Kapa.ai and authenticated with Google or GitHub for abuse/rate-limit controls. It is a documentation lookup service, not the account-action server.
- Paddle's live OAuth flow uses direct user authorization; account permissions are based on Paddle access and can be managed in the Paddle MCP settings.
- `PaddleHQ/paddle-agent-skills` is licensed Apache-2.0. Paddle Toolkit preserves the upstream license file and attribution; its skills are separately authored and are not mirrored copies.

## Implementation decision

Submit the final skills ZIP as **Skills only**. Declare only Paddle's OAuth-capable live MCP dependency in the narrowly scoped live-operations skill. Keep sandbox MCP configuration user-owned because it requires a secret Bearer key and is not OAuth-capable. Do not submit Paddle's existing MCP server as though it were operated by Kazım Akgül.

## Primary references

- [OpenAI: Build skills](https://developers.openai.com/plugins/build/skills)
- [OpenAI: Package your plugin](https://developers.openai.com/plugins/build/plugins)
- [OpenAI: Authenticate users](https://developers.openai.com/plugins/build/auth)
- [OpenAI: Submit plugins](https://developers.openai.com/plugins/deploy/submission)
- [OpenAI: Submission errors](https://developers.openai.com/plugins/deploy/submission-errors)
- [OpenAI: Plugin guidelines](https://developers.openai.com/plugins/app-guidelines)
- [Paddle: Paddle MCP server](https://developer.paddle.com/sdks/ai/paddle-mcp/)
- [Paddle: Docs MCP server](https://developer.paddle.com/sdks/ai/docs-mcp/)
- [Paddle: Live MCP OAuth release](https://developer.paddle.com/changelog/2026/paddle-mcp-oauth/)
- [PaddleHQ/paddle-agent-skills](https://github.com/PaddleHQ/paddle-agent-skills)
- [PaddleHQ/paddle-agent-skills LICENSE](https://github.com/PaddleHQ/paddle-agent-skills/blob/main/LICENSE)
