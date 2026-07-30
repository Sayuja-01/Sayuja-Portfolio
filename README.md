# Sayuja's portfolio — deploy guide

## What's in here
- `index.html` — the whole site (single file, no build step, no backend).
- `profile.jpg` — add your photo here with this exact filename, and it'll appear automatically in the hero. Until you add it, the site shows your initials ("SK") in a rose circle instead.

## Deploy on Vercel (free) — takes about 5 minutes

1. Push this folder to a GitHub repo:
   ```
   git init
   git add .
   git commit -m "Portfolio site"
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
2. Go to https://vercel.com/new and import the repo. Framework preset: "Other" — no build step needed.
3. Deploy. Your site is live at `your-project.vercel.app`.
4. (Optional) Add a custom domain under Settings → Domains.

Any static host works the same way — Netlify, GitHub Pages, Cloudflare Pages, etc. Since this is a single static HTML file, there's nothing to configure beyond uploading it.

## Editing content later
Open `index.html` in any text editor. Each section is plain HTML — search for:
- `id="page-home"` → hero, name, tagline, the 4 stat numbers
- `id="page-experience"` → each job is a `<div class="tl-item">` block
- `id="page-projects"` → each project is a `<div class="proj-card" data-date="YYYY-MM-DD">` block — projects sort themselves newest-first automatically based on that date, so just edit the date and it repositions on its own
- `id="page-skills"` → skill bars (edit the `data-w="88"` number to change the bar %)
- `id="page-about"` → About Me text
- `id="page-contact"` → email/LinkedIn/Calendly/phone, and the resume download button

To publish changes: save, then `git add . && git commit -m "update" && git push`. Vercel auto-redeploys within about a minute.

## Updating your photo or résumé after you've deployed
Both are just files sitting in this folder — `profile.jpg` and `resume.pdf`. To update either:
1. Replace the file locally (same exact filename — `profile.jpg` / `resume.pdf`).
2. `git add . && git commit -m "update resume" && git push`
3. Vercel redeploys automatically within about a minute — no code changes needed, no dashboard clicking.

If you ever rename the file (e.g. `resume_v2.pdf`), you also need to update the two spots in `index.html` that reference `resume.pdf`: the "Resume ↓" nav button and the download button on the Contact page.
