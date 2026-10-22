# The Fine Line

Your art portfolio site — plain HTML/CSS/JS, no build tools required.

## Pages

- `index.html` — home page with hero + featured work
- `gallery.html` — the full gallery
- `about.html` — bio and contact details

## Adding or replacing artwork

You never need to touch the HTML to add new art. Everything the gallery shows comes from one file:

`assets/js/gallery-data.js`

1. Drop your image file into `assets/images/` (jpg, png, or webp all work).
2. Open `assets/js/gallery-data.js` and copy one of the existing entries, e.g.:
   ```js
   {
     title: "Your Piece Title",
     category: "Illustration",
     image: "assets/images/your-file.jpg",
     description: "A line or two about the piece.",
     featured: true
   },
   ```
3. Set `featured: true` if you also want it to show on the home page; `false` keeps it in the gallery only.
4. Save the file. That's it — both `index.html` and `gallery.html` read from this same list.

Update the placeholder text and email/social links in `about.html` whenever you're ready.

## Going live on GitHub Pages

1. Push this branch, then merge it into `main` (or open the PR and merge it) so `main` has these files.
2. In the GitHub repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch", pick `main` and `/ (root)`, then **Save**.
4. GitHub will publish the site at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## Wrapping your own domain around it

Once Pages is live:

1. Still in **Settings → Pages**, under **Custom domain**, enter your domain (e.g. `thefineline.com` or `www.thefineline.com`) and save. GitHub will create a `CNAME` file in the repo automatically.
2. At your domain registrar (wherever you bought the domain), add DNS records pointing to GitHub:
   - For an apex domain (`thefineline.com`), add **A records** pointing to:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - For a `www` subdomain, add a **CNAME record** pointing to `<your-username>.github.io`.
3. Back in **Settings → Pages**, once DNS has propagated (can take up to a few hours), tick **Enforce HTTPS**.

Tell me your exact domain name and I can add the `CNAME` file and double-check the DNS records for you directly.

## Once your domain is live

Each page has `og:image` tags (used for link previews on social media, iMessage, Discord, etc.) that currently point to a relative image path. Once your domain is wrapped, tell me the URL and I'll update those to full `https://yourdomain.com/...` links so previews render correctly everywhere.

## Gallery features

- **Click any artwork** to open it full-size in a lightbox. Use the arrows, or your keyboard's left/right and Escape keys, to browse.
- **Filter buttons** on the Gallery page are generated automatically from whatever `category` values exist in `assets/js/gallery-data.js` — add a new category there and a filter button appears on its own.
