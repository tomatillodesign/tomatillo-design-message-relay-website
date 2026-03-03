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

## 4) Optional custom domain

If you want this available on a custom domain/subdomain:

1. In **Settings** -> **Pages**, set **Custom domain**.
2. Add DNS records at your DNS provider:
   - `CNAME` for subdomain target to `<org-or-user>.github.io`
   - or `A/AAAA` records for apex domain per GitHub docs
3. Wait for DNS propagation.
4. Enable **Enforce HTTPS** once available.

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
- **Custom domain not resolving**: validate DNS records and allow time to propagate.
