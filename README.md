# Fire Planner

A browser tool for planning support-by-fire positions, sectors of fire and target reference points (TRPs). It answers the questions a fire plan has to answer, for example "this TRP is 45° right of the direction of fire, 800 m out, inside the right limit".

This is a **tactical planning aid**. It is not a range safety tool: it does not draw surface danger zones. For live-fire safety use a separate range safety tool such as [sdz-planner](https://github.com/mickeeygee/sdz-planner).

## Use it
Open `index.html` (or the hosted page). Place each position as a single point. Type lat/lon or MGRS, tap the map, or use your GPS. Set the azimuth of the direction of fire and the left and right limits. Add TRPs from the **+** menu (New TRP) and tap the map, typing a coordinate, or entering an azimuth and distance. Each TRP shows:

- distance, azimuth in degrees and mils
- how many degrees (and mils) it is left or right of the direction of fire
- whether it is inside the left/right limits, and by how much it is inside or outside
- whether it is within the weapon's maximum effective range

TRPs are shared by every position. Angles, sector checks and range checks are shown relative to whichever position is selected, and each TRP lists which positions' sectors cover it.

**Sector overlap:** where two positions' sectors of fire cross (each needs left/right limits and a max effective range), the overlap is shaded amber on the map and listed on the Aim tab with its area and the TRPs both positions cover.

Picking an M240B preset sets the sector limits from its traverse (tripod 15°, bipod 40° total, split evenly around the azimuth).

**Arrows:** the red aim arrow and the two orange limit arrows can be dragged along their lines to move them out of the way (and sideways to change the angle). Each one remembers where you put it, per position. **Reset arrow positions** (Setup tab, or More on a phone) puts them back.

**Assault lines:** use the **+** at the top and choose **New assault line** (or the Assault tab / More menu on a phone), then tap the two ends of the assaulting element on the map. You can add as many lines as you need. Each position shows how many degrees its sector is off every line, measured at the position from whichever troop is angularly closest to the sector, and flags any line that is closer than the required angle (15° by default, editable). **Keep fire off the lines** pulls the nearest sector edge out to the required angle, working through the closest line first. If that would cut the sector below half its width (for example a 15° tripod traverse), it slides the whole sector away instead and keeps its width. Assault lines are shared by all positions.

**Copy fire plan** puts a text summary on the clipboard. **Download KML** opens in Google Earth. **Save project** writes a JSON file you can open on another device.

Everything is stored in your own browser. Nothing is sent to any server (map pictures load from Esri World Imagery and OpenStreetMap, and the app works with the map turned off).

## On a phone
The map fills the screen and the controls sit in a bottom sheet. Drag the handle up for the full controls (Setup, TRPs, More) and down to a compact bar with big one-tap buttons: **Use my location** or **Place on map** to start, then **Add TRP**, **Aim**, **Undo**, **GPS** and **More**. Turned sideways, the controls become a panel on the right.

## Things to know
- Angles are measured from the direction of fire at the position, in true degrees (no grid or magnetic correction). 6400 mils per circle.
- Weapon ranges are typical published figures, not authoritative. Check them against the weapon manual and your unit SOP. The range box is editable.

## Planned
Support-by-fire sectors as their own object, final protective line, range cards, friendly positions.

## Build
`index.html` is generated. Edit `src/app.html` and run `python3 tools/build.py`, which inlines Leaflet (BSD-2-Clause), polygon-clipping (MIT) and the MGRS helper from `vendor/`.
