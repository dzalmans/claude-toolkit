# claude-toolkit

All of LapMate's Claude Code setup plus 18 curated third-party skill packs, packaged as a **Claude Code plugin marketplace**. Every project turns on only the plugins it needs, so Claude's context isn't flooded with ~290 skills at once.

## What's inside

| Plugin | What it's for |
|---|---|
| `lapmate-flutter` | 25 official Flutter/Dart skills (from LapMate) |
| `apple-design` | Apple design language + iOS HIG (from LapMate) |
| `supabase` | Supabase + Postgres best practices (from LapMate) |
| `frontend-design` | Anthropic's web design skill (from LapMate) |
| `hallmark`, `impeccable`, `ui-ux-pro-max`, `magic-ui`, `scroll-craft` | Web UI design: anti-AI-slop, polish, design systems, animated components, scroll sites |
| `stitch-design-md` | Google Stitch / DESIGN.md skills |
| `humanizer`, `stop-slop` | Make writing sound human |
| `agent-skills`, `vercel-agent-skills` | Engineering workflow (spec → ship) and React/Next.js best practices |
| `understand-anything` | Codebase knowledge graph + dashboard |
| `security-audit` | `/security-audit` web-app audit |
| `expo` | React Native / Expo apps |
| `hyperframes` | HTML → video |
| `ppt-master` | Editable PowerPoint from docs |
| `open-seo`, `paid-ads` (Claude Ads) | SEO and paid-ads audits |
| `google-workspace` | Gmail/Drive/Docs/Sheets/Calendar via the `gws` CLI |

Reference material (not plugins): `library/awesome-design-md` (~70 brand DESIGN.md files) and `library/design-md-spec`.

Details, upstream commits and licences: `docs/SOURCES.md`. Security notes: `docs/SECURITY_REVIEW.md`.

## Use it in a project

**A. Plugins (recommended).** Copy `templates/settings.json` to `<project>/.claude/settings.json` and list the plugins you want under `enabledPlugins` as `"<plugin>@claude-toolkit": true`. Or interactively:

```
/plugin marketplace add dzalmans/claude-toolkit
/plugin install hallmark@claude-toolkit
```

**B. Plain copy (always works, including cloud sessions).** Copy `plugins/<plugin>/skills/*` into `<project>/.claude/skills/` (and `commands/*` into `.claude/commands/`), and commit them.

**Starting a new project:** copy `templates/CLAUDE.md` (your standing rules: stage-by-stage, handoff report, never self-merge) and fill in the stack. LapMate's exact `CLAUDE.md` and `.mcp.json` are in `templates/lapmate/`.

## Updating

Ask Claude: "re-sync plugin X from the upstream in docs/SOURCES.md, re-run the security review, and show me the diff".
