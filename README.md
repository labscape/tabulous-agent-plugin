# Tabulous Agent Plugin

Connects AI agents to a [Tabulous](https://www.tabulous.ai) lab data workspace over the [Model Context Protocol](https://modelcontextprotocol.io).

This plugin follows the [Agent Plugins](https://agent-plugins.org) open standard. It contains no code: it points your agent at the hosted Tabulous MCP server at `https://app.tabulous.ai/mcp`.

## What agents can do

Once connected, an agent can:

- List Registry Tables and read records from them
- Browse files stored in a record's folder
- Look up Toolkit items, workspace members, and workspace info
- Stage changes (records, schema, Toolkit items, files) as a **changeset** for review

Agents cannot write to your workspace directly. Every change is staged as a changeset with a review link, and a person approves it in Tabulous before anything goes live. Read `docs` through the MCP server for the full agent workflow guide.

## Installation

### Cursor

Install **Tabulous** from the Cursor Marketplace, or add the plugin manually:

```bash
git clone https://github.com/labscape/tabulous-agent-plugin ~/.cursor/plugins/local/tabulous
```

Then run **Developer: Reload Window**. The Tabulous MCP server appears under Customize.

### Any other MCP client

Add a remote (Streamable HTTP) MCP server with this URL:

```text
https://app.tabulous.ai/mcp
```

The client will open a browser window to sign in with your Tabulous account.

## Authentication

The server uses OAuth 2.1 with Dynamic Client Registration. No API keys or configuration variables are required. On first use your MCP client redirects you to Tabulous to sign in; the resulting token is scoped to your user and organization, so the agent sees exactly what you can see.

By default only workspace admins can connect agents. Admins can open it up to all members under **Settings > Integrations > External Agents** in Tabulous.

## Files

| Path | Purpose |
| --- | --- |
| `plugin.json` | Agent Plugins manifest |
| `mcp.json` | MCP server definition (remote, Streamable HTTP) |
| `assets/logo.svg` | Marketplace logo |

## Support

Questions or issues: open an issue in this repository or reach out to the Tabulous team through the app.

## License

MIT. See [LICENSE](LICENSE).
