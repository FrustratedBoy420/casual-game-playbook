# KPI Gates

All numbers are **starting defaults** for casual and puzzle games on US-weighted traffic. Re-tune them from your own cohorts after 3–5 launches.

## Test stages

| Stage | Traffic | Budget (typical) | Question answered |
|---|---|---|---|
| A. Creative / CPI test | Store page or playable + video ads, 1–3 geos | $300–$1,000 | Do people want to click and install? |
| B. Retention test | 1,000–3,000 installs, cheap geo (e.g. PH, IN, LATAM) or Tier-1 if budget allows | $1,000–$5,000 | Do they come back? |
| C. Monetization test | Tier-1 cohorts (US / CA / UK / AU), 2,000+ installs | $3,000–$15,000 | Do they pay back the CPI? |
| D. Scale | Tier-1, budget steps of +20–30%/week | open | Does ROAS hold as spend grows? |

Retention from cheap geos is a directional signal only. Confirm with Tier-1 traffic before scaling.

## Gate thresholds

### Gate A: market fit (CPI)

| Metric | Kill | Iterate | Pass |
|---|---|---|---|
| IPM (installs per 1,000 impressions) | < 10 | 10–25 | > 25 |
| Store page conversion (view → install) | < 20% | 20–30% | > 30% |
| CPI US iOS, puzzle | > $4.00 | $2.50–$4.00 | < $2.50 |
| CPI US Android, puzzle | > $2.00 | $1.00–$2.00 | < $1.00 |

### Gate B: retention

| Metric | Kill | Iterate | Pass |
|---|---|---|---|
| D1 retention | < 30% | 30–38% | > 38% |
| D7 retention | < 8% | 8–14% | > 14% |
| D30 retention | < 3% | 3–6% | > 6% |
| D0 playtime | < 8 min | 8–15 min | > 15 min |
| FTUE completion | < 75% | 75–90% | > 90% |
| Level-5 reach | < 60% | 60–75% | > 75% |

### Gate C: monetization

| Metric | Kill | Iterate | Pass |
|---|---|---|---|
| Ad ARPDAU (Tier-1) | < $0.04 | $0.04–$0.08 | > $0.08 |
| IAP conversion (D7 payers / installs) | < 0.5% | 0.5–1.5% | > 1.5% |
| D7 ROAS | < 10% | 10–18% | > 18% |
| D30 ROAS | < 30% | 30–50% | > 50% |
| Predicted payback | > 365 days | 180–365 days | < 180 days |

### Gate D: scale health (weekly)

- ROAS curve holds within 15% of the test cohort as spend rises. If not, pause the step-up.
- Blended CPI rises less than 25% per doubling of spend.
- Creative fatigue: replace any creative whose IPM drops 30% from its peak.

## Decision tree

```
Gate A fail ──► change theme/art/hook once ──► fail again ──► KILL
Gate A pass ──► Gate B
Gate B fail ──► iterate FTUE/difficulty/content (max 2 cycles) ──► still fail ──► KILL or PARK
Gate B pass ──► Gate C
Gate C fail ──► tune ads/IAP via remote config (max 2 cycles) ──► still fail ──► RESKIN or PARK
Gate C pass ──► SCALE (Gate D weekly) ──► plan franchise sibling
```

## Definitions

- **KILL:** remove from the stores or leave it unlisted. Stop all spend and updates. Write a 5-line post-mortem.
- **PARK:** keep it live with no UA and no updates. Let it earn organically. Review quarterly.
- **RESKIN:** keep the package and save system. Change the art, narrative and name, then retest from Gate A.
- **SCALE:** UA budget steps, weekly live-ops updates, A/B tests running continuously.

## A/B testing rules

- One variable per test. Split users at install through remote config.
- Need at least 1,000 users per arm for retention tests and 3,000+ for monetization tests.
- Run tests for a full 7 days minimum to cover weekday and weekend behaviour.
- Log `ab_group` as a user property on every analytics event.
