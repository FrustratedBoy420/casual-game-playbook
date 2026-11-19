# casual-game-playbook

A [Claude Code](https://claude.com/claude-code) skill for building, launching and scaling free-to-play **casual and puzzle mobile games** as a portfolio, the "systems-led" way.

When you start a new game, Claude uses this playbook to:

- pick a concept: proven genre + theme twist + target audience, scored against a checklist
- plan a shared Unity platform base: ads mediation, IAP, analytics, attribution, remote config, consent, reviews, live ops
- design monetization: ad placements, frequency caps, an IAP ladder
- write the store listing and ASO
- build a UA creative hook matrix
- run soft-launch tests against fixed KPI gates
- decide whether to kill, iterate, reskin, park or scale, then extend winners into a franchise

It is distilled from public teardowns of portfolio mobile studios. See [`references/case-study-spill-games.md`](references/case-study-spill-games.md).

## Install

```bash
# personal skill (all projects)
git clone https://github.com/FrustratedBoy420/casual-game-playbook ~/.claude/skills/casual-game-playbook

# or project skill
git clone https://github.com/FrustratedBoy420/casual-game-playbook .claude/skills/casual-game-playbook
```

On Windows (PowerShell):

```powershell
git clone https://github.com/FrustratedBoy420/casual-game-playbook "$HOME\.claude\skills\casual-game-playbook"
```

Claude Code loads it automatically. It triggers on requests like "start a new puzzle game", "plan monetization for my game", "write my store listing", "should I scale or kill this game?". You can also call it directly: `/casual-game-playbook`.

## Structure

```
SKILL.md                     workflow, principles, guardrails
references/
  kpi-gates.md               test stages, thresholds, decision tree, A/B rules
  monetization.md            ad placements, remote-config keys, IAP ladder, economy
  platform-modules.md        shared base modules, Unity layout, init order, event taxonomy
  aso.md                     naming, package IDs, listing copy, screenshots, ratings
  ua-creatives.md            hook matrix, video recipe, channels, budget pacing, geos
  portfolio-ops.md           cadence, genre scoring, franchise, reskin/park/kill, team
  case-study-spill-games.md  public teardown the playbook is based on
templates/
  game-brief.md  tech-plan.md  store-listing.md  creative-matrix.md
  test-report.md  launch-checklist.md
```

## Guardrails built in

- Original IP only: proven mechanics, never copied names, art, characters or levels.
- Ads must show real gameplay.
- Native review APIs only, with no incentivized ratings.
- ATT, GDPR (UMP / TCF) and accurate privacy labels. Adult target audience.
- Benchmarks are starting defaults. Re-tune them from your own data.

## Disclaimer

The KPI thresholds are industry-style starting points, not guarantees. The case study uses public information and third-party estimates, which may be inaccurate. This project is not affiliated with any company mentioned.

## License

MIT
