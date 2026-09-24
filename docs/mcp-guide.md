# Connect Rihla through MCP

## Production connection

| Setting | Value |
|---|---|
| Name | Rihla |
| MCP server URL | `https://mcp.sadaa.com/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth |
| Scope, if requested | `rihla` |

Enter the complete HTTPS URL including `/mcp`. Sign in to your Rihla account and review the access request. Users do not need the backend MCP service secret. Do not paste a service credential into OAuth client-secret fields.

## Claude: direct connector

In Claude, open **Customize → Connectors → Add custom connector**, enter the production URL, then connect and finish sign-in. Organization owners may need to add or enable the connector first. UI labels and availability depend on the host version and workspace policy.

A direct connector adds Rihla tools, not the five skill files. To use the full bundle, install `rihla-plugin` from this repository's marketplace as described in the [README](../README.md). On Claude Desktop/Cowork, **Customize → Plugins → Add marketplace → Add from a repository** is the marketplace route. While this release is only on its feature branch, ensure the selected source includes that branch; a bare repository URL generally selects the default branch. If the UI cannot select a branch, use the branch checkout/Claude Code instructions or the direct connector for tool-only access.

## ChatGPT

Where the account and workspace allow custom MCP apps, enable developer mode through the appropriate user/admin settings, create a custom app with the production URL and OAuth, and connect your Rihla account. Administrators may need to enable or publish the app within their workspace.

Installing this GitHub marketplace in Codex does not publish it in ChatGPT or automatically import these skills into a custom connector. Public directory availability requires a separate OpenAI submission, review and publication. This repository is a public package source, not a claim of directory approval.

## First use

Try: “Show my surveys and explain which one measures the visitor experience.” Then request a specific draft or analysis. For a CX card, provide the relevant report/data, logo, brand colors and organization name. Arabic and English are supported by the skill instructions. Actual visual rendering and embedded previews depend on the host's capabilities.

Analysis is read-only. Requested survey and journey edits are draft operations; publication is a separate action that must be requested. Scores and themes must retain their population, period and evidence limitations. The skills do not add tools that the server does not expose.

## Troubleshooting

- **No connection:** confirm the full URL and complete OAuth with the intended account; check workspace connector permissions.
- **Tools but no skills:** direct MCP configuration does not install the bundle. Install the plugin and start a new task/reload the host.
- **Duplicate tools or development data:** check for old `rihla` or local `sadaa-cx` installations and verify the connection points to `mcp.sadaa.com`.
- **No image output:** check whether the host provides image/chart rendering. The skill should explain the limitation rather than claim a text report is a rendered card.
- **Draft conflict:** read the explanation and resolve the competing edit; the skills must not silently overwrite it.

## References

- [Claude custom connectors](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)
- [Claude plugins](https://support.claude.com/en/articles/13837440-use-plugins-in-claude)
- [Claude marketplace documentation](https://code.claude.com/docs/en/plugin-marketplaces)
- [ChatGPT custom MCP apps](https://help.openai.com/en/articles/12584461-developer-mode-and-mcp-apps-in-chatgpt)
- [OpenAI public plugin submissions](https://developers.openai.com/plugins/deploy/submission)
