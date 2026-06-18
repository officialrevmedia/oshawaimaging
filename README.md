# Oshawa Advance Imaging - Website

Production-ready website for **Oshawa Advance Imaging**, a diagnostic ultrasound and X-ray clinic located at 115 Simcoe St S, Oshawa, ON.

Built as a fast, accessible, SEO-optimized static site. No build step and no dependencies - just HTML, CSS, and a small amount of vanilla JavaScript. Deploy it anywhere that serves static files (GitHub Pages, Netlify, Vercel, Cloudflare Pages, or standard web hosting).

---

## Quick start

This is a static site. To preview locally, run a simple web server from this folder:

```bash
# Python 3
python3 -m http.server 8000
# then open http://localhost:8000
```

To deploy, upload the entire contents of this folder to your host's web root.

---

## Deploying with GitHub Pages

1. Create a new repository and push these files to it.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose your branch (e.g. `main`) and the `/ (root)` folder, then save.
4. Your site will be published at the URL shown on that page.

If you use a custom domain (`www.oshawaadvanceimaging.ca`), add it under **Settings → Pages → Custom domain**, then create a `CNAME` file (GitHub can do this for you) and point your DNS at GitHub Pages.

> The site's canonical URLs, sitemap, and structured data all use `https://www.oshawaadvanceimaging.ca/`. If the production domain ever changes, update those references (see **Configuration** below).

---

## Project structure

```
.
├── index.html                          Home page
├── about.html                          About the clinic
├── services.html                       Services overview
├── ultrasound.html                     Ultrasound hub (service detail)
├── x-ray.html                          X-ray (service detail)
├── obstetrical-ultrasound.html         Obstetrical ultrasound (service detail)
├── musculoskeletal-ultrasound.html     MSK & soft tissue (service detail)
├── abdominal-pelvic-ultrasound.html    Abdominal, pelvic, kidney & bladder (service detail)
├── patient-forms.html                  Downloadable forms & requisitions
├── patient-preparation.html            How to prepare, by exam
├── referring-physicians.html           Information for referring physicians
├── faq.html                            Frequently asked questions
├── contact.html                        Contact + booking form + map
├── privacy.html                        Privacy policy
├── accessibility.html                  Accessibility statement
├── 404.html                            Not-found page
├── sitemap.xml                         XML sitemap (all pages)
├── robots.txt                          Crawler directives + sitemap link
├── site.webmanifest                    PWA / installable web app manifest
├── forms/                              The 5 clinic PDF forms (linked from the site)
│   ├── Ultrasound_Requisition_Form.pdf
│   ├── Consent_Transvaginal_Transrectal_Ultrasound.pdf
│   ├── Kidney_Bladder_Ultrasound_Worksheet.pdf
│   ├── Soft_Tissue_Ultrasound_Worksheet.pdf
│   └── Wrist_Ultrasound_Worksheet.pdf
└── assets/
    ├── css/styles.css                  Full design system (single stylesheet)
    ├── js/main.js                      Nav, scroll reveal, counters, form handling
    ├── img/
    │   ├── (19 photographs)            Real clinic and imaging photography (hero, reception, ultrasound, X-ray, etc.)
    │   ├── hero-scan.svg               Animated scan motif (retained for accents)
    │   └── og-image.jpg                Social share image (Open Graph / Twitter)
    ├── logo.png                        Primary logo (transparent)
    ├── logo-white-bg.png               Logo on white background
    ├── favicon-32.png / favicon-16.png Favicons
    ├── apple-touch-icon.png            iOS home-screen icon
    └── icon-192.png / icon-512.png     PWA / manifest icons
```

---

## Clinic information (single source of truth)

This information is used across the site. If any of it changes, update it everywhere it appears (a project-wide find-and-replace is the quickest way).

- **Name:** Oshawa Advance Imaging
- **Address:** 115 Simcoe St S, Oshawa, ON L1H 4G7
- **Phone:** +1 (905) 215-1815  ·  link form `tel:+19052151815`
- **Fax:** +1 (905) 215-2145
- **Email:** info@oshawaadvanceimaging.ca
- **Hours:** Mon to Fri 9:00 AM to 6:00 PM, Sat 10:00 AM to 4:00 PM · Sun Closed
- **Areas served:** Oshawa, Whitby, Courtice, Bowmanville, Ajax, Pickering, Clarington, Durham Region

---

## What's included for SEO

- Unique `<title>` and meta description on every page.
- Canonical URLs on every page.
- Open Graph + Twitter Card tags with a branded share image.
- Structured data (JSON-LD): `MedicalClinic` / `LocalBusiness` with address, geo, hours and services on the home page; `FAQPage` on the home, FAQ and service pages; `BreadcrumbList` on inner pages.
- `sitemap.xml` and `robots.txt`.
- Semantic HTML, descriptive alt text, and mobile-first responsive layout.
- Real, web-optimized photography (compressed baseline JPEGs) plus lightweight SVG accents for fast loading and strong Core Web Vitals.

---

## Customisation notes

**Photography.** The site ships with real clinic and imaging photography throughout (hero, reception, ultrasound, X-ray, musculoskeletal and more), all in `assets/img/` as web-optimized baseline JPEGs. To swap any image, replace the file in `assets/img/` (keep the same filename) or update the `src` on the relevant `<img>`.

**The contact form.** `contact.html` and the home page include an appointment-request form. On submit, it opens the visitor's email app with a message to info@oshawaadvanceimaging.ca, pre-filled with their name, phone, email, requested service, preferred date, and message, ready to send. This requires no backend and works on any static host. If you later prefer the form to submit silently to a backend (for example Formspree, Netlify Forms, or your own endpoint), update the `#contactForm` handler in `assets/js/main.js`.

**The map.** The contact page and home page embed a Google Maps view of the address. No API key is required for the basic embed used here.

**Updating the year.** The footer year updates automatically via JavaScript.

---

## Browser support

Works in all modern browsers (Chrome, Edge, Firefox, Safari) on desktop and mobile. The layout uses CSS grid/flexbox and progressive enhancements; if JavaScript is disabled, all content remains readable and all links work.

---

© Oshawa Advance Imaging. All rights reserved.
