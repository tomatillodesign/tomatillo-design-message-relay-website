# GitHub Pages Deployment Instructions

This guide walks through launching this static site on GitHub Pages.

## Prerequisites

- You have access to: `https://github.com/tomatillodesign/tomatillo-design-message-relay-website`
- This local folder contains at least:
  - `index.html`
  - `styles.css`
  - `README.md`

## 1) Connect local folder to the GitHub repo

From the project root:

```bash
git init
git add index.html styles.css README.md GH_PAGES_DEPLOYMENT.md content.md
git commit -m "Initial landing page build"
git branch -M main
git remote add origin https://github.com/tomatillodesign/tomatillo-design-message-relay-website.git
git push -u origin main
```

If the remote already has content, pull/reconcile first before pushing.

## 2) Enable GitHub Pages

1. Open the repository on GitHub.
2. Go to **Settings** -> **Pages**.
3. Under **Build and deployment**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main`
   - **Folder**: `/ (root)`
4. Click **Save**.

GitHub will publish and provide a URL like:

`https://tomatillodesign.github.io/tomatillo-design-message-relay-website/`

## 3) Verify the site

After deployment completes:

- Confirm homepage loads with expected typography and styles.
- Confirm links work:
  - `https://tomatillodesign.com`
  - `mailto:info@tomatillodesign.com`
- Test mobile + desktop layout.
- Confirm no missing CSS (unstyled page usually means wrong path or file missing from root).

## 4) Connect custom domain (`message-relay.org`)

Use these exact settings to point your domain at GitHub Pages.

### GitHub Pages settings

1. In your repo, open **Settings** -> **Pages**.
2. In **Custom domain**, enter:
   - `message-relay.org`
3. Click **Save**.
4. Wait for GitHub to create/confirm the `CNAME` file in the published site.
5. Enable **Enforce HTTPS** when it becomes available.

### DNS records to add

At your DNS provider, configure:

- Apex/root domain (`message-relay.org`) as `A` records:
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`
- Optional IPv6 `AAAA` records (recommended):
  - `2606:50c0:8000::153`
  - `2606:50c0:8001::153`
  - `2606:50c0:8002::153`
  - `2606:50c0:8003::153`
- `www` host as `CNAME`:
  - `www` -> `tomatillodesign.github.io`

### Redirect behavior recommendation

- Keep `message-relay.org` as the primary domain in GitHub Pages.
- Keep `www.message-relay.org` DNS configured so GitHub can automatically redirect it to the primary domain.

### Validation checklist

- `dig message-relay.org +short` returns GitHub Pages IPs.
- `dig www.message-relay.org +short` resolves via `tomatillodesign.github.io`.
- `https://message-relay.org` loads over HTTPS without certificate warnings.
- `https://www.message-relay.org` redirects to your configured primary domain.

## 5) Ongoing updates

For future content or style changes:

```bash
git add index.html styles.css README.md GH_PAGES_DEPLOYMENT.md
git commit -m "Update landing page content/styles"
git push
```

Pages auto-redeploys after each push to the configured branch.

## Troubleshooting

- **404 page**: verify Pages source branch/folder is correct.
- **No styles**: confirm `styles.css` is in repo root and linked as `./styles.css`.
- **Old content still showing**: hard refresh browser and wait for Pages build completion.
- **Custom domain not resolving**: check exact `A/AAAA/CNAME` values, remove conflicting records, and allow DNS propagation time.
