# LapMate: instructions for Claude Code

- **Read `docs/PLAN.md` before any work.** It is the single source of truth: product spec, design direction and stages.
- **Plan v2 (owner 2026-10-27) wins where it conflicts:** `docs/PLAN_V2.md` (devices, cameras, pricing, EU launch, stage order) and `docs/ECOSYSTEM.md` (the LapMate app family). New logic goes into packages (`packages/disciplines/<name>` for sport-specific parts), never into an app shell.
- **Stack:** Flutter (iOS, Android, web) using **Cupertino widgets on every platform**, Riverpod (not BLoC), Drift (SQLite), flutter_blue_plus, and Supabase (Postgres, Auth, Storage, Realtime, Edge Functions).
- **Look and feel:** iPhone OEM style, **always dark**, Apple Fitness/Workout + Apple Maps feel (see PLAN.md §2). Three tabs: Drive · Analyse · Me.
- **Skills** live in `.claude/skills/` (inventory: `docs/SKILLS.md`):
  - `apple-design` and `ios-hig` are for **design principles only**. Never write SwiftUI/UIKit code; translate to Flutter.
  - Use the `flutter-*` / `dart-*` skills for implementation and tests, `supabase` / `supabase-postgres-best-practices` for the backend, and `frontend-design` for web pages.
- **Dart MCP server** is configured in `.mcp.json`. Use it for analysis, tests, formatting and pub.
- **Work stage by stage** (PLAN.md §8). Stop at the end of each stage with a summary, acceptance-criteria proof and an on-track checklist (🏁), then wait for the owner's "go".
- Follow the development rules in PLAN.md §7: `telemetry_core` is pure Dart with ≥90% coverage; build the replay simulator early; design first, then golden tests; no hard-coded strings (EN and LV); metric units; secrets never in the repo; ask before adding paid services.
- The cloud environment is Linux: Android, web and tests run here. iOS builds go through macOS CI.

## Handoff report for the reviewer (standing rule, owner 2026-10-21)
At the end of every stage, and whenever the owner says "handoff", create a single self-contained report file so the owner's reviewer (another Claude, who cannot see this repo or chat) can understand the state and write the next prompt.

File: `docs/handoff/STAGE_<N>_HANDOFF.md` (overwrite if it exists; for mid-stage handoffs use `STAGE_<N>_HANDOFF_<YYYY-MM-DD>.md`).
Also save a copy as `docs/handoff/handoff.zip` containing the .md plus all screenshots listed below.

The report must contain, in this order:
1. Status: stage number, done / in progress / blocked, branch name, latest commit hash, PR link.
2. What was built: short list of features, packages, screens.
3. Acceptance criteria from docs/PLAN.md for this stage: each one with ✅/❌/⚠️ and the proof (test command + result summary, coverage %, CI run link and status).
4. Screenshots: export golden/test images of every new or changed screen and component (PNG, max ~15 images, phone sizes) into `docs/handoff/screens/` and list them with one-line captions.
5. Deviations from PLAN.md and why (also logged in DECISIONS.md).
6. Problems, risks, known bugs, TODOs left.
7. Questions and decisions needed from the owner, numbered, each with a recommendation.
8. What needs the owner's action outside the repo (accounts, secrets, keys, devices, on-track tests 🏁 with a checklist).
9. Proposed next step: what is planned next and roughly how long.
10. Key file tree (2–3 levels) and the content of any config the reviewer must check (pubspec workspace, CI workflow names, .env example — never real secrets).
11. Visual files: a list of EVERY visual file created or changed in this stage (screenshots, goldens, mockups, diagrams, icons, SVG/PNG/JPG/PDF/HTML previews), each with its path and a one-line description.

Rules:
- Plain language first, technical detail second. Max ~400 lines.
- Never include secrets, keys, passwords or personal tokens.
- Commit and push the handoff files.

At the very end of the reply, ALWAYS:
A) Give the direct GitHub link to the handoff .md and to handoff.zip, plus the exact file paths.
B) Send ALL visual files so the owner can see them in the chat:
   - If a tool can send/attach files, use it and send every visual file from section 11 (plus handoff.zip).
   - If files can't be attached, show each image inline with markdown AND give a clickable GitHub link for each one (github.com/<owner>/<repo>/blob/<branch>/<path>), one per line, grouped by screen.
   - Never skip this step. If there are no visual files, say "No visual files this time".

## Merging (standing rule, owner 2026-10-22)
- **Never merge a stage PR yourself.** Merge only when the owner explicitly writes "merge PR #N".
- **The owner tests on iPhone only** (no Android device; owner 2026-10-22). When a PR's CI is green, run the **Release** workflow on the PR branch (TestFlight), and tell the owner once the build is uploaded so they can update in TestFlight and test before merging. Don't send APK links. Release no longer runs on merge, so there is no second build. Android still builds and is tested in CI.
