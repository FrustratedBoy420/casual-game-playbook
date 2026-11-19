# Launch Checklist: <Game>

## Build
- [ ] `_Platform` package on the latest version
- [ ] Crash reporting live and a test crash received
- [ ] Remote config defaults bundled, fetch timeout set
- [ ] All analytics events firing (check in the debug view)
- [ ] Attribution SDK sees test installs, SKAN / Privacy Sandbox configured
- [ ] Ads: all formats load in test mode, ILRD revenue reaches analytics
- [ ] IAP: every product purchasable in sandbox, restore works, receipts validated
- [ ] Remove-ads purchase really disables interstitials and banners
- [ ] Review prompt fires only at the configured positive moment
- [ ] Notification permission asked after session 2+, not at first launch
- [ ] 30+ levels, all solver-validated, difficulty curve set in remote config
- [ ] FTUE under 60 s, no text walls
- [ ] Offline play works

## Compliance
- [ ] ATT prompt (iOS) and UMP / TCF consent (EEA / UK)
- [ ] Privacy policy lists every SDK in the build
- [ ] Store data-safety / privacy labels match the SDKs
- [ ] Target audience 18+ (or 13+), not in a kids or families program
- [ ] Original art, names and characters (no third-party IP)
- [ ] Ad creatives show real gameplay

## Store
- [ ] Title, subtitle, keywords and descriptions from `store-listing.md`
- [ ] 5+ screenshots with headlines, preview video
- [ ] Store listing experiments queued

## UA
- [ ] 6–12 creatives from `creative-matrix.md` uploaded
- [ ] Campaign goal: installs (switch to tROAS after data)
- [ ] Daily budget and geo set per `kpi-gates.md` stage
- [ ] Dashboard ready: CPI, IPM, D1/D7, ARPDAU, ROAS by cohort

## Post-launch
- [ ] Day 1, 3 and 7 checks scheduled
- [ ] Gate review date set, `test-report.md` started
