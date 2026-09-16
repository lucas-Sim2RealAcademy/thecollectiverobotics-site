# Collective Robotics Inc. one page site

Static site built from `docs/plural-robotics/collective-robotics/website-spec-2026-09-16.md`.
No framework, no build step, no JavaScript, no analytics, no cookies.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole page. All copy comes verbatim from section 2 of the spec. |
| `style.css` | All styling. The nine palette variables sit at the top of the file. |
| `fonts/` | Self hosted woff2, latin subsets. Outfit variable (wordmark), Poppins 600 and 700 (headings), Inter 400 (body). |
| `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`, `icon-512.png` | The segmented C alone, black on white. |
| `og.png` | 1200 by 630 link preview card. Black ground, white lockup, one line of text. |
| `img/` | Four WebP images, each under 150 KB. |
| `screenshot-1280.png`, `screenshot-375.png` | Local previews only, not pushed. |

Page weight is about 88 KB before images and about 603 KB with them, fonts included.

## Brand notes

The segmented C is an inline SVG, defined once in `index.html` under `#c-mark` and reused
everywhere. It is a single stroked circle with a dash pattern, so it scales cleanly and there is
no image file to keep in sync. The header and footer use the horizontal lockup, mark at cap
height with "Collective" bold and "Robotics" light and letterspaced. The version with one segment
in nursery green appears once, in the hero, and nowhere else.

The oversized C motif appears once, cropped off the right edge of "What we are building next".

## Images

Four images ship with the page and one placeholder remains.

| File | What it is | How it is labeled |
|---|---|---|
| `img/rows-render.webp` | Hero. A nursery block from the project's own simulation. | Caption says "Simulation", concept render, not a photograph. |
| `img/map-example.webp` | The example tree record on a phone. | Caption says "Example", plus the imagery attribution line. |
| `img/collect-render.webp` | The ground robot moving down a row. | Caption says "Simulation". |
| `img/ground-robot-render.webp` | The ground robot in a row, front view. | Caption says "Concept render". |

Nothing on the page is presented as a photograph of a real farm. There are no real farm photos on
this machine yet. When the shot list is shot, the renders should be replaced by the real frames and
the "Simulation" captions removed.

One placeholder plate remains, in "Who is behind this": a candid portrait of Lucas in the rows.

### The tree record example image

`img/map-example.webp` is built, not photographed. The base layer is real aerial imagery from the
USDA NAIP program, which is public domain, pulled from the USGS NAIP Plus ImageServer:

```
https://imagery.nationalmap.gov/arcgis/rest/services/USGSNAIPPlus/ImageServer/exportImage
  ?bbox=-84.10790,32.89430,-84.10510,32.89660&bboxSR=4326&imageSR=4326
  &size=870,852&format=png&f=image
```

That is a field grown block in middle Georgia, cropped tightly to rows so that no building, road,
sign, or boundary that could identify a business is in frame. The service reports a native ground
sample of 0.3 m. The tile was rotated so the rows run vertically, then a window was cropped and
scaled up about three times, so the base is soft. That is the real limit of public aerial imagery
at phone zoom.

Over that base sit the species colored circles, one per tree, placed on rows and tree positions
detected from the imagery itself, the row labels, the selected tree ring, the record card, and the
legend. Every number in it is an example and the image is stamped "Example". No Google, Bing,
Apple, or Mapbox imagery is used anywhere.

The attribution line "Aerial imagery: USDA NAIP (public domain)" sits under the image on the page
and must stay with it.

### Replacing images

Export at 1600px wide or less, WebP, under 150 KB each, with `width`, `height`, `alt`, and
`loading="lazy"` on everything except the hero. Do not use `decoding="async"`, it makes headless
screenshots capture before the image paints. No farm name in any file name or alt text.

## Accent color

Nursery green, option A in the spec. To switch to safety orange, edit three lines in `style.css`:

```
--accent:#E04E1B;
--accent-hover:#B93D12;
--accent-tint:#FBEDE7;
```

If orange is chosen, link text on white must use `#B93D12` and orange may never carry text
smaller than 18px.

## Copy rules that bind any future edit

No customer claims, no accuracy numbers, no percentages, no pricing, no farm names anywhere
including file names and alt text, no cofounder names, no em dashes or en dashes, and none of
these words: GIS, geospatial, orthomosaic, point cloud, SLAM, photogrammetry, AI, machine
learning, platform. The three parts idea appears exactly once, in the "What we are building next"
intro line.

## Deploy status

Preview only, on GitHub Pages at the repo's github.io URL. There is deliberately no `CNAME` file
and no DNS has been touched. The custom domain cutover below is a separate step that Lucas
authorizes.

## DNS records to add, ready to paste

Records live at Squarespace Domains, reachable from the Google Admin console under Account, then
Domains, then Manage domains, or from domains.squarespace.com using the Google account.

Screenshot the full existing record list before editing. Add these. Delete nothing, except an
existing Squarespace parking or default A record on `@` if one is there.

Four A records, host `@`, default TTL:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Four AAAA records, host `@`, default TTL:

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

One CNAME:

```
Host: www    Value: lucas-Sim2RealAcademy.github.io.
```

Note the CNAME value is the account's github.io hostname with no repository name after it.
Do not add any wildcard record.

### Do not touch

Leave the MX records exactly as they are. Leave the SPF TXT, the DKIM record on
`google._domainkey`, the DMARC record on `_dmarc`, and the `google-site-verification` TXT exactly
as they are. Do not move nameservers. The domain's only current job is carrying
lucas@thecollectiverobotics.com and no website is worth risking that.

### Cutover order, when Lucas says the word

1. Add a `CNAME` file at the repo root containing exactly `thecollectiverobotics.com`.
2. Settings, Pages, custom domain: enter `thecollectiverobotics.com`, save, wait for the DNS
   check to go green.
3. Tick Enforce HTTPS. It can take up to 24 hours to become available.
4. Verify email is untouched: `dig MX thecollectiverobotics.com +short` and
   `dig TXT thecollectiverobotics.com +short` match the screenshot taken before the edit.
5. Send a test message to lucas@thecollectiverobotics.com from a Gmail account and confirm it
   arrives.
6. Load all four: `http://thecollectiverobotics.com`, `https://thecollectiverobotics.com`,
   `http://www.thecollectiverobotics.com`, `https://www.thecollectiverobotics.com`.
7. Paste the link into a text message and check the preview card renders.
