# Paul Roy: oral histories website

A simple two-page site (home + contact) built for GitHub Pages. No build tools needed.

## Files
- `index.html` home page: intro, how it works, sample interviews, about Paul, pricing
- `contact.html` contact details and enquiry form
- `style.css` all the styling (colours are at the top)
- `images/` hero image, Paul's portrait, and six placeholder interview photos
- `audio/` put the six sample clips here, named `interview-1.mp3` to `interview-6.mp3`

## Still to fill in
Anything highlighted yellow on the site is a placeholder. Search the HTML for `class="ph"` to find them all.
When finished, delete the `.ph` rule near the top of `style.css`.

1. Interview photos: replace `images/interview-1.jpg` to `interview-6.jpg` (square photos work best, about 600 x 600 px).
2. Audio clips: add MP3s to `audio/`. Keep each short (1 to 3 minutes) and under 10 MB. GitHub's hard limit is 100 MB per file.
3. Paul's background sentence in the "Hi, I'm Paul" section.
4. Prices for the optional extras, and the GST note under $750.
5. Email and phone on `contact.html` (replace `EMAIL` and `PHONE` in the links too).
6. Contact form: sign up free at formspree.io with Paul's email, create a form, and replace `YOUR_FORM_ID` in `contact.html`.
7. Testimonials: a ready-made section is commented out in `index.html`. Switch it on once there are real quotes.

## Hosting
The live site is **https://lifestories.org.nz**, hosted on Cloudflare Pages (Roland's Cloudflare account).

Every push to `main` deploys automatically through GitHub Actions (`.github/workflows/deploy.yml`). Check the **Actions** tab to see each deploy. To redeploy without changes, open the workflow there and click **Run workflow**.

The workflow needs one repository secret, `CLOUDFLARE_API_TOKEN` (Settings > Secrets and variables > Actions). Roland supplies the token.

Only the site files are published: `*.html`, `*.css`, `*.svg`, `*.xml`, `images/` and `audio/`. If you add a new top-level file type, add it to the "Collect site files" step in the workflow.
