# AdsKompass Landing Page

Static marketing site for adskompass.com. No build step — these are plain HTML files with Tailwind CSS loaded via CDN.

## Files

- `index.html` — the landing page
- `terms.html` / `privacy.html` — full Terms of Service and Privacy Policy content
- `favicon.svg` — browser tab icon

## Local preview

No server needed. Just open `index.html` directly in a browser (double-click it, or drag it into a browser window).

## Before going live

Done:
- ✅ Terms of Service / Privacy Policy — full content in `terms.html`/`privacy.html`, converted from `Legal/AdsKompass_Terms_of_Service.md` and `Legal/AdsKompass_Privacy_Policy.md`
- ✅ Contact form — wired to Formspree (`https://formspree.io/f/mlgyqqjw`)
- ✅ Telegram handle — `@Thomas_mktai_bot`

Still to do:
1. **Add Google Analytics (optional).** In `index.html`, find the commented-out `<!-- Google Analytics ... -->` block near the top of `<head>`. Once you have a GA4 property, replace both occurrences of `G-XXXXXXXXXX` with your real measurement ID and remove the `<!--` and `-->` comment markers around the block.

2. **Add a social share image (optional).** `index.html`'s `og:image` tag points to `/og-image.png`, which doesn't exist yet. Add a 1200×630px image at that path if you want a nice preview image when the link is shared on social media/WhatsApp/etc. — without it, shared links just won't show a preview image, everything else still works.

3. **If your legal content changes**, the Markdown sources live at `Legal/AdsKompass_Terms_of_Service.md` and `Legal/AdsKompass_Privacy_Policy.md` in the bot project folder — update those first, then re-convert to `terms.html`/`privacy.html` (ask Claude Code to redo the conversion, or edit the HTML directly for small changes).

## Deploying to Vercel

**Option A — Vercel dashboard (easiest):**
1. Go to https://vercel.com and sign in (or create a free account)
2. Click "Add New" → "Project"
3. Either connect this GitHub repo, or drag-and-drop this folder directly onto the upload area
4. Leave all build settings as default — there's no build step, Vercel will serve the HTML files as-is
5. Click "Deploy"

**Option B — Vercel CLI:**
```bash
npm install -g vercel
vercel
```
Follow the prompts. No configuration file is needed.

## Custom domain (adskompass.com)

1. In the Vercel dashboard, open your project → Settings → Domains
2. Add `adskompass.com`
3. Vercel will show you DNS records to add at your domain registrar (usually an `A` record or `CNAME`, Vercel's UI tells you exactly which)
4. Add those records at wherever adskompass.com is registered — propagation usually takes a few minutes to a few hours

## Environment variables

None needed. Formspree and Google Analytics are both configured directly in the HTML (see "Before going live" above), not via environment variables — there's no server-side code in this project to read them.
