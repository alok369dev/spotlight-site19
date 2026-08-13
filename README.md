# Spotlight — Website (v6: light premium + automation-ready)

Single-page site, no build step required (plain HTML/CSS/JS).

## Files you need — all 9

1. `index.html` — the whole site
2. `assets/logo-mark.png` — small nav icon *(reuse your existing file — not regenerated this round)*
3. `assets/hero-fixture.png` — hero spotlight graphic *(reuse existing)*
4. `assets/logo-full.png` — full logo, used in the footer *(reuse existing)*
5. `assets/favicon.png` — browser tab icon *(reuse existing)*
6. `robots.txt` — crawler rules, placed at the repo root
7. `sitemap.xml` — sitemap, placed at the repo root
8. `llms.txt` — machine-readable summary for LLMs/answer engines, placed at the repo root
9. `README.md` — this file (optional to upload)

**Important:** only `index.html` + the root SEO files were rebuilt this round. The four PNGs under `assets/` are unchanged — keep your existing ones in place.

## What changed in v6

**A completely new visual direction — light, pastel, premium.** Every prior version (v1–v5) used a dark theme. This one flips to a warm ivory paper background with a champagne-gold / dusty-mauve / soft-sage pastel palette — editorial and creative rather than "control-room technical," while keeping a technical edge in the interaction layer (see below).

- **Custom cursor spotlight** — a soft gold/mauve glow follows the pointer everywhere on the page (the brand's own literal spotlight), plus a small ring cursor that grows over anything interactive. Both are automatically disabled on touch devices and when reduced motion is requested.
- **Magnetic buttons** — primary/ghost buttons nudge slightly toward the cursor on desktop.
- **Flip "play cards" for Services** — each of the four service lines is a card that flips in 3D on hover (desktop) or tap/Enter (touch & keyboard) to reveal its Auto vs. Human breakdown, instead of a static list.
- **New "Systems" section** — states plainly that Spotlight is automation-ready from day one: webhook/API-first workflows, an n8n-shaped pipeline diagram, and a row of stack pills (n8n, agentic AI orchestration, webhooks/REST API, Meta Ads Manager, Zapier, CRM sync).
- **New "Dispatch" section (Blog / News / Events)** — a tabbed, filterable content grid rendered from a small JS array (`SPOTLIGHT_CONTENT`) with realistic placeholder posts. It's deliberately built so that pointing the `CONTENT_SOURCE_URL` constant at a live JSON endpoint (e.g. an n8n webhook backed by a sheet or headless CMS) is a one-line change — no other code needs to move. Matching `Blog`/`BlogPosting` and `Event` JSON-LD are in the `<head>` for two of the sample posts and the sample event.
- **Meta Ads-ready** — Open Graph/Twitter Card tags kept from v5, plus a commented, ready-to-activate Meta Pixel snippet in `<head>` (just paste a Pixel ID in two places and uncomment).
- Full SEO/AEO/GEO/LLMO stack carried forward and extended: `ProfessionalService`, `WebSite`, `FAQPage` (now 7 questions, including automation & Meta Ads questions), `robots.txt` (AI crawlers explicitly allowed), `sitemap.xml`, `llms.txt` (now documents the automation layer and Dispatch feed).
- Kept from earlier versions: scroll progress bar, active-nav highlighting, scroll-reveal animation, FAQ accordion, skip link, semantic HTML, and the validated contact form with mailto handoff.

## Deploy on Vercel via GitHub

1. Upload `index.html`, `robots.txt`, `sitemap.xml`, and `llms.txt` to the repo root, keeping your existing `assets/` folder as-is.
2. On vercel.com → your project → Framework Preset: **Other** → Deploy.
3. Every push to `main` auto-redeploys.
4. Once you have a real domain, replace every `https://www.spotlight.agency/` reference (in `index.html`'s `<head>`, `sitemap.xml`, and `llms.txt`) with your actual URL.

## Turning on automation & ads (when you're ready)

- **Blog/News/Events feed:** in `index.html`, set `CONTENT_SOURCE_URL` (search for it near the bottom `<script>`) to a JSON endpoint that returns an array shaped like the objects in `SPOTLIGHT_CONTENT`. An n8n workflow writing to a sheet/CMS and exposing it via a webhook GET is the simplest path.
- **Meta Pixel:** in `<head>`, find the commented `META PIXEL` block, paste your Pixel ID in both places it appears, and remove the `<!-- -->` wrapper.
- **Contact form:** currently opens the visitor's email client via `mailto:`. Swap in a real form backend (Formspree, an n8n webhook, a serverless function) for silent submissions that can also trigger an automated workflow.

## Editing
- Copy and section content live directly in `index.html` — search for the section id (`#about`, `#services`, `#systems`, `#how`, `#fitfor`, `#dispatch`, `#results`, `#faq`, `#contact`).
- If you edit the FAQ text, update the matching `FAQPage` JSON-LD block in `<head>` too.
- Colors and fonts are CSS variables at the top of the `<style>` block (`:root`) — `--gold` is the marketing accent, `--mauve` is the intelligence accent, `--sage` is the systems/automation accent.
- Footer social links (`Instagram`, `LinkedIn`) are placeholders (`href="#"`) — add real URLs when ready, and update the matching `sameAs` array in the Organization JSON-LD.
