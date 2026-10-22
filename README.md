# Fire Planner

A browser tool for planning support-by-fire positions, sectors of fire and target reference points (TRPs). It answers the questions a fire plan has to answer, for example "this TRP is 45° right of the direction of fire, 800 m out, inside the right limit".

This is a **tactical planning aid**. It is not a range safety tool: it does not draw surface danger zones. For live-fire safety use a separate range safety tool such as [sdz-planner](https://github.com/mickeeygee/sdz-planner).

## Use it
Open `index.html` (or the hosted page). Place the left and right ends of a position on the map, or a single point. Type lat/lon or MGRS, tap the map, or use your GPS. Set the azimuth of the direction of fire and the left and right limits. Add TRPs by tapping the map, typing a coordinate, or entering an azimuth and distance. Each TRP shows:

- distance, azimuth in degrees and mils
- how many degrees (and mils) it is left or right of the direction of fire
- whether it is inside the left/right limits, and by how much it is inside or outside
- whether it is within the weapon's maximum effective range

**Copy fire plan** puts a text summary on the clipboard. **Download KML** opens in Google Earth. **Save project** writes a JSON file you can open on another device.

Everything is stored in your own browser. Nothing is sent to any server (map pictures load from Esri World Imagery and OpenStreetMap, and the app works with the map turned off).

## Things to know
- Angles are measured from the direction of fire at the middle of the position, in true degrees (no grid or magnetic correction). 6400 mils per circle.
- Weapon ranges are typical published figures, not authoritative. Check them against the weapon manual and your unit SOP. The range box is editable.

## Planned
Support-by-fire sectors as their own object, final protective line, range cards, friendly positions.

## Build
`index.html` is generated. Edit `src/app.html` and run `python3 tools/build.py`, which inlines Leaflet (BSD-2-Clause) and the MGRS helper from `vendor/`.
