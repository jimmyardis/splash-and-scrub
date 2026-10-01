## Meta
| Field | Value |
| Project | Splash and Scrub |
| Last Active | 2026-10-01 |
| Status | shipping |
| Location | /home/wner/splash-and-scrub |
| Repo | jimmyardis/splash-and-scrub (public) |
| Live URL | https://splashandscrubsc.com/ |

## Current State
Live at https://splashandscrubsc.com on GitHub Pages with HTTPS enforced; the
`www` host, plain `http`, and the old github.io URL all 301 to it. One
self-contained `index.html` (~7.0 MB) for the Irmo, SC car and boat wash at
1016 Rauch-Metz Rd: inlined CSS, embedded SVG favicon, and art baked in as data
URIs, so there are no external assets to break. The file was authored elsewhere
and pushed as delivered; the only repo-side additions are `.nojekyll` and `CNAME`.

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
- Any real photos of the bays to swap in for the illustrated art?
- The page has no canonical or `og:url` tag; worth adding in the next delivered
  build now that there is a real domain?

## Session Log
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
