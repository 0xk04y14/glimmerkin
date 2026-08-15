# Glimmerkin — static, no-JS site

A landing page for the [Glimmerkin NFT collection](https://opensea.io/collection/glimmerkin) built with plain HTML and CSS only — **zero JavaScript**, no build step, no framework.

- The mobile nav menu uses the CSS-only "checkbox hack" (a hidden `<input type="checkbox">` + a `<label>`).
- The FAQ accordion uses native `<details>`/`<summary>`, which the browser handles with no script.
- All artwork (logo, hero image, and the 8 soul thumbnails) is pulled from your live OpenSea listing, so it always matches the real collection.

## Fixing "No Next.js version detected" on Vercel

If your Vercel project was previously deployed as a Next.js app (even in an earlier attempt), Vercel stores that choice in the project's **Framework Preset** setting and keeps running `next build` even after you push a plain static site with no `package.json`. That's what causes:

```
Error: No Next.js version detected. Make sure your package.json has "next"...
```

This repo includes a `vercel.json` with `"framework": null`, which tells Vercel this is a plain static site. But the dashboard setting can still override it, so also do this once:

1. Open the project in Vercel → **Settings → General → Framework Preset**.
2. Change it from **Next.js** to **Other**.
3. Save, then go to **Deployments** → redeploy the latest commit (or push any new commit).

After that, Vercel will just serve `index.html` and `css/styles.css` directly — no build step at all.

## Structure


```
index.html       All markup and content
css/styles.css   All styling
```

## Run locally

Just open `index.html` in a browser — no server or install needed.

## Deploy on GitHub Pages

```bash
git init
git add .
git commit -m "Glimmerkin static site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```
Then in the repo: **Settings → Pages** → Source: `main` branch, root folder. Your site goes live at `https://<your-username>.github.io/<repo-name>/`.

## Deploy on Vercel

Import the repo at [vercel.com/new](https://vercel.com/new). Framework preset: **Other**, no build command, output directory `.`. Deploy.

## Editing content

Everything — the 8 souls, stats, roadmap, FAQ — is written directly in `index.html`. To update supply, floor price, or owners, edit the numbers inside the `<ul class="stat-row">` block near the top. To change socials, update the links in the `<header>` and `<footer>`.
