# UseAgents Agent Plugin

[Agent Plugins](https://agent-plugins.org) package for [UseAgents](https://useagents.site) — discover real developer tools at runtime instead of guessing from training data.

This plugin bundles:

- **MCP server config** — connects to the hosted UseAgents registry at `https://mcp.useagents.site/mcp`
- **Agent Skill** — teaches agents the search → context → docs → implement workflow

Compatible with Cursor and other [Agent Plugins 1.0.0](https://agent-plugins.org/specification) clients.

## What's included

| Component | Purpose |
| --------- | ------- |
| [`plugin.json`](./plugin.json) | Plugin manifest (name, version, metadata) |
| [`mcp.json`](./mcp.json) | Remote MCP server (`search_tools`, `get_tool_context`, `search_docs`) |
| [`skills/useagents/`](./skills/useagents/) | Discovery skill with MCP, CLI, and API references |

## Workflow

When an agent needs a developer tool:

1. **Search** — Query the registry with a natural-language task
2. **Shortlist** — Compare slug, capabilities, and freshness from results
3. **Fetch context** — Load install/bootstrap guidance for the chosen slug
4. **Search docs** — Ask deeper how-to questions against the tool's official documentation
5. **Implement** — Write code from context and docs; never invent package names when context is missing

## Install

### Cursor (local)

1. Clone this repo into your local plugins directory:

   ```bash
   git clone https://github.com/useagentsai/agent-plugin.git ~/.cursor/plugins/local/useagents
   ```

2. Restart Cursor or run **Developer: Reload Window**
3. Open **Customize** and confirm the UseAgents MCP server and skill are loaded

### Other Agent Plugins clients

Clone or copy this directory into your client's plugin path. The client discovers `plugin.json`, `mcp.json`, and skills under `skills/`.

## MCP tools

| Tool | Description |
| ---- | ----------- |
| `search_tools` | Natural-language registry search |
| `get_tool_context` | Install and usage context for a slug |
| `search_docs` | Search a tool's official docs with a question |

Docs: https://docs.useagents.site/mcp/tools-reference/introduction

## Related

- **Standalone skill install** — `npx skills add useagentsai/skills` ([useagentsai/skills](https://github.com/useagentsai/skills))
- **UseAgents site** — https://useagents.site
- **Documentation** — https://docs.useagents.site
- **Agent Plugins spec** — https://agent-plugins.org

## License

[MIT](./LICENSE)
