# Nordlytics — Company Website

Static company website for **Nordlytics AB** (org.nr 559323-4874), deployed
via **Cloudflare Pages** from this GitHub repository.

Plain HTML + CSS with **zero build step** — the `public/` folder is the
complete, deployable site.

## Pages

| Path        | Purpose                                                              |
| ----------- | -------------------------------------------------------------------- |
| `/`         | Start page — headline, services overview, product, about teaser, CTA |
| `/services/`| Services and engagement model                                        |
| `/products/`| Products and case studies (Shot Log et al.)                          |
| `/company/` | About the company + official registration details                    |
| `/contact/` | Contact information                                                  |
| `/privacy/` | Privacy policy (GDPR)                                                |
| `/terms/`   | Terms of service                                                     |
| `/404.html` | Not-found page (Cloudflare Pages serves this automatically)          |

Also included: `robots.txt`, `sitemap.xml`, security headers in `_headers`,
Open Graph meta tags and Organization JSON-LD structured data.

## Deploying to Cloudflare Pages

1. Push this repository to GitHub.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Connect to Git** and select the repo.
3. Build settings:
   - **Framework preset:** `None`
   - **Build command:** *(leave empty)*
   - **Build output directory:** `public`
4. Add the custom domain `nordlytics.se` (and `www`) under **Custom domains**, and make sure the canonical URLs in the HTML (`https://nordlytics.se/...`) match the final domain.

Every push to the production branch deploys automatically.

## Local preview

```sh
cd public
python3 -m http.server 8000
# open http://localhost:8000
```

## Before going live — checklist

- [ ] **Email address:** the site uses `contact@nordlytics.se` throughout. Create the mailbox or search-and-replace it with the real address (`grep -r "contact@nordlytics.se" public/`).
- [ ] **Domain:** verify all canonical/OG URLs match the final domain (currently `https://nordlytics.se`).
- [ ] **Apple Developer review:** the site includes a start page describing the business, services, a product with a working web-app link, contact details, company registration info, a privacy policy and terms — the pages Apple typically checks. Update the "Last updated" dates on the legal pages whenever they change.
- [ ] Optionally add real analytics (requires updating the privacy policy) and a screenshot of the Shot Log app on the products page.

## Why a company review passes

The site states clearly who the company is (legal name, org. number,
registration date, address, board member on `/company/`), what it does
(`/services/`, `/products/`), how to reach it (`/contact/`), and includes the
legal documents Apple's review looks for (`/privacy/`, `/terms/`).