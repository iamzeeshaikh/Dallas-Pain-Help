# DallasPainHelp.com — Astro Lead Generation Website

A fully SEO-optimized, statically generated lead generation website for a Dallas, TX pain management clinic.
Built with Astro 6, Tailwind CSS 4, and TypeScript.

## Quick Start

```bash
npm install
npm run dev        # Local dev server at localhost:4321
npm run build      # Production build to ./dist/
npm run preview    # Preview the production build locally
```

## Project Structure

```
src/
  components/
    SEO.astro           # Injects all head meta, OG, schema, font preload
    Header.astro        # Sticky header with click-to-call + mobile menu
    Footer.astro        # Footer mega-nav with NAP for local SEO
    AppointmentForm.astro  # Accessible lead capture form
    Breadcrumbs.astro   # Visual breadcrumbs + BreadcrumbList schema
    CTASection.astro    # Reusable CTA band component
  layouts/
    BaseLayout.astro    # Base HTML layout wrapping all pages
  pages/
    index.astro         # Homepage
    about.astro         # About page
    contact.astro       # Contact + form
    request-appointment.astro  # Dedicated conversion page
    thank-you.astro     # Post-form submission confirmation
    404.astro           # Custom 404
    conditions/
      index.astro               # All conditions index
      [slug].astro              # Dynamic condition pages (14 conditions)
    treatments/
      index.astro               # All treatments index
      [slug].astro              # Dynamic treatment pages (8 treatments)
    locations/
      index.astro               # All locations index
      [slug].astro              # Dynamic location pages (13 locations)
  data/
    conditions.ts       # All condition content + SEO + schema data
    treatments.ts       # All treatment content + SEO + schema data
    locations.ts        # All location content + SEO + schema data
  styles/
    global.css          # Tailwind 4 + custom brand variables + utility classes
public/
  fonts/
    inter-var.woff2     # Self-hosted Inter variable font
  images/               # Add real photos here
  favicon.svg           # Brand favicon
  robots.txt            # Allows crawling, references sitemap
  _headers              # Netlify caching + security headers
```

## Before Going Live — Complete TODO List

Search the codebase for `// TODO` to find every item. Key items:

### Business Information
- [ ] Replace phone number `(214) 555-0100` with real clinic phone
- [ ] Replace address `1234 Medical Drive, Suite 100, Dallas, TX 75201` with real address
- [ ] Update `lat/lng` coordinates in structured data (homepage + contact)
- [ ] Replace email `info@dallaspainhelp.com` with real email
- [ ] Update clinic hours in `contact.astro` and `Footer.astro`
- [ ] Update `priceRange` in LocalBusiness schema on homepage

### Content & Credentials
- [ ] Add real physician bios, credentials, and board certifications in `about.astro`
- [ ] Add real board certification badge images and hospital affiliation logos
- [ ] Verify all insurance participation claims before launch
- [ ] Replace placeholder patient testimonials with real, HIPAA-compliant reviews (written consent required)
- [ ] Add `AggregateRating` schema to homepage once you have real, verifiable review data
- [ ] Verify "15+ years experience" and "5,000+ patients" stats or remove them
- [ ] Update `sameAs` in Organization schema with real social media URLs

### Images
All image placeholders are clearly marked. Replace each with a licensed or owned photo:
- Hero image: doctor-patient consultation
- About page: physician team photo
- Condition pages: relevant condition/anatomy illustrations
- Treatment pages: procedure photos
- Location pages: local area landmarks
- OG default image: `public/images/og-default.jpg` (1200×630px JPEG)
- Favicon 32px PNG: `public/favicon-32.png`
- Apple touch icon: `public/apple-touch-icon.png`

### Analytics & Search Console
- [ ] Add Google Tag Manager ID in `SEO.astro` (search for `GTM-XXXXXXX`)
- [ ] Uncomment and enable GTM `<noscript>` fallback in `BaseLayout.astro`
- [ ] Add Google Search Console verification meta tag in `SEO.astro`
- [ ] Set up GA4 conversion events for form submissions and click-to-call

### Form / CRM
- [ ] Connect `AppointmentForm.astro` to your CRM, email provider, or Netlify Forms
  - For Netlify Forms: Add `netlify` and `data-netlify="true"` attributes to the `<form>` tag
  - For Formspree/Resend/HubSpot: Update the `action` attribute and add any hidden fields
- [ ] Test the form end-to-end before launch
- [ ] Add form submission conversion tracking (GA4 event or GTM trigger)

### Legal & Compliance
- [ ] Create and link a real Privacy Policy page
- [ ] Create and link a Terms of Service page
- [ ] Verify the medical disclaimer in the Footer is accurate
- [ ] Ensure all testimonials and reviews comply with FTC guidelines
- [ ] Review HIPAA compliance for your form → CRM pipeline

### Deployment (Netlify recommended)
1. Push to GitHub/GitLab
2. Connect to Netlify — it auto-detects Astro, runs `npm run build`, deploys `dist/`
3. Add domain `dallaspainhelp.com` in Netlify Site Settings → Domain Management
4. Enable Netlify's automatic HTTPS (Let's Encrypt)
5. The `public/_headers` file is automatically applied by Netlify

### Pre-Launch SEO Checklist
- [ ] Submit `sitemap-index.xml` to Google Search Console
- [ ] Submit `sitemap-index.xml` to Bing Webmaster Tools
- [ ] Create and verify Google Business Profile for the clinic address
- [ ] Ensure NAP (Name/Address/Phone) is identical on website, GBP, and all citations
- [ ] Set up local citations: Yelp, Healthgrades, Zocdoc, Vitals, US News Health
- [ ] Install and verify Google Search Console
- [ ] Run Lighthouse audit and address any score below 90
- [ ] Test all 44 pages on mobile (BrowserStack or real device)
- [ ] Confirm all 44 canonical URLs are correct in the sitemap

## Adding Content

### Add a new condition
1. Add a new entry to `src/data/conditions.ts` following the `Condition` interface
2. The page at `/conditions/[slug]/` is generated automatically by `[slug].astro`
3. Add the slug to related treatments' `conditions` arrays for cross-linking
4. The sitemap and footer update automatically

### Add a new treatment
1. Add a new entry to `src/data/treatments.ts` following the `Treatment` interface
2. The page at `/treatments/[slug]/` is generated automatically
3. Cross-link from relevant condition pages

### Add a new location
1. Add a new entry to `src/data/locations.ts` following the `Location` interface
2. The page at `/locations/[slug]/` is generated automatically
3. Add the slug to related locations' `relatedLocations` arrays

## Technology

- **Astro 6** — static output, zero client JS by default
- **Tailwind CSS 4** — via `@astrojs/tailwind` vite plugin
- **TypeScript** — strict mode, all data files typed
- **@astrojs/sitemap** — auto-generates `sitemap-index.xml` + `sitemap-0.xml`
- **Self-hosted Inter font** — no Google Fonts CDN, preloaded for LCP
- **JSON-LD structured data** — LocalBusiness, MedicalCondition, MedicalProcedure, FAQPage, BreadcrumbList, WebSite, Organization
