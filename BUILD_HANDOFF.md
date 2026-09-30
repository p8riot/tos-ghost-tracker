# P.M.S. Tracker 2.3.0 Build Handoff

Product: P.M.S. Tracker - The Other Side
Version: 2.3.0
Release status: Stable
Release class: MINOR
Baseline: 2.2.0
Schema compatibility: unchanged, DATA_SCHEMA_VERSION 2

## Release scope

This release upgrades the Behavior filtering system and its mobile UI without changing the persistent data schema.

Primary changes:

- Uniform half-width bordered Behavior controls.
- Independent Lights On/Off, Radio On/Off, Individual Breakers On/Off, Candle Light/Extinguish controls.
- Simplified Main Breaker filter.
- Candle Cannot Light filtering added using the user-approved Ghost Information interpretation.
- Variable LOS category added while retaining normal LOS categories.
- Mobile touch targets increased to 44 CSS px minimum.
- Cross / Desecration notes added in compact form.

## Compatibility

- Existing evidence system preserved.
- Existing storage schema preserved.
- Puca mimic exceptions preserved.
- Existing service-worker scope and PWA paths preserved.
- Service-worker cache identity bumped for this release.

## Validation status

Application logic, behavior truth tables, voice commands, responsive layout, syntax, manifest, icon, and app-shell integrity passed.

Installed/offline PWA behavior is NOT TESTED live in the execution environment because Chromium is prevented from navigating to localhost/file origins. See QA_REPORT.md.

## Deployment

Follow DEPLOYMENT.txt. Upload the complete package without changing relative paths unless the corresponding HTML, manifest, and service-worker paths are updated together.
