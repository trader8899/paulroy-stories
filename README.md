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

## Putting it online with GitHub Pages
1. Create a free account at github.com.
2. Click **New repository**. Name it e.g. `paulroy-stories`, set it to **Public**, and create it.
3. Click **uploading an existing file**, drag in everything from this folder (keep the `images` and `audio` folders), and click **Commit changes**.
4. Go to **Settings > Pages**. Under "Build and deployment", choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. After a minute or two the site appears at `https://YOUR-USERNAME.github.io/paulroy-stories/`.

## Custom domain (optional)
Buy a domain (e.g. from a NZ registrar), then in **Settings > Pages > Custom domain** enter it and follow GitHub's DNS instructions. Tick **Enforce HTTPS** once it's available.
