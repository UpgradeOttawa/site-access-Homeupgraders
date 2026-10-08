# Independent review request: homeupgraders.ca website (static files)

Scope: the files in this repo only (the website). Do not review or comment on the separate apps at apps.homeupgraders.ca.
Nothing here is deployed. Please report problems; do not assume anything is fine because the author says so.

## What to verify (please check each one yourself, from the files)
1. All 13 routes exist with trailing slashes: /, /about-us/, /services/, 8 service pages, /contact-us/, /gallery/ (+ 404.html).
2. Each page has exactly one H1, a unique title and meta description, a canonical on https://homeupgraders.ca/ (no www), and Open Graph / Twitter tags.
3. Header on every page: phone link tel:+16133147926 and "Get a Free Quote" pointing to /contact-us/. Nav order: Home, About Us, Services (8 sub-items), Orleans Contractor, Gallery, Tools, Contact Us.
4. The Tools menu links go to specific pages on apps.homeupgraders.ca (not only the hub). Confirm every link is well-formed.
5. Structured data (JSON-LD) parses on every page. Homepage schema should match the Google Business Profile: 91 Branthaven St, Orléans, ON K4A 0G5; phone 613-314-7926; hours Mon-Fri 06:00-21:00, Sat 10:00-21:00, Sun closed; ten service areas. Flag any invented claim.
6. Wording rules: business is "third-generation" (son is the fourth generation). None of these strings may appear: Premier, 20,000, endless, 5 star, Builder OS, fourth-generation as a business description.
7. gallery/photos.json: 254 entries, every entry has alt text, and no precise coordinates (pins are one point per postal-prefix area).
8. Images: every <img> for the service/card/About photos has width and height; no base64 images remain.
9. .htaccess: www -> non-www redirect, the two legacy redirects, and ErrorDocument 404. Check the rules for loops or mistakes.
10. Accessibility and mobile: menu open/close script on the inner pages, aria-expanded states, no horizontal scroll at 390 px.

## Known, intentional differences (not bugs)
- Homepage uses the new design (inline CSS, native <details> menus); inner pages still use css/style.css. The homepage H2 headings differ from the original WordPress text on purpose.
- 404.html is noindex and has no canonical on purpose.
- Contact form posts JSON to a Supabase edge function. Do not submit it.

## Author's own check results (2026-10-08, branch site/header-tools-2026-10-08)
Static checks: 20 of 23 pass; the 3 non-passes were test-script limits or the intentional homepage heading change (see above).
Browser checks (Chromium, 390 and 1363 px): no horizontal scroll on any of 13 pages, no JS errors, phone menu opens/closes on all 13, contact form blocks empty submit and the honeypot stays empty, gallery renders 254 images with alt text.
