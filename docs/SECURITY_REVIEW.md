# Security review (2026-10-28)

Checked every copied file for: hooks, MCP servers, pipe-to-shell installs, remote code execution, prompt-injection phrases and committed secrets.

**Result: nothing malicious found.** Hits were defensive text (skills telling Claude to *refuse* `curl | bash` or to ignore injected instructions) and one fake test key (that test folder was removed).

Things to know before enabling:

| Plugin | What runs automatically | Risk / advice |
|---|---|---|
| `impeccable` | Hooks on session start, after every Edit/Write, and on Stop run its bundled `impeccable` launcher. First run may download its engine binary from GitHub releases, verified against `engine-checksums.txt`. | Low. Enable only in web-UI projects. |
| `understand-anything` | PostToolUse hook runs a Node script; SessionStart hook can tell Claude to refresh the knowledge graph without asking, **only if** you turned on `autoUpdate` in `.understand-anything/config.json`. | Low. Leave autoUpdate off unless wanted; analysis costs many tokens. |
| `expo` | Adds Expo's hosted MCP server (`https://mcp.expo.dev/mcp`). | Needs an Expo login. |
| `open-seo` | Adds OpenSEO's hosted MCP server (`https://app.openseo.so/mcp`). | Some calls are paid. |
| `paid-ads`, `ppt-master`, `ui-ux-pro-max`, `hyperframes`, `hallmark`, `scroll-craft`, `understand-anything`, `vercel-agent-skills` | Ship Python/Node/shell scripts that run only when a skill asks Claude to run them (Claude asks permission per command unless you auto-approve). | Normal; review prompts before approving. |
| everything else | Markdown only. | None. |

Re-run this review whenever a plugin is re-synced from upstream.
