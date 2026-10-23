# Build and validation report

## Files and coordinates
- `sensorHolder.kcl`: one fused sensor holder; original requested coordinate frame.
- `servoBase.kcl`: servo base; shaft datum at local (0, 0).
- `main.kcl`: display-only X offsets of -75 mm and +75 mm; parts remain separate.
- Editable dimensions are at the top of each part file. Servo dimensions are unmeasured guesses. Optional base mounting holes are enabled.
- Shared solver profiles are in `profiles.kcl`; sketches inside helpers are not point-and-click editable.

## Checks
- Both part files and main.kcl execute. All 13 holder sketches and all 6 servo-base sketches are fully constrained.
- Sensor holder: mesh integrity completed without defects, one connected mesh component. Visual/source review shows ribs confined to edge margins and all three pockets and six windows open, except for the specified 0.5 mm snap-lip projections.
- Horn counterbores: nominal adjacent edge separation 5.4995 mm; separation to centre opening 1.95 mm. Centre recess depth 2+2 mm breaks through the nominal 4 mm tab.
- Servo base: KCL execution succeeds, but exported mesh integrity FAILS: not watertight and not a consistently oriented positive volume. Do not treat it as print-ready. Dependent directional mesh checks were blocked.
- Servo posts have integral R2 roots on their Y sides, not all-around base fillets; X faces are left clear for insertion. A 0.00001 mm outward post offset avoids a kernel coincident-face union failure.
- Volumes returned by the geometry engine: holder 17296.955 mm³; base 35598.400 mm³. The base volume result does not override its mesh failure.

## Screening scope
- FDM profile used provisionally to access mesh checks: +Z build direction, 0.2 mm sampled layers, 45° overhang threshold from build plate. No printer, material, minimum wall/gap/contact requirement or build envelope supplied.
- Holder screening flags 30 overhang regions, chiefly tab holes/rounded lower corners and snap-lip undersides; no unsupported layer islands reported. Thickness sampling is partial and minimum thickness/gap suitability is indeterminate.
- This is mesh screening and visual/source review, not slicer, fit, strength, or manufacturing certification. Stopped after the final checks as requested.
