## Meta
| Field | Value |
| Project | Splash and Scrub |
| Last Active | 2026-10-19 |
| Status | shipping |
| Location | /home/wner/splash-and-scrub |
| Repo | jimmyardis/splash-and-scrub (public) |
| Live URL | https://splashandscrubsc.com/ |

## Current State
Live at https://splashandscrubsc.com on GitHub Pages (HTTPS, apex domain). As of
2026-10-19 the page is `index.html` (~25 KB) plus `img/*.webp` (~1 MB, was 7.8 MB
of inline data URIs), with AutoWash JSON-LD, canonical/OG tags, `robots.txt` and
`sitemap.xml`. Hours read "Open 24 hours, 7 days a week" to match the Google
profile; phone 803.995.2206; Google Map embedded in the Location section.

## Next Action
Submit https://splashandscrubsc.com/sitemap.xml in Google Search Console and run
the page through Google's Rich Results Test to confirm the AutoWash schema.

## Blockers
None.

## Open Questions
- Prices and bay/service details: confirmed by the owner, or still placeholder?
- A future outside re-delivery of a self-contained index.html would undo the
  image split, schema and hours. Re-apply them rather than overwrite blindly.
- Does the business want Google Business Profile and Search Console set up, the
  way Lake Murray Tree Service was?
- More real photos to replace the remaining illustrated art (soapy car, SUV)?
- Retire the `splash-and-scrub-boat-hero` repo now that its version has been
  promoted to production and the boat-photo hero is the losing variant?
- The page has no canonical or `og:url` tag; worth adding in the next delivered
  build now that there is a real domain?

## Session Log
### 2026-10-19 (search + speed pass)
- Hours now match the Google Business Profile (open 24 hours): desktop contact
  block, mobile location + footer, FAQ split into hours/prices.
- Added AutoWash JSON-LD (name, address, phone, 24/7, areaServed), canonical,
  Open Graph/Twitter tags + img/share.jpg, robots.txt, sitemap.xml; title and
  description now say "24-hour".
- Moved all 25 inline images into img/*.webp (the two photos were embedded
  twice; resized to 900px). Lazy-loading below the fold and preloading the hero.
  The 7.8 MB page went down to 25 KB of HTML plus about 1 MB of images.
- The Map embed requested from the profile review was already in place (2026-10-08).
- No lat/long in the schema: the Census and OSM geocoders don't know the address.

### 2026-10-19
- Changed the contact phone everywhere on the page (meta description, schema,
  tel: links, visible text) from 803.834.0367 to 803.995.2206, at the user's
  request. Verified live on splashandscrubsc.com.

### 2026-10-13
- The client picked the logo hero. Replaced production's `index.html` with the
  file from `splash-and-scrub-boat-hero` (whose name is historical — it holds
  the logo-hero option) and pushed. `CNAME` and `.nojekyll` untouched.
- Diffed the two files with data URIs stripped before overwriting: the only
  difference is the `.boat-hero` overlay block and the mobile `.hero-art>.boat`
  rule. The Maps embed, the bays photo, and the gallery crop are present in
  both, so nothing from the 2026-10-08 session was lost in the swap.
- The boat-photo hero is not deleted — it stays recoverable at commit 55c39c4.
- Verified on the live URL with headless Chromium at 1440 and 390 wide: desktop
  shows the painted logo banner with the Get directions / View wash options
  hotspots, mobile shows the painted banner above the stacked headline.
### 2026-10-08
- Desktop hero: overlaid the boat photo (taken from the boat-hero repo) on the
  top ~70% of the painted #services panel, with HTML eyebrow, headline, and
  Get directions / View wash options buttons. The painted service cards stay.
  The old painted-button hotspots under it were removed, and a white mask hides
  the painted splash that had bled into the bottom of the header strip.
- Mobile hero: the painted logo banner was replaced with the boat photo. The
  existing headline, CTAs, and cards are unchanged.
- Replaced the gray map placeholder with a keyless Google Maps embed
  (`/maps/embed?pb=` by street address) and added the same map to the mobile
  location section. Searching by business name dropped the pin on "Storage
  Rentals of America", so the map uses the address only.
- Gallery slot 3 (RV) now shows the new bays/vacuums photo (IMG_0039, resized
  to 1536x864) on both desktop and mobile.
- Decision: hand-edited the file in the repo instead of waiting for a new
  delivery, as the owner asked. If an outside build is delivered later, these
  edits must be carried into it or they will be lost.
- Verified on the live URL with headless Chromium (desktop 1440 and mobile 390).
- Follow-up: re-cropped the bays photo (cut sky off the top, zoomed ~1.37x,
  shaped to the slot at 1536x986) so its asphalt/treeline and blue rooflines
  line up with the vacuum photo beside it. Page is now ~8.8 MB.
### 2026-10-01
- Moved the site to the custom domain `splashandscrubsc.com` (apex). DNS was
  already in place at Namecheap before this session: four GitHub Pages A
  records on the apex and `www` CNAME to `jimmyardis.github.io`.
- Added a `CNAME` file, pushed, set the domain through the Pages API, and
  turned on HTTPS enforcement once the certificate (apex + `www`, expires
  2026-12-30) showed as approved.
- Verified live: `https://splashandscrubsc.com/` returns 200 with the full
  6,959,469-byte page; `http://`, `www`, and the old github.io URL all 301 to
  it. `index.html` was not touched: it had no hard-coded github.io references.
### 2026-09-18
- Replaced `index.html` with `splash-and-scrub-updated.html` as delivered,
  committed, pushed, and confirmed the deployed page matches byte-for-byte
  (6,959,469 bytes) after the Pages build reported `built`.
- Diffed the new build against the old one with data URIs stripped: it adds a
  `max-width:640px` block that reworks the mobile hero (art bleed, stacked
  headline and CTAs, tighter header/nav) while leaving the desktop composition
  alone, adds a `.facility-photo` to the gallery (23 -> 24 images), and splits
  the headline to "CLEAN CARS." / "CLEAN BOATS." on two lines.
- Confirmed the phone number, street address, and both outbound links are
  unchanged, and that the file is still fully self-contained (no non-`data:`
  asset references).
### 2026-09-14
- Copied the delivered `index.html` out of Windows Downloads into a new repo at
  `/home/wner/splash-and-scrub`, added `.nojekyll`, committed, and created
  `jimmyardis/splash-and-scrub` as a public repo.
- Enabled GitHub Pages on `main` at root via the Pages API; polled until the
  build reported `built` and the URL returned 200.
- Verified the deployed page byte-for-byte against the local file and confirmed
  there are no non-`data:` asset references that could 404 in production.
- Chose a public repo deliberately: Pages on a private repo needs a paid plan,
  and this matches the pattern used for the other client sites.
