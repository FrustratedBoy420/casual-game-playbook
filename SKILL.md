---
name: casual-game-playbook
description: Systems-led playbook for building, launching and scaling free-to-play casual and puzzle mobile games (Unity, iOS + Android) as a portfolio. Covers concept choice (proven genre + theme twist + target audience), a shared monetization/analytics/live-ops base, store listing and ASO, UA video hooks, soft-launch KPI gates, and kill / reskin / scale / franchise decisions. Use when the user starts a new mobile game, picks or validates a game concept, plans ads or in-app purchases, writes a store listing, plans UA creatives, sets up analytics or remote config, runs a soft launch, or asks whether to kill or scale a title.
---

# Casual Game Playbook

A repeatable method for making casual mobile games that pay for their own user acquisition. It is distilled from public teardowns of portfolio studios (see `references/case-study-spill-games.md`). Hits come from **method, not magic**: ship many cheap, well-instrumented games, measure them against fixed gates, and put money only behind the winners.

## Core principles

1. **Portfolio over one hit.** Aim for 5–10 profitable titles. Expect most prototypes to die.
2. **Proven mechanic, fresh wrapper.** Pick a genre that already tops the charts. Differentiate on theme, tone, art and audience, not on a new mechanic.
3. **Platform first.** Every game reuses one shared base for ads, IAP, analytics, attribution, remote config, consent, reviews and live ops. A new game should be mostly content and art.
4. **Measure before you spend.** Every game ships with full analytics and attribution from build #1. No metrics means no decision.
5. **Fixed gates.** Kill, reskin or scale using the thresholds in `references/kpi-gates.md`, not gut feeling.
6. **Spend only on winners.** Paid UA goes to titles that clear the gates. Everything else gets zero budget.
7. **Winners become franchises.** A winning theme becomes a brand umbrella for sibling games ("Brand: Genre").
8. **Speed is the moat.** Short cycles, batch launches, weekly updates on live winners.

## Workflow

Run the phases in order. Each phase writes a file under `docs/` in the game project. Copy the templates from `templates/`.

| Phase | Goal | Output | Reference |
|---|---|---|---|
| 0. Audience and market | Pick who and where | section in `docs/game-brief.md` | `references/portfolio-ops.md` |
| 1. Concept | Proven genre + twist + hook | `docs/game-brief.md` | `references/portfolio-ops.md` |
| 2. Platform base | Wire the shared modules | `docs/tech-plan.md` | `references/platform-modules.md` |
| 3. Monetization design | Ads + IAP ladder | section in `docs/tech-plan.md` | `references/monetization.md` |
| 4. Prototype | Core loop + 30 levels + FTUE | playable build | this file |
| 5. Store and ASO | Name, package ID, listing | `docs/store-listing.md` | `references/aso.md` |
| 6. UA creatives | Hook matrix, 6–12 videos | `docs/creative-matrix.md` | `references/ua-creatives.md` |
| 7. Soft launch | Buy test traffic, read gates | `docs/test-report.md` | `references/kpi-gates.md` |
| 8. Decide | Kill / iterate / reskin / scale | decision in `docs/test-report.md` | `references/kpi-gates.md` |
| 9. Scale and live ops | UA budget, weekly updates, franchise | `docs/launch-checklist.md` | `references/portfolio-ops.md` |

### Phase 0–1: Concept

Fill `templates/game-brief.md`. A concept passes only if all of these hold:

- The core mechanic exists in at least 2 games in the current top-200 Puzzle or Casual charts.
- You can state the twist in one line: theme, tone, art style, audience, or one small mechanic tweak.
- The target player is named, with age band, gender skew, motivation and play moment (for example "adults 40+, relaxing 5-minute break, commute, evening wind-down").
- At least 3 ad hooks can be written for it (see `references/ua-creatives.md`).
- 100+ levels can be produced cheaply: procedural, or AI-assisted with a solver check.
- The name can follow the franchise pattern `Brand: Genre Keyword`.

Strong default audiences for casual puzzle: adults 35+, skewing women, in US / UK / CA / AU. They retain well, tolerate ads, have high ad eCPMs, and buy remove-ads and bundles.

### Phase 4: Prototype rules

- Core loop playable in under 10 seconds from first launch. No login wall.
- FTUE (first-time user experience) teaches by doing in 1–3 levels, with no text walls.
- 30 polished levels minimum for soft launch, with an easy start and a difficulty curve controlled by remote config.
- Feedback moments: progress counter (for example "4/30"), celebration burst, streaks. These double as ad footage.
- Calm defaults for the relaxing positioning: no timers, no lives, generous hints. Monetize through hints, boosts and remove-ads, not frustration.
- Every event in `references/platform-modules.md` (analytics taxonomy) fires from day one.

### Phase 8: Decision rules (summary)

| Result | Action |
|---|---|
| Fails the CPI / IPM gate | Kill, or change the theme and art and retest once |
| Good CPI, weak retention | Iterate on FTUE, difficulty and content for 2 cycles max, then kill |
| Good retention, weak monetization | Tune ads and IAP through remote config |
| Weak but not dead after 2 cycles | Reskin (new art and narrative, same package) or park (no updates, no UA) |
| Clears all gates | Scale UA in steps, ship weekly updates, plan a franchise sibling |

The full thresholds are in `references/kpi-gates.md`.

## Applying this skill to a new game project

When the user starts a new game:

1. Create `docs/` and copy all files from `templates/` into it.
2. Walk the user through the game brief. Push back on concepts that fail the Phase 1 checks.
3. Generate the Unity project structure and module stubs listed in `references/platform-modules.md`. Each module sits behind an interface, so SDK vendors can be swapped.
4. Put every tunable number in remote config with sane defaults, never hard-coded.
5. Draft the store listing and creative matrix before the build is finished, so marketing is ready at soft launch.
6. Before soft launch, run `templates/launch-checklist.md` item by item.

## Guardrails

- **Original IP only.** Use proven mechanics, but never copy a specific game's name, characters, art, levels, music or store assets.
- **Honest ads.** Creatives must show real gameplay from the actual build. Misleading "fake gameplay" ads breach Google and Meta policy and wreck retention.
- **Reviews through native APIs only.** Use `SKStoreReviewController` / Play In-App Review, triggered after positive moments. Never offer rewards for ratings, and never gate content on them.
- **Consent and privacy.** Implement ATT (iOS), Google UMP / TCF for GDPR, and a privacy policy that lists the actual SDKs. Set the store target audience to 18+ (or 13+ minimum), and keep the game out of Families / Kids programs unless it is fully compliant.
- **Ethical monetization.** No loot boxes aimed at vulnerable players, clear prices, and a remove-ads purchase that really removes forced ads (rewarded ads may stay opt-in).
- **Benchmarks are defaults.** The thresholds in the references are starting points. Re-tune them per genre and geo from your own data.

## Reference files

- `references/kpi-gates.md`: test design, metrics, thresholds, decision tree
- `references/monetization.md`: ad placements, frequency caps, IAP ladder, offers
- `references/platform-modules.md`: shared base modules, Unity layout, analytics events, remote config keys
- `references/aso.md`: naming, package IDs, listing copy, screenshots, ratings
- `references/ua-creatives.md`: hook matrix, video recipe, channel setup
- `references/portfolio-ops.md`: cadence, batch launches, geo strategy, franchise, reskin and park rules
- `references/case-study-spill-games.md`: public teardown this playbook is based on
