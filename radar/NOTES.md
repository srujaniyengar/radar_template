# Sensor-holder project — partial, NOT print-ready

## Current status
- `plate.kcl`: executes; all 9 evaluated sketches fully constrained. Three module pockets, six windows, three header slots, six wedge lips, raised backing bridge and chamfered square plug. Engine volume 19,930.087 mm³; local uniform-density COM (-0.251762, 0, 11.919179) mm.
- `hub.kcl`: executes; all 11 evaluated sketches fully constrained. Engine volume 31,768.369 mm³; local uniform-density COM (0.767669, -0.000080, 27.455584) mm. **Its exported mesh failed integrity screening**, so executable KCL is not evidence that this part is printable or export-safe.
- `bottomCover.kcl`: executes; all 7 evaluated sketches fully constrained. Engine volume 29,020.335 mm³; local uniform-density COM (-0.000002, -0.254720, 3.403006) mm.
- `pedestal.kcl`: failed draft. The union of the shell with four corner posts failed. One topology-preserving retry cut the post footprints out of the cavity cutter, but that subtraction also failed. No successful finished-shell validation, snapshot, or physical properties.
- `main.kcl`: executable **three-part partial preview**, with the missing pedestal called out in its header. The cover is at Z=0 and the holder at its intended installed height; the empty space is intentional, not an invisible pedestal.
- `reviewColumn.kcl`: alternate executable three-part preview. It does not add manufactured parts to the BOM.
- Both preview orientations were visually checked once. The assembly execution report lists zero local sketches because it imports parts; use the individual part constraint reports above.
- No servo, horn, sensors, inserts, screws, rubber pads, ballast or cable solids are modeled. There are exactly three sensor positions, not extra modules.

## Recovery history
1. Original plate attempt failed on a solver-scope name collision; an alias fixed it.
2. Original plate retry reached a failed bridge union; work stopped as requested.
3. User requested another retry. Connecting the plate to its bridge legs, then the beam, then the plug succeeded without dimensional changes.
4. New hub's final groove subtraction failed. Its one retry moved the cut earlier and extended the groove 0.1 into the foot to avoid the coplanar junction; execution succeeded.
5. New bottom cover succeeded on its first execution.
6. New pedestal failed and its one retry failed. Repairs stopped. No failed features were silently removed.

## Clearance review — analytical bounds, NOT a collision simulation
The 90 × 70 reference box was not modeled as a manufactured part. Its assumed top is Z=60. The shaft is (X,Y)=(0,0), +Z; hub bottom is Z=66, foot top Z=70, socket centre Z=116. Row and column screenshots show cans would face +X.

- Plate front datum X=42, panel rear X=39. Bridge rear/plug shoulder X=33. Socket opening X=13; plug tip X=1. Thus free plug length is 32 and insertion depth 12, with 20 shoulder-to-opening stand-off.
- Row panel minimum Z=87.5; column panel minimum Z=70. Their respective vertical separations from the stand-in top are 27.5 and 10.0. The hub foot, at Z=66, sets the overall holder-to-box vertical lower bound of 6.0.
- Pan rotation about +Z preserves all these Z bounds continuously through -100..+100 degrees (indeed any pan angle).
- Plate-panel radial separation from the foot cylinder is at least 39 - 21.25 = 17.75. Bridge material is at radius >=33, giving at least 11.75. Plug material is at Z>=108, 38 above the foot top. Hence a conservative partition-based plate-to-foot lower bound is 11.75 in either orientation for all pan angles.
- Nominal 16 square plug vs 16.5 square cavity gives 0.25 per side at 0/90/180/270 degrees; both plug cross-section and tip chamfer have fourfold symmetry. This is a dimensional check, not a printed fit or physical insertion test. The clamp screw must be backed off for removal.
- At the default plug size, the central header slot starts at X=9.95 in plate coordinates, 1.95 from the plug/bridge footprint edge at X=8. The specified slider range was NOT fully validated: plug width 20 reduces this projected margin to -0.05. Do not assume every documented parameter-range combination works.
- Hub foot cable hole centre radius 15.75, radius 4, horn recess radius 10.25, outer foot radius 21.25 gives 1.5 between cable bore and recess and 1.5 to the outside edge. The cable groove intentionally connects to this hole.
- Actual servo height/horn stack, the extra PCB bridge, sensor installation/removal, electronics, screw tools, and moving cables remain unverified. Mesh defects in the hub prevent promoting these source-derived bounds to complete geometry approval.

## FDM screening performed once per completed part
Assumptions: consumer FDM, user-specified PLA or PETG and 0.4 nozzle; +Z build direction (front face down for plate, foot down for hub, cover underside down); 0.2 mm layer sampling assumed; 45° surface angle from the build plate used as a screening boundary. No printer volume, minimum total contact area, or universal thickness/gap threshold was supplied. Orientation optimization was NOT performed.

| Part | Result | Evidence |
|---|---|---|
| Plate | Mesh integrity passed; overhang warnings | 732.8 mm² horizontal underside on the backing bridge, plus small nominal-45° lip regions reported at approximately 44.9999° due to tessellation. |
| Hub | Mesh integrity FAILED | Exported mesh not watertight and not a consistently oriented positive-volume enclosure. Thickness, gaps, overhangs, contact and island checks were blocked. |
| Cover | Mesh integrity passed; overhang warnings | Four counterbore shoulders at 23.8791 mm² each and four rubber-foot recess ceilings at 78.4137 mm² each; total flagged horizontal area about 409.17 mm². |
| Pedestal | Not analyzed | KCL does not execute. Intended top-down orientation remains untested. |

Plate sampled minimum thickness 0.117851 mm near a tapered snap-lip edge, sampled minimum gap 2.522012 mm, ideal bed contact 3834.591 mm². Cover sampled minimum thickness 2.0 mm, sampled minimum gap 3.582665 mm, ideal contact 5763.291 mm². Ray sampling covered all triangle centroids (2060 plate, 2390 cover), not continuous surfaces; no configured thresholds means these results remain indeterminate, not passes. Do not substitute the gap samples for specific socket or header fits.

Layer checks completed 206 plate sections and 81 cover sections without isolated-layer findings; partial support and bridging feasibility are not checked. Geometry confidence was 0.9 for overhang/contact and 0.7 for sampled rays; some imported-function source attribution was unresolved. No slicer, support generation, material-specific bridge test, adhesion, strength, fatigue or printer validation was performed. **Zero support-requiring area has NOT been demonstrated.**

## Conditional static stability calculation — not a validated assembly result
Inputs supplied: base plus existing ballast 250 g; total rotating payload 60 g; payload COM 60 above the nominal Z=60 top.
Additional assumptions: original 250 g base COM at Z=30 and centred; worst-case payload COM at radial offset 42, Z=120; rubber feet have full 10-diameter contact discs centred at X=±29/Y=±19 and protrude 1 below cover; extra secured ballast centred at Z=10; rigid level support, no sliding, no cable force or acceleration. The actual printed payload mass and contact footprint are unknown.

Worst pan direction is toward the short support edge (reachable at ±90). Effective half-width is 19+5=24. For 310 g total, horizontal COM shift = 60*42/310 = 8.129 mm, support margin = 15.871 mm, COM height above assumed ground = (250*30+60*120)/310 + 1 = 48.419 mm. Tipping angle = atan(15.871/48.419), approximately **18°**, below 25°.

For added ballast b at height 11 above assumed ground, the 25° criterion is:
`[24*(310+b) - 60*42] / [250*31 + 60*121 + 11*b] >= tan(25°)`.
This gives b >=110.186 g: round upward to **111 g additional ballast**, raising the original base-plus-ballast mass from 250 to at least **361 g** under these assumptions. This is not a verified amount for the unfinished pedestal. Initial ballast quantity to reach 250 g is `250 g - measured dry base/hardware mass`, if positive. Total ballast and actual capacity require that dry mass and the ballast packing density. Tray nominal capacity is 60*40*12 = 28,800 mm³ = 28.8 cm³; secure ballast against shifting.

Every added design value is listed in `ASSUMPTIONS.md`. Do not print or treat this as the completed four-part design.
