# Series A — Website

A two-page marketing + newsroom site for **Series A**, built as static HTML/CSS/JS with no build step or dependencies. Ready to deploy as-is on GitHub Pages, Netlify, Vercel, or any static host.

## Structure

```
.
├── index.html                  # Landing page (hero, stories, spotlight, index, community)
├── seriesa-main-screen.html    # Newsroom / publication page
├── assets/
│   ├── css/
│   │   ├── index.css           # Styles for the landing page
│   │   └── newsroom.css        # Styles for the newsroom page
│   ├── js/
│   │   ├── index.js            # Scroll reveals, ticker, avatar cluster, etc.
│   │   └── newsroom.js         # Newsroom data + rendering logic
│   └── images/                 # All local photography used on the landing page
└── README.md
```

The two pages are linked to each other via the **Publication** nav item:
- On `index.html`, "Publication" links to `seriesa-main-screen.html`.
- On `seriesa-main-screen.html`, "Publication" links back to `index.html`.

Because these are relative links, keep both HTML files at the same directory level.

## Running locally

No build step is required — it's plain HTML/CSS/JS. Any static file server works:

```bash
# Option 1: Python
python3 -m http.server 8000

# Option 2: Node (if you have it)
npx serve .
```

Then open `http://localhost:8000` in your browser.

Opening `index.html` directly by double-clicking also works, since all assets are referenced with relative paths.

## Deploying to GitHub Pages

1. Push this folder to a GitHub repository (see commands below).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch".
4. Choose the `main` branch and `/ (root)` folder, then save.
5. GitHub will publish the site at `https://<your-username>.github.io/<repo-name>/`.

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Notes on content

- Images used in the newsroom page's story/news cards are loaded from Unsplash by URL (see `assets/js/newsroom.js`) rather than stored locally — swap those URLs for your own hosted images whenever you're ready.
- All bylines are attributed generically to "SeriesA Journalist"; update `assets/js/newsroom.js` and the hero byline in `seriesa-main-screen.html` if you want named authors again.
- The "In the News" data feeding the newsroom's ticker/cards lives directly in `assets/js/newsroom.js` (`cardStories`, `newsFeed`, `picks` arrays) — edit those objects to change headlines, categories, and images without touching any markup.
