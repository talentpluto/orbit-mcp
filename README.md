# Orbit MCP

Polaris is TalentPluto's people-finding assistant for Orbit members. This
repository is the plugin marketplace that connects Claude Code and Codex to
it. It is separate from the Pluto recruiting plugin
([talentpluto/pluto-mcp](https://github.com/talentpluto/pluto-mcp)):
installing one never installs the other, and each has its own sign-in.

With Polaris you work on your own Polaris thread, the same one you text:
catch up on what Polaris found, say yes or no to people with your reasons,
refine searches, manage goals, answer intro requests and ask for intros.
Everything you decide shows up in iMessage and on the dashboard, and Polaris
learns from it as if you had texted.

Sign in with the phone you text Polaris from. New to Polaris? The sign-in
window lets you join: it finds your profile, then you text Polaris a short
code from your phone to start, the same way the website does. Polaris is open
to the same people as the website.

From Claude or Codex you can also tell Polaris about yourself (your agent
shows you what it will share first), see what Polaris remembers, answer intro
requests, update your profile and public page, import your LinkedIn
connections, draft Gmail messages, and read your conversation with Polaris.

## Install

### Claude Code

```text
/plugin marketplace add talentpluto/orbit-mcp
/plugin install polaris@orbit
```

Then run `/mcp`, select **polaris**, and sign in. Start a new session
afterward.

### Codex CLI

```bash
codex plugin marketplace add talentpluto/orbit-mcp
codex plugin add polaris@orbit
codex mcp login polaris
```

### Codex desktop

Open **Plugins**, add the marketplace `talentpluto/orbit-mcp`, install
**Polaris** and sign in.

### Claude app

Add a custom connector with the URL
`https://app.talentpluto.com/api/mcp/orbit` and sign in. On Team and
Enterprise plans an admin may need to add the connector for you first.

## Try it

"What's new from Polaris?", "Pass on the first three, too senior", "Keep
looking for this every week", or "Tell Polaris about me".
