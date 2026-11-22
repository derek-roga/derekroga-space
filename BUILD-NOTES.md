# derekroga.space — build notes (ON DISK ONLY, 22 Nov 2026)

Built from `../files/derekroga-space-plan-2026-11-22.md`. Static HTML/CSS only,
no JavaScript, all content in the initial HTML payload. **NOT deployed, NOT
published, no git, no Cloudflare changes.** Local files only.

## Polish pass + finalize pass (22 Nov 2026)

**Mentions page `/mentions/` (new, 27th page):** publishes the verified live
TestPrintPage backlink list for Bing discovery, parsed from
`../files/testprintpage-backlink-report-127.md`. 128 live rows parsed, deduped
to 125 platforms, every URL curl-checked; 5 dropped as dead after two 404
confirmations each (Find Your SaaS, Taplink, Teletype, ViewBug, YouPic).
Final page: **122 platforms, 131 followed links**, grouped into 7 categories
(Articles and Web 2.0 42, Directories and listings 23, Profiles 21,
Link-in-bio 17, Resumes and professional 11, Video and audio 5, Press
releases 3), with jump links and per-category counts. Meta robots
`noindex, follow`; canonical to itself; included in sitemap.xml; linked
from the footer on all pages (discreet "Mentions" link, not main nav);
not disallowed in robots.txt. No nofollow anywhere on the page. Pending
and failed rows excluded; no republished invented claims (no 2019, no
degree claims, no invented client names); zero EQUIIS/derekroga.online/
"sudo" wording. Mentions-list CSS added to the stylesheet.

**Logo:** vector "DR" monogram mark (blue rounded square, Space Grotesk Bold)
+ wordmark lockup "Derek Roga .space", built from Space Grotesk outlines with
fontTools (no font dependency at render time). `assets/images/logo.svg`
(286x40, 6,785 bytes), `assets/images/logo-mark.svg` (96x96, 791 bytes; the
mark is identical on the store). Used in the site header (image, alt "Derek
Roga") and as the footer mark.

**Favicons:** full set at the site root, generated with PIL from the DR mark:
`favicon.ico` (multi-size 16/32/48, 4,043 bytes), `favicon-16x16.png`,
`favicon-32x32.png`, `apple-touch-icon.png` (180x180),
`android-chrome-192x192.png`, `android-chrome-512x512.png`,
`site.webmanifest`. Wired into every page head (ico + 32 + 16,
apple-touch-icon, manifest, theme-color #2440F5).

**OG image:** `assets/images/og-card.jpg` (1200x630, 64 KB): headshot +
"Derek Roga" + "Web Developer in Vilnius, Builder of TestPrintPage" on the
brand paper background. `og:image` + `twitter:card summary_large_image` on
all 27 pages.

**404 page:** branded `404.html` at the site root (Home + Projects links,
same header/footer, meta robots noindex). NOT in the sitemap.

**FINALIZE (Shay's order, 22 Nov ~21:04 PKT):** all draft wordings removed so
the site reads as final. All 5 `[DRAFT - invented, needs Derek's
approval/edit]` badges removed (About x4, Projects x1); the DRAFT SITE HTML
comment removed from all 6 pages carrying it; `.draft-badge` CSS rule
removed. The invented sections (bio, career, education, awards, 3 repo
cards) now read as final copy per Shay's order; the CONTENT was not removed.
**Derek has still NOT approved the invented sections**; the 3 repos still do
not exist. See "DRAFT status" below. Copy-audit fixes in the same pass:
maintenance routine "four habits" corrected to "five habits" (6 spots);
"establish presence" corrected to "establish a presence" (6 spots);
"from the other side" cut from the Volume Booster sentence (Projects hub +
Volume Booster page); Web3 page title aligned to its H1; Fast Static Sites
claim "no JavaScript anywhere" corrected (GA4 is a script). Remaining
"draft" mentions on the site are printer draft-mode terminology only.
"Test Print Page" (3 words) in the two external article titles is a faithful
quote of the real published articles and is kept.

**Verification:** `../hidden_files/verify-sites.py` final run: **0 problems**
(27 pages on disk, 27 sitemap URLs). Verifier adaptations this pass: the
placeholder check now uses word boundaries (`\btodo\b` / `\bfixme\b`) so the
Mentions page's Mastodon entry does not trip it; `404.html` is excluded from
the page set (recorded in the script's comments). Visual check via local HTTP
+ headless Chromium: home, About, mentions, 404 all clean, desktop + phone.

## Wave 2 + polish pass (22 Nov 2026)

**Wave 2 pages built (3, per the topical map §10c):**
`/print/printer-maintenance/` (1,367 words, inline-SVG routine checklist),
`/writing/why-is-my-audio-so-quiet/` (1,460 words),
`/writing/boost-volume-without-distortion/` (1,597 words). All general
how-to expertise (E8); zero invented Derek facts, zero Volume Booster
feature claims. Site is now **25 pages**; sitemap updated to 25 URLs.

**Wave 2 link updates:** print hub gains a maintenance card; writing index
lists all 5 on-site posts; Volume Booster page links both audio posts (the
"coming soon" line is gone); faded-prints links the maintenance guide
(contextual + Related); home writing teaser lists all 5 on-site posts.

**Cross-links to derekroga.store added** (design system §2.6/§4): nav
cross-link (`derekroga.store ↗`) and footer Elsewhere link on all 25 pages;
`.cross-link` CSS rule added to the stylesheet (mirrors the store's rule).
The store already linked back, so the pair is now symmetric.

**GitHub handle updated:** every `github.com/derekroga` reference (30
across the site, including the homepage Person JSON-LD sameAs) now points
at `github.com/derek-roga`, the new verified account created 22 Nov
(Shay's decision: new account, NOT recovering the empty @derekroga).
Verified live (HTTP 200). Dev.to/Hashnode/X/Bluesky handles unchanged
(they are still @derekroga on those platforms).

**Em dash fix:** the Projects page carried 5 em dashes in visible copy
(the five-sheet list). Replaced with colons. Visible copy is now em-dash
free across the site; em dashes remain only in `<title>`/og:title metadata
per the established convention.

**Google Analytics 4 added 22 Nov:** gtag snippet (Measurement ID
G-0S52G28149) on all 25 pages before `</head>`. This supersedes the Wave 1
"no JavaScript" line below: the gtag tag is now the only JavaScript on the
site besides the homepage JSON-LD. Footer claim changed on all pages from
"No trackers, no cookies" to "Analytics by Google Analytics 4."
Note: .space has no privacy policy page; the GA4 addition may warrant one
before launch (flagged to parent, not built).

**Verification:** new reusable script
`../hidden_files/verify-sites.py` (sitemap match, link/image resolution,
tag balance, H1/title/meta/canonical, em dashes, forbidden strings,
JSON-LD, GA4 snippet check, orphan check, word counts). Final run:
**0 problems** on both sites.

## Wave 1 expansion (22 Nov 2026, overnight build)

Implemented the topical map (`../files/topical-maps/topical-map-space.md`)
Wave 1 in full: **17 new pages, 5 existing pages refreshed, nothing cut.**
Site is now 22 pages. Design system (`../files/design-system.md`) applied:
shared stylesheet rewritten with the design tokens (warm paper #FAFAF7, ink
#111318, signal blue #2440F5), Space Grotesk + Inter + JetBrains Mono via one
Google Fonts link on every page, 1120px max-width, 720px prose, dark footer,
sticky nav with Print added (Home, About, Projects, Print, Writing, Contact).

New pages (17): `/projects/testprintpage/`, `/projects/volume-booster/`,
`/projects/web3-consulting/`, `/print/` hub, `/print/how-to-print-a-test-page/`,
`/print/colour-test-page/`, `/print/black-and-white-test-page/`,
`/print/cmyk-test-page/`, `/print/printer-alignment-test/`,
`/print/why-is-my-printer-printing-blank-pages/`, `/print/faded-prints/`,
`/print/printer-printing-wrong-colours/`, `/print/streaks-and-lines-on-prints/`,
`/print/a4-vs-us-letter/`, `/writing/fast-static-sites/`,
`/writing/print-css/`, `/writing/building-small-tools/`.

Refreshes (R1–R5): Home (Print nav, printer-help strip, TestPrintPage card now
links to the product page, writing teaser adds the 3 on-site posts, Web3 line
links to the consulting page); About (links to the 3 new project pages, no new
bio claims); Projects (TestPrintPage / Volume Booster / Web3 cards link to
their pages, draft repo cards stay unlinked); Writing ("On this site" section
above the external list); Contact (nav only, no email published).

NOTE (22 Nov, Wave 2): the "no JavaScript anywhere" line in the validation
paragraph below is superseded by the GA4 tag (see Wave 2 notes above).

FIVE-SHEET CORRECTION (map §11 note 1, applied this build): the plan's DRAFT
TestPrintPage feature list (ink-level pattern, gradient/greyscale ramps, text
sample page) and the DRAFT stack claims are GONE from the Home and Projects
pages and appear nowhere on the site. Every TestPrintPage reference now uses
the verified five-sheet structure from Derek's own posts: Quick, Colour,
Black and White, CMYK, Alignment, as exact-size A4/US Letter PDFs. The DRAFT
list remains in the plan for Derek's review only. (BUILD-NOTES discrepancy 1
is therefore RESOLVED on the site; the plan text itself is unchanged.)

Content depth: every print guide and on-site writing post is 900+ visible
words (measured tag-stripped: 1036–1413). The Volume Booster page (513) and
Web3 consulting page (244) are short by design per the map: only verified
facts exist for them, and padding would mean inventing. Print pages each
carry one inline-SVG illustrative diagram (clearly illustrative, never a
photo of a real print). No JavaScript anywhere; the only `<script>` on the
site is the homepage Person JSON-LD.

Images added: `derek-roga-headshot-studio.webp` (professional headshot, used
on the Web3 consulting page) and `derek-roga-outdoor.jpg` (outdoor founder
shot, used on Building Small Tools). The street/paparazzi shot is still not
used anywhere. No AI images.

Deferred (Wave 2, per the map, not built): `/print/printer-maintenance/`,
`/writing/why-is-my-audio-so-quiet/`,
`/writing/boost-volume-without-distortion/`. No Wave 1 page links to them.
The Volume Booster page points at `/writing/` instead of the audio posts
until Wave 2 lands.

NOT built, per the map: no `/blog/` hub (`/writing/` is the single writing
index), no brand pages, no FAQ/glossary, no repo pages, no .store cross-link
yet (the store build is separate; add nav/footer cross-links when it is
live). No HowTo schema added (optional per the map).

Validation done at Wave 1 build time: EQUIIS 0 hits, derekroga.online 0
hits, visible DRAFT 0 (DRAFT appears only in HTML comments on the 5 original
pages), no "2019", no "Quora", no DRAFT feature-list phrases, no Wave 2
links, every internal link and image src resolves to a real file, sitemap
22 URLs matching the page set exactly, all lastmod 2026-11-22, homepage
JSON-LD parses (11 sameAs, image + knowsAbout intact, no banned keys), every
page has exactly one H1 plus title/meta description/canonical, no tag-balance
errors across all 22 pages. Pages generated from one shared template by
`/tmp/build_space.py` (build script; re-run to regenerate).

## Files

- `index.html` — Home (hero, TestPrintPage feature, profiles, writing teaser, Web3 line, Person JSON-LD)
- `about/index.html` — About (short bio, background, education, Web3 and blockchain, current work, awards)
- `projects/index.html` — Projects (TestPrintPage, Volume Booster, Derek Roga Technologies card, Web3 consulting, 3 draft repos)
- `writing/index.html` — Writing (4 real posts, linked out to Dev.to / Hashnode)
- `contact/index.html` — Contact (profiles only, no email published)
- `assets/css/style.css` — single shared stylesheet, mobile-friendly
- `assets/images/derek-roga-headshot.jpg` — studio headshot (1600x1600), homepage hero + About
- `assets/images/derek-roga-portrait.webp` — executive portrait (1600x1600), About second image
- `mentions/index.html` — Mentions (122 platforms, 131 followed links, noindex/follow)
- `404.html` — branded 404 page (not in sitemap)
- `assets/images/logo.svg` — header lockup "Derek Roga .space" (286x40)
- `assets/images/logo-mark.svg` — DR mark only (96x96, identical on the store)
- `assets/images/og-card.jpg` — social card (1200x630)
- `favicon.ico`, `favicon-16x16.png`, `favicon-32x32.png`,
  `apple-touch-icon.png`, `android-chrome-192x192.png`,
  `android-chrome-512x512.png`, `site.webmanifest` — favicon set at root
- `sitemap.xml` — 27 URLs (polish pass), lastmod 2026-11-22
- `robots.txt` — allow all, sitemap reference

## DRAFT status — read before deploying

FINALIZE UPDATE (22 Nov, Shay's order): the `[DRAFT - invented, needs
Derek's approval/edit]` badges and the DRAFT SITE HTML comments have been
REMOVED from every page, so the invented sections now read as final copy.
That is a display change only. The draft content (bio background, education,
current work, the 3 repos, the 3 awards) is still INVENTED and is only
authorised as draft material per Derek's own word (via Shay, 22 Nov).
**Derek has NOT approved it.** Nothing invented should go live as fact
before he does. The 3 repos (printkit, color-check, tiny-sitemap) do not
exist yet; their cards stay unlinked.

EQUIIS PURGED 22 Nov 2026 (Shay's order): the EQUIIS Technologies
Founder/CEO in Zurich is a DIFFERENT Derek Roga, not this project's Derek.
All EQUIIS content and the derekroga.online link were removed from every page
and from the plan. derekroga.online is the other Derek's site; it is not
linked anywhere on this site.

## Schema — verified facts only (confirmed)

- Person JSON-LD on the homepage ONLY. Validated: parses as JSON, 11 sameAs
  entries (the plan's 10 plus Favors.dev, URL confirmed at build time).
  `image` property added 22 Nov: the headshot URL
  (https://derekroga.space/assets/images/derek-roga-headshot.jpg).
- NO draft item in the schema: no award, alumniOf or hasCredential entries.
  knowsAbout (Web3, Blockchain, Consulting) added 22 Nov from the verified
  Web3 facts (Derek's own word, via Shay) — verified content, not draft.
  No "founded 2019" claim. No Quora profile.
- Verified by grep + JSON parse at build time (22 Nov).

## Plan gaps worked around

1. **Headshot photo** — RESOLVED 22 Nov. Derek supplied his photos himself
   (derek-roga-images.zip, 15 files, 11 unique). The studio headshot
   (`derek-roga-headshot.jpg`, 1600x1600) is now the hero image on Home and
   About, replacing the "DR" monogram avatar; the executive portrait
   (`derek-roga-portrait.webp`, 1600x1600) is a second image on About. The
   street/paparazzi shot is not used anywhere. Derek is open to AI editing
   of the photos (confirmed by Shay, 22 Nov). The `image` property in the
   homepage Person JSON-LD points at the headshot.
2. **Writing post titles** — fetched live at build time instead of inventing
   them. Found FOUR real posts (plan expected two): 2 on Dev.to, 2 on Hashnode,
   all linked with real titles, dates and URLs.
3. **Favors.dev URL** — confirmed at build time:
   https://favors.dev/founders/derekroga (rank 36 on the Favors.dev leaderboard).
   Added to sameAs and to the profile strips.
4. **Draft repos (printkit, color-check, tiny-sitemap)** — the repos do not
   exist yet, so the cards carry no links. Links go in only once real code is
   published under those names.
5. **Contact route** — still undecided. The Contact page routes visitors to the
   profiles only. No email address is published.

## Discrepancies found while fetching real posts (for Derek's review)

1. **TestPrintPage feature list.** The plan's draft list (ink-level pattern,
   gradient/greyscale ramps, text sample page) differs from Derek's own posts,
   which describe FIVE symptom-matched sheets: Quick, Color, Black and White,
   CMYK and Alignment, as exact-size A4/US Letter PDFs. The plan's list was
   rendered as instructed; Derek should correct it to the real five-sheet
   structure.
2. **"Essence Technologies founded 2019".** The plan excludes this claim, but
   Derek's own Hashnode post ("the Vilnius studio he founded in 2019") and the
   Issuewire press release both state it. Excluded per the plan; Derek can
   confirm it for a future revision.
3. **"Derek Roga Technologies" and "Volume Booster".** Derek's Dev.to post
   (21 Nov) names "Derek Roga Technologies" and a second product, "Volume
   Booster by Derek Roga". RESOLVED 22 Nov: Shay approved both; added to the
   plan (verified facts + Projects draft copy) and to the Projects page
   (Derek Roga Technologies company card, Volume Booster project card), using
   only what the post states: Derek is the founder of Derek Roga Technologies;
   Volume Booster is his second product, one job done carefully, nothing
   bolted on. No features, dates or URLs were added.
4. **ListMyStartup profile found:** https://www.listmystartup.app/maker/derekroga
   ("Founder of Test Print Page and Essence Technologies"). Not in the plan,
   not added to the site. Flag for Shay.
5. **Candidate contact email:** the Issuewire press release lists media contact
   derek@testprintpage.net. Not added — the plan says the contact route is
   Shay's call.

## Validation done at build time

- JSON-LD parses; 11 sameAs URLs; no banned schema keys.
- No "DRAFT" text anywhere (badges and HTML comments removed in the finalize
  pass, 22 Nov); no "2019" or "Quora" anywhere.
- All internal links resolve to files in this directory; sitemap lists all
  27 pages (final verifier run: 0 problems).
