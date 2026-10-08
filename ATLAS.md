## Meta
| Field | Value |
| Project | Splash and Scrub |
| Last Active | 2026-10-08 |
| Status | shipping |
| Location | /home/wner/splash-and-scrub |
| Repo | jimmyardis/splash-and-scrub (public) |
| Live URL | https://splashandscrubsc.com/ |

## Current State
Live at https://splashandscrubsc.com on GitHub Pages (HTTPS, apex domain). One
self-contained `index.html` (~8.8 MB, all art as data URIs). As of 2026-10-08 it
is hand-edited in the repo: the original painted design is kept, but the hero
now uses the boat photo (desktop and mobile) with real HTML headline and buttons,
the location panel has a live Google Maps embed, and the gallery's RV slot shows
a real photo of the bays and vacuums.

## Next Action
Confirm with the owner that the hours, prices, and service details on the page
are final rather than placeholder copy.

## Blockers
None.

## Open Questions
- Are the hours, prices, and bay/service details on the page confirmed by the
  owner, or still placeholder copy?
- Does the business want Google Business Profile and Search Console set up, the
  way Lake Murray Tree Service was?
- More real photos to replace the remaining illustrated art (soapy car, SUV)?
- Retire the separate boat-hero repo now that production has the boat hero?
- The page has no canonical or `og:url` tag; worth adding in the next delivered
  build now that there is a real domain?

## Session Log
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
