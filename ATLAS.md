## Meta
| Field | Value |
| Project | Splash and Scrub |
| Last Active | 2026-09-18 |
| Status | shipping |
| Location | /home/wner/splash-and-scrub |
| Repo | jimmyardis/splash-and-scrub (public) |
| Live URL | https://jimmyardis.github.io/splash-and-scrub/ |

## Current State
Live on GitHub Pages, verified by a byte-for-byte diff of the deployed page
against the local file. One self-contained `index.html` (~7.0 MB)
for the Irmo, SC car and boat wash at 1016 Rauch-Metz Rd: inlined CSS, embedded
SVG favicon, and art baked in as data URIs, so there are no external assets to
break. Only outbound links are the `tel:` number (803-834-0367) and a Google
Maps directions link; everything else is in-page anchors, including a separate
mobile nav. The file was authored elsewhere and pushed as delivered — no edits
to the markup.

## Next Action
Decide whether the site gets a custom domain (e.g. splashandscrubirmo.com) or
stays on the github.io URL; a domain means a CNAME file plus Namecheap DNS.

## Blockers
None.

## Open Questions
- Custom domain, or is the github.io URL fine for now?
- Are the hours, prices, and bay/service details on the page confirmed by the
  owner, or still placeholder copy?
- Does the business want Google Business Profile and Search Console set up, the
  way Lake Murray Tree Service was?
- Any real photos of the bays to swap in for the illustrated art?

## Session Log
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
