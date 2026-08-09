# The Scentral Park — website build

A static, multi-page build for The Scentral Park. No build step, no dependencies — just HTML files, a shared stylesheet, and the `assets` folder.

## What's in here

```
.
├── index.html               Home — overview, teasers, links out to each page
├── sensory-garden.html       Full page: zones, session types, real pricing
├── boarding.html             Full page: facility, tiers, real pricing
├── puppy-play-date.html      Full page: age range, rules, real pricing
├── cafe.html                 Full page: real menu and pricing
├── about.html                 Full page: founding story, real team, testimonials
├── grooming.html             Placeholder page — stock photos, no real facts yet
├── locations.html            Map, coming-soon card, franchise enquiry
├── cancellation-refunds.html      Real policy content
├── health-safety-disclaimer.html  Real policy content
├── driver-safety-disclaimer.html  Real policy content
├── e-permits.html                 Real policy content
├── privacy-policy.html            Real policy content
├── terms-conditions.html          Real policy content
├── assets/
│   ├── css/main.css          Shared stylesheet, used by every page
│   ├── img/                  Real photos (uploaded by the client) + licensed stock photos
│   └── video/                 Real video clips (uploaded by the client, compressed for web)
└── README.md
```

All eight pages are built and cross-linked — this is a complete site, not a single homepage concept anymore.

## Adding or editing a page

1. Copy the closest existing page as a starting template (e.g. `boarding.html` for another pricing-driven service page) — it already wires up the shared header, footer, and stylesheet.
2. Swap in real content (the pattern so far: a `.page-hero`, then `.feature` blocks, then anything specific like `.pricing` or `.zones`).
3. Update the nav bar in **every** page (not just Home) if you add or rename a page — each page currently repeats its own copy of the header.

## Known placeholders (swap before this goes live)

- **Grooming** — the entire page runs on stock photography (Pexels), with no real pricing or service details, since no real content or photos exist for it yet. Send real photos/facts whenever available and this page should be rebuilt around them, following the pattern of the other service pages.
- **Mud** and **sand** zone cards on Sensory Garden use general garden photos — no zone-specific footage was available yet.
- **South Bangalore** location card uses a generic park photo — not real photography of that (not-yet-built) location.
- All "Get the app" buttons point to `#` — wire these up to actual App Store / Play Store links, or a deferred-deep-link service, once the app listing exists.
- Footer legal links (Privacy Policy, Terms, etc.) point to `#` — these need real pages, not something to draft here.
- The franchise enquiry CTA on Locations opens a `mailto:` link — fine for now, but likely wants a real form once enquiry volume picks up.

## Deploy to a real domain

### Option A — GitHub Pages (free, good for a client-facing preview)

1. Create a new GitHub repo and push this folder to it:
   ```bash
   git init
   git add .
   git commit -m "Initial site build"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main / (root)**. Save.
3. GitHub gives you a live URL within a minute or two, at `https://<your-username>.github.io/<repo-name>/`.
4. **For a custom domain**: add a file named `CNAME` (no extension) to the repo root containing just your domain, then add a `CNAME` DNS record pointing that subdomain to `<your-username>.github.io`.

### Option B — Netlify or Vercel (also free, drag-and-drop, no git required)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop) (or the Vercel equivalent).
2. Drag this whole folder onto the page.
3. You'll get a live `*.netlify.app` URL immediately.
4. Both support adding a custom domain under **Site settings → Domain management**.

### A note on repo size

The `assets/video` folder is ~7MB and `assets/img` is ~1.5MB — fine for git, but if you keep adding real video footage, consider [Git LFS](https://git-lfs.com/) once the repo starts growing past a few hundred MB, so clones stay fast.

## Versioning

Every page's footer shows a version number (`v2026.07.001`), format `YYYY.MM.NNN`. Bump the last segment on each meaningful deploy (new page, content fix, real bug fix) — not on every tiny tweak. Roll to a new month segment (e.g. `2026.08.001`) whenever you deploy in a new calendar month, resetting the counter. Update it in the footer of all eight pages together, since they should always agree.

## Local preview

No server needed — just open `index.html` directly in a browser. If you want it served properly (some browsers restrict video autoplay differently over `file://`), run from inside this folder:

```bash
python3 -m http.server 8000
```

then visit `http://localhost:8000`.
