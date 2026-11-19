# Monetization

Hybrid model: ads are the base layer, IAP is the upside. Every number below lives in remote config.

## Ad formats and placements

| Format | Placement | Default rules |
|---|---|---|
| Rewarded video | Hint, extra moves, double coins, unlock a level, daily chest | Always opt-in. Show the reward clearly before the ad. No cap, or a cap of about 20 per day |
| Interstitial | After a level is completed (never mid-level, never after a fail) | Start at level 3–5. Cooldown 60–90 s. Max about 1 per 2 levels at first, tightening later |
| Banner | Bottom of the gameplay screen | Optional. Older casual audiences tolerate it. Hide it during the FTUE |
| App open | On resume after more than 30 s in the background | Optional. Off for new users during the first 3 sessions |

### Default remote config keys

```
ads_interstitial_start_level      = 4
ads_interstitial_cooldown_sec     = 75
ads_interstitial_every_n_levels   = 2
ads_banner_enabled                = true
ads_app_open_enabled              = false
ads_rewarded_hint_amount          = 1
ads_first_session_no_inter        = true
```

### Mediation

- Use one mediation platform (AppLovin MAX, Unity LevelPlay or AdMob mediation) with in-app bidding enabled.
- Add 10–20 demand partners over time. More bidders mean higher eCPM, but each adds SDK size and crash risk.
- Track impression-level ad revenue (ILRD) and send it to analytics and the MMP for ROAS.

## IAP ladder

| Tier | Item | Typical price | Notes |
|---|---|---|---|
| Entry | Starter pack (one-time) | $1.99 | Coins + hints + no-ads trial. Offered after level 5–10 |
| Entry | Progression reward ladder ("treasure ladder") | $1.99 | Paid track of rewards unlocked by playing |
| Core | Remove ads | $2.99–$9.99 | Removes interstitials and banners. Rewarded ads stay opt-in |
| Core | Tiered bundles: Beginner / Super / Master / Mega / Ultra | $1.99 / $4.99 / $9.99 / $19.99 | Same structure in every game, so it is reusable |
| Whale | Coin packs | $4.99 → $49.99 → $79.99 / $99.99 | Hints and boosts sink |
| Timed | Limited-time offer | $4.99 | Triggered by remote-config segment (e.g. day-3 non-payer, after a fail streak) |

### Rules

- Show the first offer only after the player has had a win, never at first launch.
- Keep the coin economy simple: one soft currency, with hints and boosts as sinks.
- Offers are segmented by payer status and by days since install through remote config.
- iOS players usually buy more. Expect IAP-heavy revenue on iOS and ad-heavy revenue on Android.

## Economy sinks and sources

| Sources | Sinks |
|---|---|
| Level completion coins, daily reward, rewarded ads, streak bonus, events | Hints, extra moves, boosters, cosmetics (themes, frames) |

Target: an average player can afford 1 hint per 3–4 levels without paying. That keeps hints desirable but not frustrating.
