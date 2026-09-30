# P.M.S. Tracker 2.3.0 Release Notes

Release status: Stable
Release class: MINOR
Baseline: P.M.S. Tracker 2.2.0
Schema: DATA_SCHEMA_VERSION 2, unchanged

## Behavior filtering redesign

- Behavior controls now use a uniform two-column mobile-first grid.
- Every behavior occupies the same half-width bordered card.
- Behavior names stay above the clickable state button so long labels do not crowd the state text.
- Behavior touch targets are at least 44 CSS px high.
- Lights, Radio, Individual Breakers, and Candles use independent directional/capability controls.

## Main Breaker

- Simplified to `Clear -> Can Interact -> Cannot Interact -> Clear`.
- `Cannot Interact`: Echo, Wewe Gombel, Wisp.
- Post-hunt breaker changes and breaker overload/trips are not identifying Main Breaker interactions.

## Candles

Candle lighting and extinguishing are tracked independently.

- `Can Light`: Marid, Sluagh, Strigoi, Wisp.
- `Cannot Light`: the remaining 21 ghosts, per the user-approved rule that absence of the candle-lighting ability in Ghost Information is treated as inability to light candles.
- `Cannot Extinguish`: Echo, Hupia, Phantom, Puca, Skia, Strigoi, Wisp.
- `Can Extinguish`: the remaining 18 ghosts.

Useful combined results:

- Can Light + Can Extinguish: Marid, Sluagh.
- Can Light + Cannot Extinguish: Strigoi, Wisp.
- Cannot Light + Cannot Extinguish: Echo, Hupia, Phantom, Puca, Skia.

Voice commands now support `candle cannot light` as a real filter.

## LOS Speed

- Normal categories remain Very Slow / Slow / Medium / Fast.
- Added overlapping `Variable` state.
- Variable LOS membership: Ataphoi, Nasnas, Puca, Skia, Tariaksuq, Wisp, Wraith.
- Nasnas remains Very Slow under its normal LOS speed and is also Variable.
- Puca retains its hunt-mimic bypass for Base Speed, LOS Speed, and Holy Water.

## Notes

Included the compact Cross notes agreed during the 2.3.0 work:

- Cross: must be in the ghost's favorite room for it to interact with it.
- Desecration: desecrating the Cross can upset the ghost.
