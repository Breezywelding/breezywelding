# Breezy Welding, Website

Single-page static site (`index.html`). No build step, open it or deploy the folder to Vercel/Netlify as-is.

## Photos

Real project photos live in `images/` (pulled from Bryan's iCloud share, July 2026):

| Filename | Where it shows |
|---|---|
| `gate-single-1.jpg` | **Hero background**, Single Gates card, gallery tile 1 |
| `trellis-1.jpg` | Trellis card (pool + blue-pot trellis wall) |
| `trellis-pots.jpg` … `shop-fabrication.jpg` | Gallery tiles 2 to 9 |
| `trellis-poolside.jpg` | Also the CTA band background |
| `gate-rv-1.jpg` | RV Gates card + gallery tile 6 (dark composite dual-swing) |
| `gate-rv-2.jpg` | Gallery tile 7 (cedar & steel dual gate) |

Missing images fall back to a dark steel color, so the site still looks fine before photos are added.

## Before launch, replace placeholders

- ~~Phone number~~ REMOVED (Jul 2026): the number used at launch was Bryan's personal cell, so the site is email + quote form only until he sets up a business number.
- ~~Email~~ DONE: breezywelding@gmail.com (form action + footer).
- ~~Quote form~~ DONE: posts to [FormSubmit](https://formsubmit.co) → breezywelding@gmail.com (no account needed). Includes honeypot spam field, table-formatted email, and redirect to `thanks.html`. **One-time activation**: the FIRST form submission triggers a confirmation email to breezywelding@gmail.com, Bryan must click the activation link in it, then all future submissions arrive normally. Do this test submission once the site is deployed (activation is tied to the email, not the domain, so a localhost test works too).
- **Service area / cities**: adjust in FAQ + footer if needed.
- **Reviews**: the three testimonials are placeholders, swap in real customer quotes as they come in.
- **ROC license #**: if he gets licensed with the AZ Registrar of Contractors, add the number to the footer (big trust signal in AZ).
