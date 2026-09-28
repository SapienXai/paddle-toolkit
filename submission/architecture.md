# OpenAI submission architecture

**Submission type:** Skills only (portable Agent Plugins ZIP)

**Why:** SapienX owns the workflow package, not Paddle's MCP server. The package has no custom API proxy, Paddle backend, credential store, or MCP implementation. Current OpenAI skill guidance supports a skill declaring an external MCP dependency in `skills/<skill>/agents/openai.yaml`. The `paddle-live-operations` skill uses that native dependency for Paddle's OAuth-capable live endpoint.

**Live:** `paddle-live-operations` declares the Paddle endpoint directly. Paddle performs browser OAuth; user permissions remain governed by Paddle. The skill activates only for explicit live/production intent and applies extra confirmation to destructive or hard-to-reverse changes.

**Local install:** The repository marketplace uses `policy.authentication: ON_USE`, so a local install does not request Paddle authorization up front. The OAuth connection is deferred until the client first needs the live MCP.

**Sandbox:** Paddle's official sandbox endpoint currently requires a Bearer API key and does not support OAuth. The skill bundle does not embed or declare that key. Users connect their own official sandbox MCP through their client and a protected local secret mechanism. If it is absent, account mutations stop with setup guidance; code-only work continues.

**Documentation:** The Paddle docs MCP endpoint is hosted by Kapa.ai and requires Google or GitHub sign-in. It is optional and used only when already connected. Skills link to current Paddle documentation and must not invent API behavior when no current source is available.

This is a skills-only public submission because the submitted product is the skills ZIP; the live MCP dependency is an OpenAI-supported per-skill dependency and does not make SapienX the owner/operator of that server. No root `mcp.json` is included, and the submission does not claim to submit Paddle's server as SapienX's.
