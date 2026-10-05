# P.M.S. Tracker 2.3.1 Build Handoff

Product: P.M.S. Tracker - The Other Side
Version: 2.3.1
Release status: Stable
Release class: PATCH
Baseline: 2.3.0
Schema compatibility: unchanged, DATA_SCHEMA_VERSION 2

## Release scope

Temporarily removes the CheatSheet from the user-visible Reference Resources navigation and panels while preserving its implementation for later restoration.

## Preserved behavior

- CheatSheet source code remains in `Index.html` inside clearly marked HTML comments.
- CheatSheet CSS remains unchanged.
- `TOS_Cheat_Sheet_QB.png` remains packaged and cached.
- Existing `switchTab()` fallback behavior sends an unavailable/saved CheatSheet selection to Notes.
- All other Reference Resources, tracker logic, ghost data, evidence/behavior filtering, storage, and PWA structure remain unchanged.

## Validation status

Static package, HTML structure, JavaScript syntax, manifest JSON, service-worker app-shell paths, version metadata, and Reference Resources tab/panel consistency were checked for this patch. No live installed-PWA/device validation was performed in this execution environment.

## Restoration

When the CheatSheet is ready to return, remove the two `TEMPORARILY HIDDEN` HTML comment wrappers around its tab button and panel. Replace the PNG if needed, then bump the product/cache version for the new release.
