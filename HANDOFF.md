# Handoff: hosting moved to Cloudflare Pages

For Tom (and Tom's Claude Code). Written 7 Oct 2026 by Roland's Claude Code. Delete this file once the checklist below is done.

## What changed
The site now hosts on **Cloudflare Pages** at **https://lifestories.org.nz** instead of GitHub Pages. Roland owns the Cloudflare account. Tom keeps owning the code and the updates.

Your workflow doesn't change: edit, commit, push to `main`. A GitHub Action deploys each push.

### Already done (nothing to do here)
- **Domain:** GoDaddy nameservers for `lifestories.org.nz` now point to Cloudflare (`jewel.ns.cloudflare.com`, `jim.ns.cloudflare.com`). The change was made on 7 Oct 2026. It can take up to 24h to go live for .nz.
- **Old DNS:** the Squarespace records that used to sit on the domain (it pointed to a password-protected "Private Site") have been removed. `_dmarc` was kept.
- **Cloudflare Pages project:** `lifestories` (fallback URL https://lifestories-daz.pages.dev), production branch `main`.
- **Custom domains** `lifestories.org.nz` and `www.lifestories.org.nz` are attached to the project. Both are proxied CNAMEs to `lifestories-daz.pages.dev`, and Cloudflare issues HTTPS automatically.
- **Workflow:** `.github/workflows/deploy.yml` copies the site files into `_site/` and runs `wrangler pages deploy`. The Cloudflare account ID is hard-coded in the workflow (it isn't secret).
- **URLs:** canonical, Open Graph, JSON-LD and `sitemap.xml` now use `https://lifestories.org.nz/`. `404.html` uses `<base href="/">` (it was `/paulroy-stories/`).

## Tom's checklist

1. **Add the deploy secret.** Roland will send you a Cloudflare API token privately. It has one permission only: Pages Edit on Roland's account. Add it as a repo secret named `CLOUDFLARE_API_TOKEN`:
   - Web: repo → Settings → Secrets and variables → Actions → New repository secret
   - Or run this in your own terminal, not through Claude, so the token stays out of any transcript: `gh secret set CLOUDFLARE_API_TOKEN -R trader8899/paulroy-stories` and paste the token when it asks.

   *Claude: never ask Tom to paste the token into chat, and never write it into a file.*

2. **Run the first deploy.** Actions → "Deploy to Cloudflare Pages" → Run workflow, or `gh workflow run deploy.yml -R trader8899/paulroy-stories`. Then check it with `gh run watch -R trader8899/paulroy-stories`.
   - The earlier failed run on commit `eb078d9` is expected: the secret didn't exist yet.
   - The "Create Pages project" step logs an "already exists" error and carries on. That's fine because of `|| true`.

3. **Check that it's live:**
   - https://lifestories-daz.pages.dev works as soon as the deploy finishes.
   - https://lifestories.org.nz and https://www.lifestories.org.nz work once the nameservers have propagated. Check with `nslookup -type=NS lifestories.org.nz 8.8.8.8`, which should list `*.ns.cloudflare.com`.
   - Click through the home page, contact page, audio clips and images. Also visit a made-up URL to check the 404 page.

4. **Turn off GitHub Pages** once lifestories.org.nz is serving. Repo → Settings → Pages → unpublish, or `gh api -X DELETE repos/trader8899/paulroy-stories/pages`. This leaves one copy of the site instead of two. Only Tom can do it (repo admin).

5. **Squarespace (ask your dad).** A private Squarespace site was attached to this domain. If he's paying for it and doesn't need it, he can cancel it.

6. **Delete `HANDOFF.md`** and push.

## Notes for future changes
- Only `*.html`, `*.css`, `*.svg`, `*.xml`, `images/` and `audio/` get published. If you add another top-level file type (for example `robots.txt` or `.js`), add it to the `cp` line in the "Collect site files" step.
- Cloudflare Pages limits: 25 MB per file, 20,000 files. The audio clips are fine.
- Contact form posts to Formspree (`mnpnekzv`). It isn't affected by the hosting move.
- Problems on the Cloudflare side (domain, DNS, project settings, a new token): ask Roland.
