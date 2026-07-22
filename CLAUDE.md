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
   - Pending from Bryan: add a payment method (Billing), then publish the $10/day draft.
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
