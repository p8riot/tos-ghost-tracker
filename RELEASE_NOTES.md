# P.M.S. Tracker 2.3.1 Release Notes

Release status: Stable
Release class: PATCH
Baseline: P.M.S. Tracker 2.3.0
Schema: DATA_SCHEMA_VERSION 2, unchanged

## Reference Resources

- Temporarily hides the CheatSheet tab from users while its reference image is being updated.
- Preserves the complete CheatSheet HTML, styling, JavaScript compatibility, and `TOS_Cheat_Sheet_QB.png` asset for easy restoration later.
- Existing users whose saved Reference Resources tab was CheatSheet safely fall back to Notes through the existing tab validation logic.
- All other Reference Resources remain available in Tabs View and Expand All.

## Compatibility

- No persistent-data or schema changes.
- No ghost data or filtering-rule changes.
- No storage-key changes.
- PWA paths and assets are preserved.
- Service-worker cache identity bumped so installed/browser copies can receive the patch.
