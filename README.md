<img src="plugins/rihla-plugin/assets/logo.png" alt="Rihla" width="120" />

# Rihla Plugin

Five customer-experience skills and a production MCP connection for Claude and Codex, by Sadaa.

**Connection URL: `https://mcp.sadaa.com/mcp`** · Transport: Streamable HTTP · Authentication: OAuth, scope `rihla`.

`mcp.sadaa.com` is the host; include `/mcp` when adding the connector. Each user signs in with their own account. No backend service secret or API key is needed.

## Skills

| Skill | What you get |
|---|---|
| `cx-card-analysis` | A visual CX report card with supported metrics, findings and your organization's branding. |
| `cx-action-plan` | Prioritized improvements, proposed owners, time horizons and success measures; a visual card when requested. |
| `customer-feedback-analysis` | Comment themes, anonymized quotes, limitations and supported segment comparisons. |
| `survey-design-review` | Concise Arabic/English survey design, review, and authorized draft creation. |
| `journey-measurement-design` | Touchpoints, measurement plans, and authorized journey drafts. |

For visual cards, provide your **logo, brand colors and organization/branch name**. The skill asks for missing details and reuses what you already provided. A reference card supplies layout inspiration, not permission to copy its customer branding. Image rendering depends on the host's tools; this package does not bundle an image renderer.

## Install this branch

This version is on `codex/cx-skills-production-guide`. The default branch is not updated by publishing this branch. Use the branch-specific instructions below to get the five skills and production endpoint.

### Claude Code

No manual clone is needed. Run these as separate prompts in Claude Code:

```text
/plugin marketplace add https://github.com/sadaaCX/rihla-mcp.git#codex/cx-skills-production-guide
/plugin install rihla-plugin@sadaacx
```

Claude downloads the selected branch for you. On Claude Code v2.1.275 or later, you can also add and install in one prompt:

```text
/plugin install rihla-plugin --marketplace https://github.com/sadaaCX/rihla-mcp.git#codex/cx-skills-production-guide
```

Use `/mcp` to authenticate the `rihla` server. Reload plugins or restart when prompted. Try `/rihla-plugin:cx-card-analysis` with an attached report and your brand assets.

### Codex

```bash
codex plugin marketplace add https://github.com/sadaaCX/rihla-mcp.git --ref codex/cx-skills-production-guide
codex plugin add rihla-plugin@sadaacx
```

Complete OAuth in the app. For CLI authentication, run `codex mcp list` to find the registered server name, then `codex mcp login <server-name> --scopes rihla`. Start a new task to load the installed skills and tools.

The marketplace name is `sadaacx`; the package name is `rihla-plugin`; its MCP server key remains `rihla`. An already-registered marketplace may need its source/ref updated through the host's marketplace management before installing this branch.

## Claude Desktop, Cowork and ChatGPT

See the [MCP connection guide](docs/mcp-guide.md) for direct-connector setup, the difference between a connector and the skill bundle, and public-directory limitations.
