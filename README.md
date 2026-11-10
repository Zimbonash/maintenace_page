# RentSmart — Temporary "Coming Soon" Page

Static maintenance page for **rentsmart.africa**, hosted on GitHub Pages while the main platform is being upgraded.

## Files

| File | Purpose |
|---|---|
| `index.html` | The page (single file, no build step) |
| `logo.png` | RentSmart logo used in the header |
| `404.html` | Same page, so any deep link (e.g. `/property/123`) also shows the notice |
| `CNAME` | Tells GitHub Pages to serve this repo on `rentsmart.africa` |
| `.nojekyll` | Skips Jekyll processing |

## 1. Push to GitHub

```bash
cd rentsmart-maintenance
git init
git add .
git commit -m "Temporary coming soon page"
git branch -M main
git remote add origin https://github.com/<your-username>/rentsmart-maintenance.git
git push -u origin main
```

## 2. Enable GitHub Pages

Repo → **Settings → Pages**
- **Source:** Deploy from a branch → `main` / `/ (root)` → Save
- **Custom domain:** `rentsmart.africa` (already filled from `CNAME`)
- Once the DNS check passes, tick **Enforce HTTPS**

Tip: verify the domain first under **GitHub → Settings (account) → Pages → Add a domain** to stop anyone else claiming it.

## 3. Point DNS (Cloudflare)

Back up your current `@` and `www` records first so you can switch back.

Replace the apex (`@`) records with these four **A** records:

| Type | Name | Content |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

Optional IPv6 (**AAAA**, name `@`): `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`

And for www:

| Type | Name | Content |
|---|---|---|
| CNAME | www | `<your-username>.github.io` |

**Cloudflare notes**
- Set these records to **DNS only (grey cloud)** until GitHub issues its HTTPS certificate (usually 10–60 min). After that you can switch them back to Proxied, with SSL/TLS mode set to **Full**.
- **Don't touch** other subdomains like `images.rentsmart.africa`, API subdomains or MX/email records — only `@` and `www` change.

## 4. Switching back

When the new version is live, restore your saved `@`/`www` records and either remove the custom domain in the repo's Pages settings or delete the repo.

## Editing

- Contact links: WhatsApp (`wa.me/263712917071`) and `info@rentsmart.africa` in `index.html` — change if needed.
- After editing `index.html`, copy it to `404.html` too: `cp index.html 404.html`.
"# maintenace_page" 
