# Platform Modules (the shared base)

Build this once and reuse it in every game. Every SDK sits behind an interface so vendors can be swapped without touching game code.

## Module list

| Module | Responsibility | Typical vendor options |
|---|---|---|
| `Core.Boot` | Init order, splash, consent, first scene | — |
| `Core.Save` | Local save + optional cloud save | PlayerPrefs/JSON, Firebase, PlayFab |
| `Core.RemoteConfig` | All tunables, A/B group assignment | Firebase Remote Config, Unity Remote Config |
| `Consent` | ATT (iOS), GDPR/TCF, CCPA | Google UMP, mediation CMP |
| `Ads` | Mediation wrapper: rewarded, interstitial, banner, app-open | AppLovin MAX, Unity LevelPlay, AdMob |
| `IAP` | Store purchases, receipt validation, restore | Unity IAP, RevenueCat |
| `Analytics` | Event taxonomy, user properties | Firebase Analytics, GameAnalytics, AppMetrica |
| `Attribution` | Install source, SKAN / Privacy Sandbox, ROAS | Singular, AppsFlyer, Adjust |
| `Crash` | Crash and ANR reporting | Firebase Crashlytics, Sentry |
| `Notifications` | Local reminders + remote push | Firebase Cloud Messaging, local notifications |
| `Review` | Native review prompt at positive moments | SKStoreReviewController, Play In-App Review |
| `LiveOps` | Daily challenge, events, timed offers | Remote config + content JSON |
| `Economy` | Coins, hints, boosters, inventory | — |
| `Levels` | Level loader, difficulty curve, solver check | JSON / ScriptableObjects |
| `CrossPromo` | Promote sibling games (franchise) | House ads in the mediation SDK |

## Suggested Unity layout

```
Assets/
  _Platform/            # shared base, identical across games (git submodule or UPM package)
    Core/ Ads/ IAP/ Analytics/ Attribution/ Consent/ Crash/
    Notifications/ Review/ LiveOps/ Economy/ CrossPromo/
  _Game/                # game-specific code and content
    Scripts/ Levels/ Art/ Audio/ Scenes/
  Resources/RemoteConfigDefaults.json
```

Ship `_Platform` as a versioned UPM package so every game gets fixes at once.

## Init order

1. Crash reporting
2. Consent (UMP / ATT)
3. Remote config fetch (with cached defaults and a 2–3 s timeout)
4. Analytics + attribution
5. Ads (after consent)
6. IAP
7. Notifications permission (ask after a few sessions, not at first launch)

## Analytics event taxonomy

| Event | Params |
|---|---|
| `tutorial_step` | `step`, `duration_sec` |
| `level_start` | `level`, `attempt`, `difficulty_tier` |
| `level_complete` | `level`, `duration_sec`, `hints_used`, `stars` |
| `level_fail` | `level`, `reason`, `progress_pct` |
| `hint_used` | `level`, `source` (coins / rewarded / free) |
| `ad_impression` | `format`, `placement`, `network`, `revenue_usd` (ILRD) |
| `ad_reward_claimed` | `placement`, `reward` |
| `iap_offer_shown` | `offer_id`, `trigger` |
| `iap_purchase` | `product_id`, `price_usd`, `offer_id` |
| `review_prompt_shown` | `level` |
| `session_start` | `session_number`, `days_since_install` |
| `liveops_event` | `event_id`, `action` |

User properties: `install_date`, `ab_group`, `is_payer`, `max_level`, `geo_tier`, `acquisition_channel`.

## Remote config keys (defaults)

```
difficulty_curve_id            = "default"
ftue_variant                   = "A"
review_prompt_level            = 12
review_prompt_min_wins_streak  = 3
offer_starter_level            = 8
offer_ltd_trigger              = "day3_nonpayer"
push_reminder_hours            = 20
crosspromo_enabled             = false
```

Monetization keys are listed in `monetization.md`.

## Level production

- Generate levels with procedural rules or AI assistance. Always validate them with an automated solver (solvable, unique answer where needed, difficulty score).
- Store levels as JSON so new content can ship through remote content updates without a new build where the store rules allow it.
- Difficulty curve: about 5 easy levels, then a saw-tooth (hard level, then 2 easier ones), controlled by remote config.
