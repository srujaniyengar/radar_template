# Assumptions and deviations — mm unless noted

These are starting values, not measured hardware interfaces. Original dimensions supplied by the user are retained in `dimensions.kcl` unless a deviation is expressly listed below. The pedestal remains an unvalidated draft; its values describe intended geometry, not a finished part.

## Scope and files
- Four intended printed components: plate, hub, pedestal shell, bottom cover. Only plate, hub and cover currently execute. No wing or external side panels were added to the holder.
- The imported STL was viewed as a reference only, not dimensionally reverse-engineered or edited.
- Parameters are ordinary editable KCL numbers with range comments; no actual UI slider controls were created. Ranges are not a validated configuration envelope.
- Repeated blocks, circles and wedges use shared custom functions. Sketches inside those functions are not point-and-click editable in the application.
- No hardware bodies, thread helices, sensor electronics, flexible cables or rubber material deformation are modeled.

## Plate
| Item | Assumption / implemented value |
|---|---|
| Native axes | 92 along X, 57 along Y, front Z=0; rear pockets open toward +Z, cans toward -Z before assembly rotation. |
| Pocket layout | Centres (-30,0), (0,0), (30,0); 20.3 along X and 45.3 along Y; floor Z=1. |
| Can windows | Centres Y=±13 at each pocket centre X; CAD Ø16.4 without compensation; only six windows. |
| Headers | Slots 4 along X, 12 along Y; centre at pocket X+11.95, Y=0; 0.2 overlap into pocket long edge. |
| Snap lips | Two per module, six total; wedge width/rise 1.5/1.5 (45°); length 6 along Y; crown Z=3.2; base Z=1.7; overlap 0.5. Positive-X lip at Y=-16, negative-X lip at Y=+16. |
| Snap fit | No PCB thickness, flexural beam stiffness, insertion force or fatigue allowance was assumed verified. The wedge lips need functional testing. |
| Backing bridge — extra feature | Integral to plate, added to connect the central plug without placing its base directly through the middle board. Top Z=9, underside Z=6, beam 16 × 56.5 × 3. Not part of the original request; rear component and board-installation clearance remain unresolved. |
| Bridge legs | Width 16, length 5.35, centres Y=±25.575, bottom Z=2.8, top Z=9. |
| Plug | 16 square; nominal length 32 above bridge top; geometric blank includes 0.2 joining overlap. Tip chamfer 1 around four sides; tip Z=41. |
| Plate corners | No corner rounding beyond the user's unspecified square perimeter. |
| Default header/plug margin | 1.95 in projected local X, not valid across the entire 14..20 plug range; see NOTES. |
| Colour | #3b9cbb, display only. |

## Hub
| Item | Assumption / implemented value |
|---|---|
| Enlarged foot | Ø42.5 instead of requested Ø36, interpreting “alr start” as approval of the previously proposed option. Thickness remains 4. |
| Cable-hole edge wall | Additional 1.5 outer wall assumed when deriving Ø42.5. Cable bore remains CAD Ø8, centred at X=-15.75/Y=0. |
| Stem | 26 × 26, vertical-corner R3; native bottom overlaps foot by 0.2 at Z=3.8. Housing top Z=63; socket centre Z=50 (46 above foot top). No extra pedestal, wings or side panels on hub. |
| Socket | CAD 16.5 square, depth 12, back X=1, mouth X=13; 1 mm lead-in widens mouth to 18.5. No separate shrink correction to square socket. |
| Horn recess | CAD Ø20.5, depth exactly 2 from bottom; unmeasured fit. |
| Centre screw access | Ø5.7 CAD to target approximately Ø5.5 with 0.2 undersize; extended through the stem to allow tool access. |
| Bolt pattern | Four positions on Ø14 circle, clocked 45°, at X/Y=±4.949747. Unmeasured match to horn. |
| M2 bores | Ø2.6 CAD to target Ø2.4 printed. |
| Counterbores | Ø4.6 CAD to target Ø4.4 printed; assumed depth 1 below foot top, with same-diameter access wells continuing to stem top. Leaves nominal 1 of bearing material above the 2-deep horn recess. Screw-head height and driver access are not hardware-verified. |
| Lock insert | Axis +Z at X=9/Y=0; Ø4.4 CAD for requested Ø4.2 printed; 5 deep from top, opening 0.25 into cavity because roof is 4.75 thick. For nominal M3 × 4 insert; no insert model or chosen vendor. |
| Lock wall check | At default dimensions, front exterior wall to bore is 13-9-2.2=1.8; separation to nearest Ø4.6 access well is approximately 1.90. No thermal-installation or strength guarantee. |
| Lock screw | M3 functional callout only; length, head and tip form not selected. Must retract for plug rotation/removal. |
| Cable groove | Width 12 along Y, effective depth 6 into rear X face. Cutter extends 0.1 outside rear and 0.1 into foot top to avoid a coplanar boolean. Inner X=-7; groove floor Z=3.9. |
| Colour | #e8aa48, display only. |

## Pedestal draft
| Item | Assumption / intended value |
|---|---|
| Overall assembled envelope | 90 × 70 × 60 includes 4-thick cover. Shell height therefore 56 and is intended to sit at Z=4 in the completed assembly. |
| Shell cavity | 84 × 64 with R3 vertical inside corners; top thickness 6. Outside corners R6 and top chamfer 1.5. |
| Servo orientation | Long body axis X, body centre X=-5.5/Y=0 so assumed shaft is at origin. Assumed shaft offset +5.5 from body centre is unmeasured. |
| Servo fit | Rectangular opening 23.1 × 12.6 (22.5 × 12 plus 0.3 each side); no body-corner radii assumed. |
| Servo pilots | Ø1.9 CAD to target Ø1.7 printed, 5 deep; centre X=-5.5±13.75, Y=0. |
| Servo metadata only | User starting ear span 32, ear thickness 2.5 and underside height 16 retained as parameters, but there is no modeled servo to verify them or the horn stack. |
| Top cable bore | CAD Ø16, centre X=0/Y=15 from shaft. Leaves just 0.7 nominal planar web to the servo opening; this is an unresolved thin-web issue, not approved structure. |
| Rear | +Y is pedestal rear; centred 14-wide bottom notch. Body removes upper 4 of total 8-high notch; cover removes lower 4. |
| Corner posts | Centres X=±37/Y=±27; nominal Ø11 × 12 high from shell bottom. These booleans are the failed feature. |
| Inserts | Four Ø4.4 CAD × 5 deep bores from shell bottom for nominal M3 × 4 heat-set inserts; nominal radial material 3.3 before wall intersections. |
| Intended printing | Top face down, not yet screened or sliced. |
| Intended colour | #4c5669, display only. |

## Bottom cover
| Item | Assumption / implemented value |
|---|---|
| Outline | Same 90 × 70 envelope and R6 corners as shell, thickness 4. No locating tongue or gasket assumed. |
| Screw pattern | Matches post centres X=±37/Y=±27. |
| Screw clearance | Ø3.6 CAD to target nominal Ø3.4 printed M3 clearance. |
| Screw heads | Ø6.6 CAD to target Ø6.4 printed, 2 deep from underside. Screws not selected; these pockets may not suit all M3 heads. |
| Rubber seats | “Recesses of 10” interpreted as Ø10, depth assumed 1.5; centres X=±29/Y=±19. CAD diameter uncorrected. |
| Rubber parts | Only for the conditional stability calculation: assumed full Ø10 contact, 2.5 overall pad thickness, thus 1 protrusion. Adhesion/compression and actual pads are unverified and not modeled. |
| Ballast tray | Added integrally to cover, open upward; clear 60 × 40 × 12, wall thickness assumed 2; outside 64 × 44, top Z=16. Capacity 28.8 cm³. No internal ballast retainer assumed. |
| Cable notch | 14 wide, through cover at +Y edge; cutter extends through wall and outside by 1 each side. |
| Colour | #718096, display only. |

## Placement, screening and calculation assumptions
- Hub bottom at Z=66 (6 above reference top Z=60); shaft/horn stack has not been measured to confirm this placement. Socket centre at Z=116. Plate front centre X=42/Y=0/Z=116.
- Default preview pan=0 and plate quarter-turn=0 (row); separate column review uses 90. No animated pan or sampled collision solver ran. Continuous-pan bounds in NOTES are coordinate calculations, not a dynamics simulation.
- Square socket fit is nominal 0.25 per side; no external plug shrink, elephant-foot allowance, or tuned friction coefficient was assumed.
- A 0.2 diameter allowance was added to small fastener/insert bores only. Windows, round cable openings, horn recess and pad seats retain stated CAD diameters. Do not apply another 0.2 compensation blindly in a slicer.
- Boolean construction allowances are not functional tolerances: blind tools extend 0.1 beyond open face; through tools generally extend 1 beyond each face; plate pocket cutter extends 0.1; integral unions overlap 0.1 or 0.2; pedestal post-preserving tools extend 2 below the draft shell and are consumed as tools.
- Build screening assumed 0.2 layer height, +Z build for the three completed parts, 45° surface angle from build plate. Printer size, material density, extrusion width, temperatures, speeds, infill, wall count and cooling were not invented. No print mass estimate is given.
- Stability assumptions and exact formula are in NOTES: supplied base-plus-existing-ballast mass 250 g and payload 60 g; assumed base COM Z=30 centred, payload COM Z=120/radius42, extra secured ballast COM Z=10, ground Z=-1, full rubber contact discs, rigid static support, no acceleration/cable load/sliding. These produce approximately 18° and require at least 111 g extra ballast under this scenario, not a validated completed design.

No zero-support, complete-fit, load-capacity, tipping-safety or manufacturability claim is made.
