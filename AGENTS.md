# Repository instructions

Do not add test files, test packages, test scripts, test fixtures, or CI
workflows that run tests in this repository.

Treat Polaris as a stable, thin connector. Ship routine tools and behavior
from the TalentPluto server; do not change the `polaris` server name, URL,
OAuth resource, scopes, compatibility headers, or `ON_INSTALL` policy unless
an explicit connector or permission-boundary migration requires it.

The plugin ships dual packaging over one `plugins/polaris` directory: Codex
reads `.agents/plugins/marketplace.json`,
`plugins/polaris/.codex-plugin/plugin.json` and `plugins/polaris/.mcp.json`;
Claude Code reads `.claude-plugin/marketplace.json` and
`plugins/polaris/.claude-plugin/plugin.json`, which carries an inline MCP
config. Keep the two plugin manifests' name, version and server URL in sync.
Keep the skills in `plugins/polaris/skills/` client-neutral, and keep the
Codex-only OAuth compatibility header out of the Claude Code config.

Do not tell users to upgrade, reinstall, log out or reconnect for routine
server updates or a missing tool alone.

This repository never changes the Pluto plugin in `talentpluto/pluto-mcp`.
