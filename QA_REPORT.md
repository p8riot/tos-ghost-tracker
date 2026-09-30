# P.M.S. Tracker 2.3.0 QA Report

Release status: Stable package
Date: 2026-09-30

## Result summary

- Application logic / runtime: PASS
- Ghost data validation: PASS
- Behavior truth-table regression: PASS
- Candle logic: PASS
- Main Breaker logic: PASS
- Variable LOS logic: PASS
- Voice behavior commands: PASS
- Mobile responsive Behavior UI: PASS
- JavaScript syntax: PASS
- Manifest / app-shell file integrity: PASS
- Installed PWA / offline live validation: NOT TESTED in this environment because the browser sandbox blocks localhost/file navigation used for service-worker testing.

## Data validation

Startup validator result:

- 25 ghosts
- 7 active evidence types
- 0 validation errors
- 0 validation warnings

## Behavior truth-table checks

All states passed their expected membership counts:

- Base Speed: Slow 13, Medium 12, Fast 2.
- Main Breaker: Can Interact 22, Cannot Interact 3.
- Individual Breakers On: Can 22, Cannot 3.
- Individual Breakers Off: Can 24, Cannot 1.
- Candle Light: Can 4, Cannot 21.
- Candle Extinguish: Can 18, Cannot 7.
- Doors: Can Close/Lock 24, Cannot 1.
- FLX-POD: Can Deactivate 17, Cannot 8.
- Holy Water: None 2, Low 18, High 7. Puca remains intentionally eligible under mimic logic.
- Hunt Cooldown: Short 4, Medium 19, Long 2.
- Natural Early Hunt: 3.
- Lights On: Can 20, Cannot 5.
- Lights Off: Can 21, Cannot 4.
- LOS Range: Near 2, Far 23.
- LOS Speed: Very Slow 3, Slow 8, Medium 11, Fast 8, Variable 7.
- Manifest: Full Form Possible 20, Shadow Only 5.
- Radio On: Can 23, Cannot 2.
- Radio Off: Can 23, Cannot 2.

Targeted combination tests also passed, including:

- Lights On + Cannot Off = Sluagh, Wisp.
- Lights Cannot On + Can Off = Nasnas, Tariaksuq, Wewe Gombel.
- Radio On + Cannot Off = Strigoi.
- Radio Cannot On + Can Off = Phantom.
- Individual Breakers Cannot On + Can Off = Echo, Wewe Gombel.
- Candle Can Light + Can Extinguish = Marid, Sluagh.
- Candle Can Light + Cannot Extinguish = Strigoi, Wisp.
- Candle Cannot Light + Cannot Extinguish = Echo, Hupia, Phantom, Puca, Skia.

## Candle-specific checks

PASS:

- `Candle Light` cycles Clear -> Can -> Cannot -> Clear.
- `Candle Extinguish` cycles Clear -> Can -> Cannot -> Clear.
- `candle cannot light` voice command sets the Cannot Light filter.
- Canonical behavior helper returns `Can light` for Marid and `Cannot light` for Echo.
- Best-test/helper logic no longer disagrees with the Candle Light filter.

## Main Breaker checks

PASS:

- Simplified cycle Clear -> Can Interact -> Cannot Interact -> Clear.
- Cannot Interact returns exactly Echo, Wewe Gombel, Wisp.
- Post-hunt and overload guidance remains non-identifying.

## LOS Speed checks

PASS:

- Variable state returns exactly Ataphoi, Nasnas, Puca, Skia, Tariaksuq, Wisp, Wraith.
- Nasnas remains in Very Slow and Variable.
- Puca mimic behavior remains preserved.

## Mobile / responsive checks

Behavior controls were browser-tested at:

320, 360, 375, 390, 430, 768, 1024, 1366, and 1920 CSS px.

PASS at every tested width:

- 18 behavior controls.
- 9 rows, 2 controls per row.
- No horizontal overflow.
- Labels remain inside their own behavior cards.
- Minimum behavior button height: 44 CSS px.
- Bordered cards preserve visual separation on narrow screens.

## Package integrity

PASS:

- Inline JavaScript parses successfully with Node syntax validation.
- `manifest.webmanifest` parses as valid JSON.
- Required icons exist at declared sizes: 192x192 and 512x512.
- Apple touch icon exists at 180x180.
- Every file listed in the service-worker app shell exists.
- Service-worker cache identity is release-specific for 2.3.0.
- Build metadata channel is `stable`.
- No preview-channel markers remain in the runtime source.

## Live PWA limitation

A local HTTP server was started successfully and its files were reachable with command-line HTTP checks. Chromium navigation to localhost and file origins is blocked by the execution environment with `ERR_BLOCKED_BY_ADMINISTRATOR`, so service-worker registration, installed-PWA presentation, and offline reload could not be promoted to LIVE PASS here.

The manifest, service-worker source, app-shell paths, icons, and cache identity passed static validation. Final hosting should still use HTTPS, as documented in DEPLOYMENT.txt.
