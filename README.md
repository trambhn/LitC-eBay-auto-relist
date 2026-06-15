# LitCommerce — eBay Auto Relist Template (Mockup)

Interactive UI prototype for the **eBay Auto Relist Template** in LitCommerce's Marketplace Integration. Built in the LitCommerce template-editor pattern: master enable/disable toggle, listing-status condition, All Product Quantity condition (with an "Any" minimum-quantity floor), and a max-relist cap.

Static **HTML + CSS + vanilla JS** — no React, no build step, no runtime dependencies. Renders anywhere and deploys to Vercel as-is. The mockup is the site root (`index.html`).

## Run locally

```bash
npx serve .
# open the printed http://localhost:3000
```

Or just open `index.html` in a browser.

## Push to GitHub

```bash
git init
git add .
git commit -m "LitCommerce eBay auto-relist template mockup"
git branch -M main
git remote add origin https://github.com/<your-org>/auto-relist-template.git
git push -u origin main
```

## Deploy to Vercel

1. Go to https://vercel.com/new and import the GitHub repo.
2. Framework preset: **Other** (auto-detected). No build command; output directory is the repo root.
3. Deploy. The mockup is served at the root URL.

`vercel.json` pins the static behavior explicitly.

## Open decisions (left as backend hooks, not UI)

- **Linked listings only** — auto relist runs on listings linked to a product; unlinked eBay listings are out of scope for v1.
- **90-day limit** — listings ended more than 90 days ago can't be relisted by eBay and should be skipped with a notice.
- **Sync reconciliation** — the "Any" minimum-quantity floor captures the seller's intent to keep a listing alive at 0 stock; the backend must honor that against the inventory-sync cycle so the listing isn't driven back to 0 and ended.
