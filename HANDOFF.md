# LaunchLayouts — Developer Handoff

## What this is

LaunchLayouts is a small web-design business. Customers browse a gallery of one-page website templates, pick one, and I build and deliver a finished site for them. Today the repo is a **static GitHub Pages site** (plain HTML/CSS, no build step, no backend).

## The problem we're solving

The site looks finished but **cannot make money**. There is no way for a visitor to pay, and no structured way for them to hand over the content I need to build their site. Every lead has to be handled manually over email. The goal of the next phase is to turn the gallery into a **self-serve sales funnel** and to cut my per-site build time so each order is profitable.

## What exists today

```
index.html              Landing page: template gallery, process, pricing, contact
assets/site.css         Landing page styles
templates/
  spotlight/            Template 01 — personal brand / performer
  encore/               Template 02 — singer / band
  clarity/              Template 03 — coach / consultant
    index.html
    style.css
```

- Pricing shown on the landing page: **$299** (starter), **$599** (featured/pro), and a "Let's talk" custom tier. Adjust these if the numbers change.
- Templates use `.ph` placeholder blocks where real images go.
- Adding a template = copy a folder, edit HTML/CSS, add a `<article class="template-card">` to `index.html`.
- Deploy = push to `main`, GitHub Pages serves from root. See `README.md`.

## What to build (in priority order)

### 1. Checkout — take payment on each template
- Add a Stripe Payment Link (or Stripe Checkout) per template / per pricing tier.
- Each template card gets a clear "Choose this template" CTA that goes to checkout.
- Collect at least a deposit at checkout; full payment is fine too.
- Success URL should redirect to the intake form (#2) with the template + tier in the query string.
- **This is the single most important item.** Nothing else matters until money can arrive.

### 2. Post-payment intake form
- After paying, the customer fills in everything I need to build the site:
  business/stage name, tagline, about text, services/offerings, photos (upload), brand colors, social links, contact email/phone, domain preference.
- Use a hosted form service (Tally, Formspree, Netlify Forms, or Typeform) — no custom backend needed yet.
- Responses should land in one place (email + spreadsheet/Airtable) and reference the Stripe payment.

### 3. Template filler script
- A small script (Node or Python) that reads one intake response and produces a filled copy of the chosen template: swaps text, drops in images, sets CSS colour variables.
- Goal: a site goes from "order received" to "first draft" in under an hour instead of a full day.
- Keep templates driven by simple, greppable placeholders (e.g. `{{BUSINESS_NAME}}`) or CSS variables so the script stays trivial.

### 4. Per-client deploy + recurring hosting
- One command / one click to publish a finished client site (GitHub Pages repo per client, or Netlify/Vercel).
- Add a monthly "hosting & updates" plan ($20–50/mo, Stripe subscription). Recurring revenue is the real prize here.

### 5. Niche landing pages for SEO
- One page per audience we already serve: "website for singers", "website for coaches", "website for performers".
- Each page shows the matching template and links straight to checkout.

### 6. More templates
- Only after 1–5 are live. Each new template should follow the placeholder convention from #3.

## What NOT to build

- A custom CMS or admin dashboard
- An AI "generate my site" builder
- A multi-tenant SaaS platform
- A framework migration (React/Next/etc.) — plain HTML/CSS is fine and fast for this

These compete with Squarespace/Wix and would take months before the first dollar. Keep it boring and shippable.

## Constraints and preferences

- Keep the site static and hosted on GitHub Pages as long as possible. Third-party hosted services (Stripe, form providers) are preferred over running our own backend.
- No secrets in the repo. Stripe publishable keys are fine in HTML; secret keys never are.
- `reference/` (if present) contains screenshots of someone else's site used for inspiration — don't publish it.
- Mobile-first; most customers will find us on their phones.

## Definition of done for phase 1

A stranger can land on the homepage, pick a template, pay, fill in the intake form, and I receive a complete brief plus payment notification — with zero manual steps from me.

## Questions? Contact

Reach out to the repo owner (viraone) for pricing decisions, Stripe account access, and brand assets.
