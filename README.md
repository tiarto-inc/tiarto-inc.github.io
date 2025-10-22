# tiarto landing (GitHub Pages)
This is a simple, fast, static landing page for **tiarto.com** with a black + magenta, high-end hardware vibe.

## Deploy
1) Create a GitHub repo named `tiarto.github.io`
2) Upload the contents of this folder to the root of that repo
3) In GitHub → **Settings → Pages → Deploy from branch (main/root)**

## Custom domain (Namecheap)
Add these DNS records in Namecheap → **Advanced DNS**:
- A @ 185.199.108.153
- A @ 185.199.109.153
- A @ 185.199.110.153
- A @ 185.199.111.153
- CNAME www tiarto.github.io

Then set **Custom Domain** in GitHub Pages to `tiarto.com` and enforce HTTPS.

## Customize
- Replace `assets/logo.svg` with your official logo (transparent background)
- Update text in `index.html` to reflect latest products/sections
- Edit colors in `styles.css` (`--accent` for magenta, etc.)
