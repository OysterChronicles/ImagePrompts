# Prompt Playground

A single-page directory of 400 image-generation slash commands (`/headshot`, `/liquidsculpture`, etc.), each with a category, description, and suggested combination. Built as one self-contained `index.html` file — no build step, no dependencies, no backend.

**Features**
- Browse all 400 commands, grouped into 23 categories
- Live search with autofill suggestions
- Filter by category
- Multi-select prompts and copy them combined
- Favourite prompts (saved in the browser via `localStorage`)
- "Surprise Me" — build a random shortlist, add more, remove any, copy or save to Selected
- Fully responsive / mobile-friendly

## Project structure

```
.
├── public/
│   └── index.html  # the entire app (HTML + CSS + JS, self-contained)
├── vercel.json      # Vercel static-hosting config (outputDirectory: "public")
├── package.json    # project metadata (no real build step required)
└── .gitignore
```

## Running locally

No build tools required. Either:

- Open `public/index.html` directly in a browser, or
- Serve it locally:
  ```bash
  npx serve public
  ```
  then open the printed local URL.

## Deploying to GitHub

1. Create a new repository on GitHub (via the web UI, or `gh repo create`).
2. From this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Prompt Playground"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

## Deploying to Vercel

**Option A — via the Vercel dashboard (no CLI needed)**
1. Push this project to GitHub first (see above).
2. Go to [vercel.com/new](https://vercel.com/new) and import the GitHub repository.
3. Vercel will detect it as a static site — no framework preset or build command needed. Leave the defaults and click **Deploy**.

**Option B — via the Vercel CLI**
```bash
npm install -g vercel
vercel login
vercel        # deploys a preview
vercel --prod # deploys to production
```

No environment variables or backend services are required — everything runs client-side in the browser.

## Troubleshooting: "No Output Directory named 'public' found"

If Vercel shows this error, it means your project's dashboard setting (Settings → Build & Deployment → Output Directory) is set to `public`. This repo already matches that (the app lives at `public/index.html`, and `vercel.json` declares `"outputDirectory": "public"`), so a fresh deploy from this structure should resolve it. If you'd rather not use a `public` folder, go to your Vercel project's Settings → Build & Deployment and clear the Output Directory field (or set it to `.`) instead.

## Notes

- Favourites are stored per-browser via `localStorage`; they are not synced across devices or shared between visitors.
- Fonts (Baloo 2, Poppins) load from Google Fonts at runtime — an internet connection is needed for them to render as intended; the page falls back to system fonts otherwise.
