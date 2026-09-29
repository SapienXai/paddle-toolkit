# Paddle account access

Paddle Toolkit contains skills, not an account proxy. Connect account tools directly to Paddle using the user's client. Never request or store a Paddle API key in chat, plugin files, repository configuration, or logs.

## Current endpoints and authentication

| Purpose | Endpoint | Authentication | Default use |
|---|---|---|---|
| Live account operations | `https://mcp.paddle.com/mcp` | Paddle OAuth; a live API key is an alternate Paddle option | Use only when the prompt names live, production, or real customer data |
| Sandbox account operations | `https://sandbox-mcp.paddle.com/mcp` | Sandbox API key as a Bearer token; this server does not support OAuth | Use for test resources and integration development |
| Documentation lookup | `https://paddlehq.mcp.kapa.ai` | Google or GitHub sign-in with Kapa.ai for rate limiting | Optional source lookup; not an account connection |

The live MCP dependency in `skills/paddle-live-operations/agents/openai.yaml` uses Paddle's OAuth-capable live endpoint. The OAuth flow authenticates directly with Paddle; Kazım Akgül does not receive the token. Paddle's current OAuth connection starts with the permissions of the connected Paddle user. The user can review or change MCP permissions in Paddle's dashboard.

## Sandbox setup boundary

The sandbox endpoint requires a secret Bearer token and has no OAuth flow. Do not put a sandbox API key in a portable manifest, `agents/openai.yaml`, command argument, source file, or conversation. Use a client that can read the key from a protected local secret/environment store. For Codex CLI, Paddle documents `codex mcp add paddle-sandbox --url https://sandbox-mcp.paddle.com/mcp --bearer-token-env-var PADDLE_SANDBOX_API_KEY`; follow the current Paddle guide for the secret's storage and the process environment. Other clients should use Paddle's documented MCP configuration and their own secure credential input.

If sandbox tools are absent, explain that an account mutation cannot run yet, link the official Paddle MCP setup guide, and continue with code-only work where possible. Do not switch to the live endpoint. Do not report that an account change happened without a successful result from the sandbox tool.

## Skills-only dependency behavior

OpenAI's current Agent Plugins guidance supports a skill declaring an HTTP MCP dependency in `agents/openai.yaml` under `dependencies.tools`. Paddle Toolkit uses that native dependency only for live OAuth, where the official endpoint supports an interactive account authorization flow. It does not bundle Paddle's MCP server, copy its authentication, or declare an API-key sandbox dependency that could encourage embedding a secret.

If a dependency cannot connect, explain the direct Paddle connection path and stop before any account action. When tools are present, use only the environment named by the user. Check the tool's actual result and surface warnings or errors; never guess a successful outcome or blindly retry a mutation.

## Action boundaries

- Read or preview first when the requested workflow supports it.
- Before any live create or update, verify the prompt names live/production and identifies the intended object and values.
- Before a destructive or hard-to-reverse live action, summarize the exact account, target, and effect and wait for clear confirmation immediately before calling the tool.
- Treat Paddle's tool warnings as information, not as a substitute for user authorization.
- Never transfer an object between sandbox and live implicitly. IDs and credentials are environment-specific.
