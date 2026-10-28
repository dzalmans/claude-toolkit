# <Project name>: instructions for Claude Code

- **Read `docs/PLAN.md` before any work.** It is the single source of truth: product spec, design direction and stages.
- **Stack:** <fill in: e.g. Next.js + Tailwind + shadcn/ui, or Flutter + Riverpod + Supabase>.
- **Skills and plugins** come from the `claude-toolkit` marketplace (see `.claude/settings.json`). Only enable what this project needs; every enabled skill costs context.
- **Work stage by stage.** Stop at the end of each stage with a summary, acceptance-criteria proof and a checklist, then wait for the owner's "go".
- Secrets never in the repo. Ask before adding paid services. No hard-coded user-facing strings.

## Handoff report for the reviewer (standing rule)
At the end of every stage, and whenever the owner says "handoff", create `docs/handoff/STAGE_<N>_HANDOFF.md` (mid-stage: `STAGE_<N>_HANDOFF_<YYYY-MM-DD>.md`) and `docs/handoff/handoff.zip` (the .md plus screenshots).

The report must contain, in this order:
1. Status: stage, done / in progress / blocked, branch, latest commit, PR link.
2. What was built.
3. Acceptance criteria from docs/PLAN.md, each with ✅/❌/⚠️ and proof (test command + result, coverage, CI run link).
4. Screenshots of every new or changed screen (PNG, max ~15) in `docs/handoff/screens/`, with captions.
5. Deviations from PLAN.md and why (also in DECISIONS.md).
6. Problems, risks, known bugs, TODOs.
7. Numbered questions for the owner, each with a recommendation.
8. What needs the owner's action outside the repo.
9. Proposed next step and rough time.
10. Key file tree (2–3 levels) and configs the reviewer must check (never real secrets).
11. Every visual file created or changed, with path and one-line description.

Rules: plain language first, max ~400 lines, no secrets, commit and push the handoff files. At the end of the reply give the GitHub links to the .md and .zip and send every visual file (or show them inline with GitHub links).

## Merging (standing rule)
- **Never merge a stage PR yourself.** Merge only when the owner explicitly writes "merge PR #N".
