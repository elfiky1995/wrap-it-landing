# Wrap It - landing page

Static marketing site for the Wrap It Android app. Plain HTML/CSS/JS, no build step.

## Preview locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.

## Deploy

Import this repo on Vercel with the defaults (framework: Other, no build command, root
directory: the repo root). Every push to `main` redeploys.

## Things to keep in sync with the app

- `styles.css` mirrors the app's design tokens (`src/theme/` in the app repo) by hand:
  colours, brand gradient, per-tool gradients and tints, radius, shadows.
- English copy lives in `index.html`; Arabic lives in the `ar` map in `main.js`, keyed by
  `data-i18n`. Add every string to both.
- `privacy.html` repeats the home page's header and footer, with section links pointing at
  `/#section`, and loads the same `main.js`. Change both pages together. Its policy text is
  in the page itself, one `<article data-lang>` per language, so it isn't in the `ar` map.
- `app-ads.txt` must stay a plain-text file holding only the AdMob line.
- Version, APK size, minimum Android version and the tool list are hardcoded copy - update
  them when cutting a release.

## The Download button

Every Download button links to `/download`, a redirect defined in `vercel.json`. Its
`destination` is the only place the APK URL lives. The APK (~165 MB) is too large to deploy
with the site, so host it elsewhere (for example as a GitHub Release asset on a public repo)
and point the redirect at it.
