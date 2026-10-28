# Installed Claude Code skills

All skills are committed in `.claude/skills/`, so they load in Claude Code on the web. Upstream licences are in `.claude/skills/_licenses/`. Installed 2026-10-21; security review: no executable scripts, no install or network commands, no prompt-injection text (only `.md` docs and 5 example `.dart` files).

| Skill(s) | Source (commit) | Licence | Purpose |
|---|---|---|---|
| 25 × `dart-*`, `flutter-*` | github.com/flutter/agent-plugins `skills/` (6e59065) | BSD-3 (Flutter Authors) | Official Flutter/Dart best practices: architecture, tests, routing, localisation, layouts |
| `apple-design` (sub-skills: liquid-glass, animation-patterns, game-feel, typography, sf-symbols, ux-writing, ui-prototyping) | github.com/rshankras/claude-code-apple-skills `skills/design` (9ffb831) | MIT | Apple design language; **principles only**. Renamed from `design`, with a Flutter note added |
| `ios-hig` | github.com/johnrogers/claude-swift-engineering `plugins/swift-engineering/skills/ios-hig` (1dc2cf4) | MIT | Apple Human Interface Guidelines; **principles only**. Flutter note added |
| `supabase`, `supabase-postgres-best-practices` | github.com/supabase/agent-skills (c9be0e9) | MIT | Database security rules (RLS), migrations, Edge Functions, Postgres performance |
| `frontend-design` | github.com/anthropics/claude-plugins-official `plugins/frontend-design` (d1adba4) | Apache-2.0 | Polished web UI (dashboard and public pages) |

To update: ask Claude Code to "re-sync the skills in docs/SKILLS.md to their latest upstream versions, re-run the security review, and show me the diff".
