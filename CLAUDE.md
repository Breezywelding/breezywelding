# Breezy Welding — Website Project

Single-page marketing website for Breezy Welding, a custom welding shop (Bryan) serving the
Phoenix metro. Almost everything lives in `index.html`; `thanks.html` is the form redirect page
and `images/` holds real project photos. No build step, no dependencies, no framework.

## Business facts (real data — do not invent or change without owner confirmation)

- Owner: Bryan, welder/fabricator
- Phone (call/text): (480) 359-5197 — Google Voice business number (Mesa, AZ; set up
  Jul 20 2026, restored across the site the same day). Bryan's personal cell was published
  at launch but removed Jul 19 2026 and scrubbed from git history; never publish it
  anywhere (this repo is public, so keep those digits out of these docs too).
- Email: breezywelding@gmail.com
- Service area: Phoenix metro — Mesa, Gilbert, Chandler, Tempe, Scottsdale, Queen Creek
- Hours: Mon–Sat 7:00 AM – 6:00 PM
- Services: RV gates, single/walkway gates, garden trellises, custom fabrication & repairs

### Pricing shown on the site (verify with owner before any change)
RV gates starting at $2,400 · Single/walkway gates starting at $1,200 · Trellises starting at $350.
FAQ promises firm quotes ("the number we give you is the number you pay") and 1–2 week
fabrication + install after deposit. Keep those promises consistent if pricing copy changes.

## Quote form (FormSubmit)

The hero quote card posts to https://formsubmit.co/breezywelding@gmail.com — no account needed.
It uses a honeypot spam field (`_honey`), table-formatted email (`_template=table`), captcha off,
and a `_next` redirect to `thanks.html` (set by the inline script at the bottom of index.html so
it works on any domain).

**Outage fallback (added Jul 2026 after formsubmit.co went down with a Cloudflare 522):** the
inline script intercepts submit and posts to FormSubmit's AJAX endpoint with a 12s timeout; on
success it redirects to thanks.html, on any failure it shows `#form-fallback` in the quote card
(call/text number + a mailto link prefilled with the form fields) so leads aren't lost while
FormSubmit is down. With JS disabled the form still posts natively. If FormSubmit keeps having
outages, consider switching to Web3Forms or Formspree. **One-time activation:** the first-ever submission sends a confirmation
email to breezywelding@gmail.com; Bryan must click the activation link before submissions arrive.
Activation is tied to the email, not the domain, so a localhost test submission works.

## Logo

`images/logo.png` — the real Breezy Welding badge (welder + "Mobile Welding & Metal
Fabrication" arc + "BREEZY WELDING" banner), processed Aug 2026 from Bryan's original
(OneDrive\Pictures\My logo.jpeg): near-black background keyed to transparent + trimmed, so
it sits on the dark header. Shown ~64px tall in the header (50px on mobile). If the logo is
re-exported, re-run the transparency/trim (scratchpad make-logo2.ps1 pattern). The tagline
mentions "Mobile Welding" — a real service angle not yet worked into the site copy.

## Design system (industrial/trade — keep this identity)

- Colors (CSS variables in :root): steel dark #1c1f24 / #262a31, spark orange #f57c1f /
  #d9660e, sand #f6f1ea, white bg
- Fonts: Oswald (headings, uppercase) + Inter (body), via Google Fonts
- Tone of copy: plain, direct, tradesman voice ("We're welders, not salesmen"). No hype.
- Missing images fall back to a dark steel color, so the site still renders fine without photos.

## Structure of index.html

Sticky dark header → hero (photo bg + quote form card) → 3 service cards with starting prices
→ why-us (dark section, 4 icons) → gallery (9 photo tiles with captions) → 3-step process
→ reviews (3 placeholder testimonials) → FAQ (details/summary accordions) → orange CTA band
→ footer → sticky mobile call/quote bar (shows under 900px).

## Photos

Real project photos in `images/` (from Bryan's iCloud share, July 2026):
gate-single-1 (hero bg, single-gate card, gallery 1), gate-rv-1/2, trellis-1, trellis-pots,
trellis-poolside (also CTA band bg), trellis-bougainvillea, trellis-modern, trellis-desert,
shop-fabrication. `trellis-row.jpg` and `trellis-vines.jpg` are in the folder but currently unused.

## Backlog / next tasks

1. Replace the three placeholder testimonials with real customer quotes as they come in.
2. Adjust service-area cities in FAQ + footer if Bryan's actual coverage differs.
3. ROC license: if Bryan gets licensed with the AZ Registrar of Contractors, add the number to
   the footer (big trust signal in AZ). Footer currently says "Licensed & Insured" — confirm
   that claim with Bryan or soften it.
4. JSON-LD has no street address (shop address unknown) — add a PostalAddress if Bryan wants
   the shop or a service-area base listed; helps local search.
5. Google Business Profile (learning from earthlight-lash, where the 5.0 x 37-review Google
   listing became the site's main trust signal): if Bryan sets one up, add the rating badge,
   aggregateRating JSON-LD, and a sameAs Maps link, and swap placeholder testimonials for
   real review quotes.
6. Facebook ads (in progress Jul 20 2026): Meta Ads for the Breezy Welding AZ page.
   - Ad account 603112911108501 (the "Breezy Welding" one from an earlier attempt) is reused;
     ads post AS the Breezy Welding AZ page (page 1187611191097402) via identity selection —
     ad accounts aren't page-locked. Budget: $10/day. Plan: Leads objective + Instant Form,
     Phoenix-metro geo, service-area cities.
   - Creatives built (images/ads/, generated by scratchpad make-ads.ps1 from on-disk photos):
     ad-trellis-square/vertical (bougainvillea vertical is the standout), ad-gate-square/vertical.
     1080x1080 + 1080x1350, brand overlay w/ price anchor + (480) 359-5197 CTA. Auto-fits price
     text to width. Regenerate/add concepts by editing make-ads.ps1. Bryan has BETTER trellis
     photos (window-grid panels, poolside waterfall) to drop into images/ads/ when available.
   - Discarded the unpublished $100/day "Trellises" draft Jul 20 2026 (Discard drafts confirmed).
     Two already-published Marketplace boosts remain but are inactive: "[Trellises] Marketplace
     listing boosted 12/2/2025" (Off) and "[Custom Steel Trellis Sets] ... 4/26/2026" (Completed),
     both $0.00 spent. Harmless; leave or delete individually if Bryan wants a clean slate.
   - Payment method IS on file (verified Aug 9 2026) on ad account 603112911108501. "No payment due
     at this time", no spending limit set. Card details deliberately not recorded here: this repo is
     public. Check them in Ads Manager > Billing if needed.
   - **Campaign draft built Aug 10 2026** (campaign 120249244621050637, adset
     120249244621070637, ad 120249244621060637). Status: In draft, NOT published.
     Campaign "Trellises & Gates - Leads - Phoenix Metro": Leads objective, Advantage+ leads
     on, campaign budget $10.00/day, Highest volume bid.
     Ad set "Phoenix Metro - Homeowners 28+": Instant forms conversion, page Breezy Welding AZ,
     Maximize number of leads, location Phoenix AZ +25mi (audience ~12M), "Reach more people
     likely to respond" UNCHECKED on purpose (it expands nationally; customers must own local
     property).
     Ad "Trellis - Bougainvillea Vertical": one vertical trellis photo from the account library
     (1537x1921), CTA "Get quote", Spanish auto-translation left ON (big Phoenix market —
     turn off if Bryan can't serve Spanish-speaking callers). Declined Meta's AI-generated
     images and AI "visual touch-ups": the site's promise is real projects, no stock photos.
   - **BLOCKER (Bryan must do, legal agreement):** "Terms of Service Not Accepted: You can't run
     lead ads until your Facebook Page accepts Facebook's Lead Generation Terms of Service
     (#1815089)." Accept via the Edit button on the error, or Page Settings > Lead Ads Terms.
     The Instant form itself can't be created until that's accepted, so the ad still needs a
     form attached afterward.
   - Note: mcp file_upload failed in this environment, so the branded ad2-*.jpg creatives in
     images/ads/ were NOT uploaded; the ad uses a clean library photo instead (clean photos
     often outperform text-heavy overlays anyway). Upload the branded ones manually to A/B test.
   - **Two ChatGPT flyer creatives added Aug 11 2026** (sources: the two `ChatGPT Image Aug 11,
     2026, 06_0*.png` files in images/ads/, 1086x1448 and 1402x1122). Both put the logo at the
     very top edge and the (480) 359-5197 CTA band at the very bottom, so Meta's auto-crop would
     clip them. Refit onto Meta-native canvases by scaling to fit and letterboxing on near-black
     (#0a0a0a), which matches the ads' own black field and is nearly invisible:
     - `ad3-built-strong-4x5.jpg` 1080x1350 — "BUILT STRONG. MADE TO LAST.", 34px side bars only
       (source was 3:4, almost 4:5 already). Best of the set; 4:5 owns the most mobile feed space.
     - `ad3-elevate-1x1.jpg` 1080x1080 — "ELEVATE YOUR OUTDOOR SPACE.", 108px top/bottom bars.
       Source is 5:4 landscape, so square costs the least padding; a 4:5 version wasted 36% of
       the canvas on black and was discarded.
     - `ad3-built-strong-1x1.jpg` 1080x1080 — square spare of the first, 135px side bars.
     Regenerate via the scratchpad `fit-ads.ps1` pattern (System.Drawing, fit + letterbox).
     Content check: the "built strong" scene is an AI restage of the real trellis-panels-trio.jpg
     project, but the "elevate" poolside backyard is fully synthetic, which cuts against the
     site's real-projects-only promise. Bryan's call; he generated them deliberately.
     These are flyer-style with heavy text. Meta dropped the 20% text rule in 2021 so they won't
     be rejected, but dense text still tends to underdeliver and the small body copy is
     unreadable at feed thumbnail size. The existing bougainvillea ad is a clean photo, so
     keeping all three in one ad set makes the campaign a real flyer-vs-clean-photo test.
   - **Both creatives are now IN the campaign (Aug 11 2026), still In draft.** Duplicated ad
     120249244621060637 twice into the same ad set (duplicating inherits page identity, CTA and
     destination, so only image + text needed changing). The ad set now holds three ads:
     - `Trellis - Built Strong Flyer 4x5` (ad 120249301860860637) — now ad4-built-strong-4x5.jpg
       (see the Aug 12 entry below; superseded ad3-built-strong-4x5.jpg). Kept the original primary
       text and "Custom Steel Trellises From $350" headline, since both already fit the
       trellis-panel creative; image swap only, so it reads as a clean image test.
     - `Trellis - Elevate Outdoor Space 1x1` (ad 120249301860870637) — ad3-elevate-1x1.jpg, new
       primary text ("Turn a blank block wall into something worth looking at...") and headline
       "Elevate Your Outdoor Space", to match that creative's message.
     - `Trellis - Bougainvillea Vertical` (original, clean library photo) — left untouched.
     Description "Free estimates in the Phoenix metro" and CTA "Get quote" on all three.
   - **Meta AI defaults turned OFF on both new ads** (they are ON by default and silently rewrite
     the creative): Add music, Add overlays (would stack more text on an already text-heavy
     flyer), Text improvements (rewrites the headline). Visual touch-ups was already off. Add
     animation left on but inert, Meta reports these images ineligible for animation. Declined the
     AI-generated image variants Meta auto-produced from the upload. Re-check these toggles on any
     future ad, they default back on.
   - Uploading needed a workaround: Ads Manager builds its `input[type=file]` on demand and clicks
     it programmatically, so no file input exists in the DOM to target and the native picker can't
     be driven. Patched `HTMLInputElement.prototype.click` to capture the input and swallow the
     click, leaving it in the DOM for the upload, then removed it and restored the prototype. This
     is why the earlier session's file_upload attempt failed. Note the picker auto-selects the new
     image ALONGSIDE the existing one ("2 selected"); deselect the old one or the ad goes carousel.
   - Left ON deliberately: Spanish translation with "Translate all ad creatives and text". Checked
     the Aug 12 before/after preview: only the caption is translated, the text baked into the
     flyer is left alone, so the earlier worry about a mangled Spanish render does not apply.
   - **Main creative as of Aug 12 2026: `ad4-built-strong-4x5.jpg`** (1080x1350; 1x1 also built).
     Same "BUILT STRONG. MADE TO LAST." flyer but using the REAL trellis-panels-trio project photo
     instead of the AI restage, so it now shows Bryan's actual work. Source was another ChatGPT
     generation (`984ebb27-…png`, 1086x1448). It is live in ad 120249301860860637, still In draft.
   - **The generated logo was misspelled** — the arc read "MOBILE WELDING & METAL FABRICAATION"
     (doubled A). ChatGPT could not fix it across four regenerations; image models are unreliable
     with text, so do not burn attempts on this. Fixed in-repo instead by compositing the real
     `images/logo.png` over the bad badge. Working script pattern is scratchpad `fix-logo5.ps1`:
     - The old artwork occupies x 43..459, y 40..287 on a flat black field, with an empty gap at
       y 288..323 before the "BUILT" headline starts at y=324.
     - Erase only the old badge's own pixels (bright AND neutral: min(R,G,B) > 22 — the background
       gradient is blue-tinted so its min channel stays low) and rebuild the background beneath by
       interpolating across each run, row by row. Do NOT flat-fill: that flattens the gradient and
       leaves a vertical seam.
     - **Stop the erase at x=460.** The photo's sunlit roof tiles and stucco wall start around
       x=461 and are bright and neutral too, so they match the same test; letting the region reach
       them blackened real photo content into a hard-cornered block (the bug that cost several
       iterations). Everything from x=461 out is left pixel-identical to the source.
     - Read one pixel PAST each side of the region as a blend target while only writing inside it,
       or a run touching the edge terminates in flat black against the sky and leaves a step.
     - Draw the real badge at the old artwork's WIDTH (417) but its own 1.584:1 ratio, so h=263;
       anchor the BOTTOM at y=288 and let it grow upward. Filling the old 417x248 box instead
       stretches it ~6% and reads as visibly squished. Growing downward would drop the banner onto
       the stucco wall (starts ~y=296), which would show through its transparent interior.
     Bryan reviews these at high zoom and catches edge artifacts, so check corners before sending.
   - Possible site work: Meta Pixel + Lead event on thanks.html for conversion tracking.

## Done

- Earthlight-lash learnings pass (Jul 2026): gallery + service-card photos converted from CSS
  backgrounds to real `<img loading="lazy">` with alt text (defers ~2 MB below the fold, adds
  image SEO); vercel.json 308 redirects added for the apex and breezywelding.vercel.app;
  JSON-LD priceRange "$350-$2400" instead of "$$"; og:locale; aria-hidden on decorative SVGs.
  Hero + CTA band stay CSS backgrounds on purpose (hero is preloaded above the fold; the CTA
  band reuses trellis-poolside.jpg which the gallery img already caches).
- FormSubmit activation confirmed by Bryan (Jul 2026): form was activated and tested working
  before the Jul 2026 formsubmit.co outage.
- Form outage fallback + quote-card scroll-margin fix (Jul 2026), shipped during a formsubmit.co
  522 outage. The AJAX success path (redirect to thanks.html) still needs one live test once
  FormSubmit is back up.
- SEO (Jul 2026, mirrored from earthlight-lash): inline SVG favicon (orange spark on steel,
  also on thanks.html), canonical URL, Open Graph/Twitter tags, LocalBusiness JSON-LD
  (areaServed cities, Mo–Sa 07:00–18:00), og.png share image (1200x630, regenerate via a
  System.Drawing script if needed), theme-color, hero image preload.
- Reduced motion (Jul 2026): smooth scroll and hover transitions/transforms disabled under
  prefers-reduced-motion — keep it that way.

## Deployment

- Live at https://www.breezywelding.com (apex breezywelding.com 308-redirects to www).
  Vercel auto-deploys pushes to `main`; project `breezywelding` in team
  papi-grande-verga-guey (CLI login bryportillo56-3043).
- **Stale duplicate (found Jul 17 2026):** https://breezywelding.vercel.app serves an OLD
  snapshot of the site (including the removed personal phone number) from a DIFFERENT Vercel
  account. Ruled out Jul 19 2026: it is not in this team, and "Continue with GitHub"
  (Breezywelding) plus the bryportillo56@gmail.com email login both map to the CURRENT
  account — so the old account is under some other email only Bryan may remember. Options:
  try old emails at vercel.com/login (email code login, no password needed), or open a
  Vercel support ticket (he owns breezywelding.com and the source repo, so they can locate
  or take down the stale project). The vercel.json redirect rule for that hostname is inert
  until then; its canonical tag pointing at www.breezywelding.com limits the SEO damage.
- Canonical/OG URLs in index.html point at https://www.breezywelding.com/ — update them if
  the domain ever changes.

## Conventions

- Keep everything in the single index.html unless the site grows past ~3 pages.
- Mobile checks: call bar shows under 900px; nav links collapse, phone number hides under 700px.
- Writing style for any copy edits: no dashes in customer-facing text, plain friendly voice.
- GitHub: https://github.com/Breezywelding/breezywelding (default branch `main`).
