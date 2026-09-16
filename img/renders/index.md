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
