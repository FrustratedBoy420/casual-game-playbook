# Case Study: Spill Games (public teardown, Nov 2026)

This is a condensed teardown of a Bengaluru portfolio studio, built only from public sources: press, app store listings, ad transparency libraries, the studio's privacy policy, Exodus Privacy static reports and AppGoblin estimates. It shows the playbook working in practice. Estimates are approximate.

## Snapshot

- Founded in 2024 by three former PlaySimple Games operators. About $14.35M raised; the Series A of $10.5M was led by Elevation Capital in Oct 2026.
- Stated thesis: a portfolio of 5–10 profitable titles, not one hit. "Hit-making is less about magic and more about method."
- In-house platform "Compass" modularizes analytics, retention, monetization and live ops. They claim about 4x faster launches, and 3 → 6 profitable titles in under 3 months.

## Portfolio pattern

| Phase | What happened |
|---|---|
| 2024 | 5 quick casual tests (merge, hex match, onet, balloon match, word jigsaw). Early ratings leaned to India, suggesting a cheap test geo. All abandoned |
| Early 2025 | First winners: Sticker by Number, Zen Math Crossword |
| Late 2025 – early 2026 | More bets: one sort game reskinned (new art + narrative, same package), one parked, and Cozy Finds: Hidden Objects became a winner |
| Jul 2026 | Franchise + batch launch: 3 games in the same week, 2 under the "Cozy" brand |
| Late 2026 | Series A money into UA on the 2 hero titles. Weekly updates on winners |

Approximate scale for the hero titles: Zen Math about 959K iOS + 492K Android installs; Cozy Finds about 231K iOS + 404K Android.

## Distribution

- Stores only, with no web or community presence. Market: US iOS first, then UK / CA / AU. English only.
- Paid UA almost entirely on Google App Campaigns: about 35 vertical gameplay videos, only for the 2 winners. No active Meta ads at the time of research.
- Ad hooks: "DESIGNED FOR SENIORS", "YOUR BRAIN AGE: 40", "HARDER THAN YOU THINK!", "SUPER RELAXING", "make your commute feel shorter". Each concept was uploaded 2–4 times as variants.
- ASO: keyword-rich package names (e.g. `com.spill.math.puzzle.games.crossmath.number.free`), the `Brand: Genre` title pattern, keyword subtitles.
- Ratings: 4.86–4.96★ across titles, with rating-to-install ratios of about 2.4–3.6%, driven by review prompts and release notes asking for reviews.

## Monetization and tech

- Unity games. Mediation through AppLovin MAX / LevelPlay / AdMob (Appodeal SDKs also found), with about 18–22 ad networks bidding.
- Singular for attribution. Firebase Analytics + Crashlytics + Cloud Messaging. AppMetrica in at least one title.
- The same IAP names across games ("Beginner / Master / Mega Deal", "Treasure Ladder", "No Ads Package"), which shows the shared modules. Prices from $1.99 to $99.99.
- Estimated revenue split: Android ad-led (about 60–64% ads); iOS more IAP-led on Cozy Finds (about 64% IAP).

## Lessons encoded in this skill

1. Shared platform + fixed gates = cheap experiments.
2. Proven mechanics + cozy, relaxing positioning + an older Tier-1 audience = efficient UA and high LTV.
3. Spend only on winners, then extend them into a franchise.
4. Many cheap creative variants on one real gameplay loop.
5. Reskin or park before you kill; batch launches; weekly live ops on winners.

## Sources

- PocketGamer.biz: https://www.pocketgamer.biz/indias-spill-games-raises-105m-in-series-a-funding/
- StartupTalky: https://startuptalky.com/news/spill-games-raises-usd-3-1-million-to-build-a-systems-led-global-mobile-gaming-company-from-india/
- Open Magazine: https://openthemagazine.com/business/ai-speeds-up-games-who-pays-for-the-players
- Google Play developer page: https://play.google.com/store/apps/dev?id=8874742134999279013
- App Store developer page: https://apps.apple.com/us/developer/spillvoy-gaming-private-limited/id1753517004
- Google Ads Transparency Center (advertiser: Spillvoy Gaming Private Limited)
- Exodus Privacy: https://reports.exodus-privacy.eu.org/en/reports/701078/
- AppGoblin: https://appgoblin.info/apps/6744523968
