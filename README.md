# FengMang Video Publisher (蜂芒视频发布助手) — Static Website

Static, dependency-free website for the TikTok for Developers app application.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Landing page (English + Chinese): what the app does, TikTok Login Kit & Content Posting API usage, scopes |
| `privacy.html` | Privacy Policy (English, with Chinese summary) |
| `terms.html` | Terms of Service (English, with Chinese summary) |
| `style.css` | Shared stylesheet |
| `.nojekyll` | Tells GitHub Pages to serve files as-is (no Jekyll processing) |
| `README.md` | This file |

No external CSS, JS, fonts, or images are loaded. The only external references are plain hyperlinks to TikTok's own policies.

## Before publishing

1. Replace the contact email placeholder in all files:
   ```bash
   grep -rl --include="*.html" tangjingcheng1997@outlook.com . | xargs sed -i 's/tangjingcheng1997@outlook.com/you@example.com/g'
   ```
   (On macOS use `sed -i ''`.)
2. Review the policy text and adjust anything that does not match how your app actually works
   (for example, which AI service providers process your content materials).

## Publish on GitHub Pages

1. Create a **public** GitHub repository (e.g. `fengmang-site`), or use `<username>.github.io` for a root user site.
2. Put these files at the **root** of the repository and push:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<username>/<repo>.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   Branch: `main`, Folder: `/ (root)` → **Save**.
4. After a minute the site is live at:
   - Project site: `https://<username>.github.io/<repo>/`
   - User site: `https://<username>.github.io/`
5. Use these URLs in the TikTok developer portal:
   - Website / App URL: `https://<username>.github.io/<repo>/`
   - Privacy Policy URL: `https://<username>.github.io/<repo>/privacy.html`
   - Terms of Service URL: `https://<username>.github.io/<repo>/terms.html`

## TikTok URL verification file

TikTok for Developers may ask you to verify ownership of your URL / URL prefix by downloading a
signature file (a `.txt` file with a name like `tiktokXXXXXXXX.txt`).

- Place that file **unchanged** (same file name, same content) in the **root of the site**,
  i.e. the same folder as `index.html`.
- Commit and push it, then confirm it opens in a browser at:
  - Project site: `https://<username>.github.io/<repo>/tiktokXXXXXXXX.txt`
  - User site: `https://<username>.github.io/tiktokXXXXXXXX.txt`
- Then click **Verify** in the TikTok developer portal.

Note: TikTok verifies the exact URL prefix you register. If you register a project site
(`https://<username>.github.io/<repo>/`), the file must be reachable under that prefix (the repo root).
If TikTok requires domain-level verification instead of a URL prefix, use a user site
(`<username>.github.io` repo) or a custom domain, or use the DNS TXT record method TikTok offers.
The `.nojekyll` file ensures the `.txt` file is served without modification.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000/
```
