# Fantasy Recap Site — Setup

This is a minimal Jekyll blog, pre-configured for GitHub Pages. GitHub builds
and hosts it for free — no separate hosting, no build step you have to run.

## One-time setup

1. **Create a new repo on GitHub.**
   - Go to github.com → New repository
   - Name it whatever you like, e.g. `fantasy-recap` (this guide assumes that name — if you pick something else, update `baseurl` in `_config.yml` to match, e.g. `/your-repo-name`)
   - Public repo (required for free GitHub Pages on a personal account)
   - Don't initialize with a README — you already have one here

2. **Push this site to it.** From this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/fantasy-recap.git
   git push -u origin main
   ```

3. **Turn on GitHub Pages.**
   - In the repo on GitHub: Settings → Pages
   - Under "Build and deployment" → Source: **Deploy from a branch**
   - Branch: `main`, folder: `/ (root)` → Save

4. **Wait ~1 minute, then visit your site:**
   ```
   https://<your-username>.github.io/fantasy-recap/
   ```
   GitHub shows the exact URL at the top of the Pages settings once it's live.

## Publishing a new week's recap

Each post is just a markdown file in `_posts/`, named `YYYY-MM-DD-anything.md`.
The date in the filename controls sort order and the date shown on the post.

1. Get the recap content from Claude (same as before — paste it a JSON file from
   `espn_fantasy_recap.py` and it'll write the post for you, already formatted
   with the front matter block below).

2. Save it as `_posts/2026-09-22-week-2-recap.md` (bump the date and week number
   each time). Front matter goes at the top of every post:
   ```
   ---
   layout: post
   title: "Week 2 Recap"
   date: 2026-09-22
   ---

   (recap content here)
   ```

3. Push it:
   ```bash
   git add _posts/2026-09-22-week-2-recap.md
   git commit -m "Week 2 recap"
   git push
   ```

4. Give it ~30–60 seconds — GitHub rebuilds automatically. Refresh the site
   and the new post is live, newest post first.

That's the whole loop each week: run the script → upload JSON to Claude → save
the post it gives you into `_posts/` → three git commands → send the link to
your league.
