# Nursery concept renders, September 16 2026

Six 4K stills plus one dusk variant, rendered headless from Unreal Engine 5.2.1
in the existing Collective Robotics nursery scene. These are cinematic brand
images, not a faithful recreation of any real farm. Caption every one on the site
as a concept render from our own simulation.

Source project: `/home/lucas/UE5/HERCULES/Unreal/Environments/Blocks/Blocks.uproject`
Private derivative maps (nothing in the film families was modified):
`/Game/CacaoField/Maps/Nursery_BrandGolden_20260916` and `Nursery_BrandDusk_20260916`,
both cloned from the accepted beauty level `Nursery_Beauty_20260905`.
Sequences and render presets: `/Game/PluralBrandStills20260916/Cine/`.
Build and render scripts: `/home/lucas/UE5/orchard_runs/run_nursery_v4/cinematic/brand_stills_20260916/`.

All PNGs are 3840 x 2160, Lumen, TSR, 16 temporal samples, no post work of any
kind beyond the engine's own post process. No text, no debug overlays, no
branding in frame.

The drone is a DJI Matrice 300 RTK static mesh from
`/home/lucas/UE5/Assets/Drones/Matrice300/source/MATRICE 300 RTK.fbx`, given a
plain dark shell material so it reads as a silhouette. It is real geometry in the
scene, not a composite. That FBX contains two separate meshes: the aircraft
(`polySurface4387`) and a hard transport case that sits on the ground under it
(`polySurface4181`). The case is dropped on import, so only the airframe, arms,
props, landing gear and gimbal camera appear in frame.

## The stills

**nursery-golden-wide-drone.png**
Low golden-hour wide across the block, sun just above the far treeline, long
shadows running toward camera, drone holding station in the upper left. 24 mm,
f/8, camera 3 m up. The most open composition of the set and the one with the
most room for a headline.

**nursery-aerial-topdown.png**
Straight-down aerial from 32 m, rotated so the rows run corner to corner. The
frame deliberately catches the edge of the block, so the canopy reads as green
diagonal stripes against tilled tan ground with shadow bands between them. 24 mm,
f/8.

**nursery-aerial-threequarter-drone.png**
Three-quarter aerial with the drone close in the foreground and the rows
receding under it, the tilled headland at the right edge. 35 mm, f/2.8, camera
16 m up, pitched 28 degrees down. Reads immediately as collection from the air.

**nursery-row-ground.png**
Ground level, standing in an aisle looking down it into the low sun. Haze between
the rows, dappled shadow across the alley, canopy closing in from both sides.
50 mm, f/2.5, camera 0.95 m up. The most atmospheric image of the set.

**nursery-rover-row-concept.png**
The ground rover in an aisle, rim-lit from behind with its shadow thrown toward
camera. 40 mm, f/2.8, camera 0.58 m up, about 3.3 m back. Concept only: this
shows the rover we are testing, not a deployed machine.

**nursery-crown-closeup.png**
Crown-level close shot, backlit leaves with the foliage falling out of focus
front and back. 100 mm, f/2.0. Works as a texture or section-break image.

**nursery-dusk-drone.png** (extra, optional)
Blue-hour variant from the dusk map: drone silhouetted against a pale dusk sky
with mist sitting in the rows. 35 mm, f/2.8. The drone's nav lights are on in the
scene but do not read against the bright sky, so do not caption it as lights-on.

## Web versions

1600 px wide WebP, each under 200 KB, for the three recommended site slots:

- `nursery-golden-wide-drone-1600.webp` (1600 x 900, 168 KB)
- `nursery-aerial-threequarter-drone-1600.webp` (1600 x 900, 190 KB)
- `nursery-rover-row-concept-1600.webp` (1600 x 900, 192 KB)

## Revisions

September 16, second pass: the golden wide, the three-quarter aerial and the
dusk shot were re-rendered with the transport case removed from the drone mesh.
Same cameras, same lighting, same maps. The top-down and the rover shot were not
re-rendered and are unchanged.

`img/renders/*.png` is in the site repo's `.gitignore`; only the WebP versions
and this file are meant to be committed.

## Hero loop video

`img/hero-loop.mp4` (1920 x 1080, H.264 yuv420p, **7.80 s**, 30 fps, 234 frames,
no audio track, 3.37 MB), `img/hero-loop.webm` (VP9, 3.02 MB) and
`img/hero-loop-poster.jpg` (1920 x 1080, 214 KB, the last held frame).
The 4K master is kept outside the repo at
`/home/lucas/UE5/orchard_runs/run_nursery_v4/cinematic/brand_stills_20260916/hero-loop-4k-master.mp4`
(3840 x 2160, CRF 17, 41 MB).

There is no fade in and no fade out. The loop seam is a 0.6 s crossfade instead:
252 frames are composited, and the delivered 234 frames dissolve their first 18
from the tail of the source back into the head
(`out[i] = lerp(src[234+i], src[i], i/18)`), which is continuous both across the
restart and at the end of the dissolve. The drone holds the same screen position
throughout, so it does not ghost during the dissolve; what dissolves is the built
overlay clearing back to a clean field. `build_loop.py` does this.

Timeline: the sweep starts at 0.5 s, every tree is acquired and the counter reads
**282 / 282** by 6.5 s, and the fully built overlay holds for the last 1.3 s.
The total is 282 rather than the 300 of the earlier long cut because the shorter
shot travels over fewer rows; it is still the true number of trees the sweep
reaches, not a chosen figure.

The rotors spin. The source FBX bakes the props into the airframe, but the same
asset folder ships a split export, so the hero drone is built from
`SM_M300_Body_NoProps.fbx` plus `Prop_PP.fbx`, whose pivot is its own hub. Four
prop actors sit at the four motor positions, measured off the airframe mesh by
`ue_hub_probe.py`, and their yaw is keyed per frame at about 180 to 195 degrees
per frame with alternating direction per motor. MRQ derives its shutter from the
post-process motion blur amount, which the stills grade sets to 0; the hero
camera overrides it to 0.5 for a 180 degree shutter, so the 16 temporal samples
spread across the shutter and the blades render as blurred discs instead of
freezing. That shutter also gives the glide its own natural motion blur. Only
the hero drone is built this way; the stills keep the single combined mesh.

The base is a clean MRQ render of `SEQ_HeroGlide` from the same
`Nursery_BrandGolden_20260916` map and the same lighting as the stills: 35 mm,
f/5.6, camera 16 m up pitched 40 degrees down, gliding forward along the rows.
The drone flies about 7.5 m ahead of and below the camera. Rendered at
3840 x 2160 with 16 temporal samples, same as the stills. The frame is full of
rows at every moment; no world edge is ever visible.

The overlay is composited in post by `brand_stills_20260916/overlay_hero.py`, so
the render itself stays clean. Tree marker positions are the level's real world
positions, exported by `ue_export_trees.py` and projected through the same camera
keys the sequence was rendered with, so nothing is tracked or estimated.

The data layer, in the site's palette:

- A thin bright green sweep line crosses the rows with a soft 40 px gradient
  trail behind it. Trees light up as it passes.
- Each tree gets a point-cloud shimmer, a one-frame glitch bracket, then settles
  to a small green dot; the trees carrying an ID also keep a thin green bracket.
  Marker strokes are 2 px at 1080p with a soft glow so they hold against bright
  foliage.
- ID tags are white monospace on a 60 percent dark pill, scattered by a
  deterministic hash so no column or band ever tags together, capped at 12 on
  screen at once and kept clear of the counter block.
- A counter climbs to 282 / 282 with a thin green progress bar under it.
- The base is graded down 8 percent with a 15 percent corner vignette so the data
  layer sits on top without changing the look.

There are no heights, calipers or any other numbers that could read as
measurements, and no branding anywhere in frame.

Verification, all extracted from the delivered `hero-loop.mp4` and inspected:
timeline frames in `brand_stills_20260916/hero_verify/` (`01_start_0.03s.jpg`,
`02_scan_0.70s.jpg`, `03_midbuild_3.50s.jpg`, `04_full_6.60s.jpg`,
`05_lastheld_7.76s.jpg`), and the seam in
`brand_stills_20260916/seam_check/` (last three frames `last_01..03.jpg`, first
three `first_01..03.jpg`, and mid-dissolve `mid_6/9/12/16.jpg`). First and last
frames measure mean luma 70.4 and 70.8, so neither end goes to black. Rotor
crops from the clean render, before any compositing, are in
`brand_stills_20260916/rotor_check/`; drone crops from the finished piece are
`hero_verify/06_drone_crop_4kmaster_5.00s.png` from the previous cut.
