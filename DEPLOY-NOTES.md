# codes.gallery deploy notes

## Current architecture
- **Domain:** `codes.gallery`
- **WWW redirect:** `www.codes.gallery` → `codes.gallery`
- **Hosting:** Cloudflare Pages
- **Source repo:** `https://github.com/theframes84-bit/codes-gallery`
- **Legacy host:** Gandi VPS config/files for `codes.gallery` removed
- **Separate site:** `vgallery.space` remains independent on VPS/WordPress

## Local source folder
`/home/dataspace/.openclaw/workspace/cloudflare/codes.gallery`

## Main deployment flow
1. Edit files in the local source folder.
2. Preview locally if needed:
   - `file:///home/dataspace/.openclaw/workspace/cloudflare/codes.gallery/index.html`
3. Commit changes:
   ```bash
   cd /home/dataspace/.openclaw/workspace/cloudflare/codes.gallery
   git status
   git add .
   git commit -m "Describe the change"
   ```
4. Push to GitHub:
   ```bash
   git push
   ```
5. Cloudflare Pages auto-deploys from the GitHub repo.
6. Verify live site:
   - `https://codes.gallery`
   - `https://codes.gallery/archive1`
   - `https://www.codes.gallery`

## GitHub auth note
If `git push` asks for a password over HTTPS, use:
- **Username:** `theframes84-bit`
- **Password:** GitHub Personal Access Token (classic), not the normal GitHub password

## Current repo details
- **Repo:** `theframes84-bit/codes-gallery`
- **Default branch:** `main`

## Cloudflare notes
- Working long-term setup is **Pages from GitHub**.
- The earlier Worker/Git-URL flow was a dead end and can be ignored.
- Old unused Worker projects can be cleaned up if they have no domains/routes.

## Known asset paths
These files are expected in the repo root or assets folder:
- `index.html`
- `archive1.html`
- `social-card.png`
- `assets/tesseract_original_motion_wireframe.gif`

## If archive thumbnail breaks again
Check that `archive1.html` uses:
```html
<img class="archive-thumb" src="assets/tesseract_original_motion_wireframe.gif" alt="Harness Loop thumbnail" />
```

## If Cloudflare Git deploy breaks
Preferred retry path:
1. Open Cloudflare Pages project (not Worker import).
2. Confirm repo is `theframes84-bit/codes-gallery`.
3. Confirm branch is `main`.
4. Let Pages build/deploy from GitHub.
5. Avoid Worker Git-URL import for this site.
