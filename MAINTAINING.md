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

## Repository ownership and rollout

This repository owns the Polaris connector packaging and client guidance.
The shared MCP server, authentication, search intake and background workers
remain in `talentpluto/webapp`; do not copy those services into this plugin.

The shared-intake and durable-search rollout is tracked in
[TP-327](https://linear.app/talentpluto/issue/TP-327), with backend changes in
[webapp#2501](https://github.com/talentpluto/webapp/pull/2501) and
[webapp#2504](https://github.com/talentpluto/webapp/pull/2504), on top of
[webapp#2496](https://github.com/talentpluto/webapp/pull/2496). Deploy both the
web server and worker before enabling the `orbit-mcp-search` task flag.
Connector guidance follows the live tool catalog and supports the existing
standalone query contract until `prepare_search` is available.
