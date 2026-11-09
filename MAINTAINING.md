# Maintaining Orbit MCP

The customer-facing setup lives in [README.md](README.md). This file covers
packaging and authentication for maintainers.

## Packaging

- Codex reads `.agents/plugins/marketplace.json`,
  `plugins/polaris/.codex-plugin/plugin.json` and `plugins/polaris/.mcp.json`.
- Claude Code reads `.claude-plugin/marketplace.json` and
  `plugins/polaris/.claude-plugin/plugin.json`. Its inline MCP config uses the
  same OAuth scopes and intentionally omits the Codex-only OAuth
  compatibility header.
- Guidance in `plugins/polaris/skills` is shared by both clients.

Keep the two plugin manifests' name, version and server URL in sync, and bump
the version when the skill or manifests change.

## Server

`polaris` is the Orbit MCP at `https://app.talentpluto.com/api/mcp/orbit`
(`app/api/mcp/orbit` and `lib/mcp/orbit` in the webapp). It has its own OAuth
resource and the scopes `orbit:read`, `orbit:write`, `orbit:intro` and
`offline_access`, which the server never combines with recruiting or
personal-profile scopes. It is gated by the `orbitMcp` feature flag and the
Orbit allow list.

Sign-in uses the phone number the member texts Polaris from. The OAuth start
page sends any request with Orbit scopes to `/connect/polaris`.
