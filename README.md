# TL;DW Studios — Website

Static marketing site for [tldwstudios.com](https://tldwstudios.com), built for GitHub + Vercel deployment.

---

## File Structure

```
/
├── index.html          ← Main site (single page)
├── favicon.svg         ← Browser tab icon
├── robots.txt          ← SEO crawler instructions
├── sitemap.xml         ← SEO sitemap (update lastmod date when you make changes)
├── vercel.json         ← Vercel deployment config (caching, security headers)
├── assets/
│   ├── logo.png        ← Your TL;DW Studios logo (replace placeholder)
│   └── og-image.jpg    ← Social share image for LinkedIn/Twitter (1200×630px)
└── README.md           ← This file
```

---

## Deploying to Vercel (first time)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **Add New Project**
3. Import your GitHub repo
4. Framework Preset: **Other** (it's a static site)
5. Build Command: *(leave blank)*
6. Output Directory: *(leave blank or set to `.`)*
7. Click **Deploy** — done. Vercel gives you a live URL instantly.

To connect your custom domain (`tldwstudios.com`):
- In Vercel: Project Settings → Domains → Add `tldwstudios.com` and `www.tldwstudios.com`
- In your DNS provider: add the A/CNAME records Vercel shows you

---

## Making Updates

Every time you push a commit to the `main` branch, Vercel automatically redeploys. No manual steps needed.

---

## TODO: Things to swap in

### 1. Logo
Replace the logo `<img>` src in the nav and footer with your actual logo file:
```html
<!-- In index.html, find this and update the src: -->
<img src="/assets/logo.png" alt="TL;DW Studios" />
```
Drop your logo file into `/assets/logo.png` (or `.svg` — SVG preferred for sharpness).

### 2. Tally Contact Form
Find this comment in `index.html`:
```html
<!-- TALLY FORM INTEGRATION:
     Replace this block with your Tally embed code. -->
```
Replace the entire `<form class="contact-form">...</form>` block with your Tally embed iframe. Example:
```html
<iframe
  data-tally-src="https://tally.so/embed/YOUR_FORM_ID?alignLeft=1&hideTitle=1&transparentBackground=1&dynamicHeight=1"
  loading="lazy"
  width="100%"
  height="500"
  frameborder="0"
  marginheight="0"
  marginwidth="0"
  title="Contact TL;DW Studios">
</iframe>
<script>var d=document,w="https://tally.so/widgets/embed.js",v=function(){"undefined"!=typeof Tally?Tally.loadEmbeds():d.querySelectorAll("iframe[data-tally-src]:not([src])").forEach((function(e){e.src=e.dataset.tallySrc}))};if("undefined"!=typeof Tally)v();else if(d.querySelector('script[src="'+w+'"]')==null){var s=d.createElement("script");s.src=w,s.onload=v,s.onerror=v,d.body.appendChild(s);}</script>
```

### 3. OG Social Image
Create a `1200 × 630px` image (JPG) for LinkedIn sharing and save it as `/assets/og-image.jpg`.
Suggested design: dark background, gold TL;DW logo, headline "You said it once. We make it work 10×."

### 4. Email address
Search `index.html` for `hello@tldwstudios.com` and replace with your actual contact email.

### 5. Sitemap date
After any significant update, edit `sitemap.xml` and update the `<lastmod>` date to today.

---

## Tech Stack

- Pure HTML / CSS / vanilla JS — no build tools, no frameworks, no dependencies
- Google Fonts (loaded via CDN)
- Tally.so for forms (when added)
- Vercel for hosting (static, free tier)

---

## Performance Notes

- All CSS is inlined in `index.html` — zero extra network requests for styles
- Fonts are preconnected for faster load
- Images in `/assets/` are cached for 1 year via `vercel.json`
- No JavaScript frameworks — page loads fast on mobile

---

*Built for TL;DW Studios · 2025*
