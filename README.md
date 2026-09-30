# Sydney's Wedding — Bridal Party Site

Three files, all needed together:

- **`index.html`** — public page. Countdown, venue/timeline, full bridal party roster (names + roles only), dress info, bachelorette date range, registry placeholder, FAQ, and the "Submit My Info" form.
- **`moh.html`** — private page, passcode-protected. Vendor contacts with phone numbers, full bridal party phone list, bachelorette payment tracking, and MOH-only notes.
- **`style.css`** — shared styling for both pages.

**Important: the passcode on `moh.html` is NOT real security.** This is a static site with no server, so there's no way to truly authenticate someone. Anyone who views the page's source code (right-click → "View Page Source," something any browser lets you do) can find the passcode in plain text. It will keep casual visitors and search engines out, but don't put anything on that page you'd be upset about a determined person seeing — no account numbers, no sensitive personal details beyond phone numbers.

## Before you publish

### 1. Set the private page passcode
Open `moh.html`, find this line near the bottom of the `<script>` section:
```
const PASSCODE = "sydney2027";
```
Change it to whatever you want to share with Kristian (and anyone else on the bride's team who needs access).

### 2. Connect the form
The "Submit My Info" form on the public page needs a Formspree endpoint to actually send submissions anywhere.

1. Go to **formspree.io** and create a free account
2. Create a new form
3. Copy the endpoint it gives you — looks like `https://formspree.io/f/abc1234`
4. Open `index.html`, find this line near the top of the `<script>` section:
   ```
   const FORMSPREE_ENDPOINT = "https://formspree.io/f/YOUR_FORM_ID";
   ```
   and replace the placeholder with your real endpoint
5. Submissions will show up in your Formspree dashboard (turn on email notifications there too, if you want)

## Hosting on GitHub Pages

1. Create a new repository on GitHub (public or private — Pages works either way, though a private repo needs GitHub Pro for Pages)
2. Upload all three files (`index.html`, `moh.html`, `style.css`) to the root of the repo
3. Go to the repo's **Settings → Pages**
4. Under "Source," select the branch (usually `main`) and folder `/ (root)`
5. Save — GitHub will give you a live URL, usually `https://yourusername.github.io/repo-name/`
6. It can take a minute or two to go live the first time

Share the base URL (`.../repo-name/`) with the bridal party — that's `index.html` by default. Only share `.../repo-name/moh.html` plus the passcode with Kristian and Sydney's team.

## Editing later

Everything is plain text/data inside the two HTML files — search for what you want to change and edit directly. No build step, no dependencies — just edit and re-upload to update the live site.

- Wedding details, roster, FAQ → inside `renderInfo()` and the `ROSTER`/`FAQS` arrays in `index.html`
- Private contacts, payment status → directly in the HTML body of `moh.html` (search the person's name)
