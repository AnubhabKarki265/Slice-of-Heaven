# Slice of Heaven — Cloudflare Pages Deploy

Static single-page site. Deploy via **GitHub → Cloudflare Pages** and attach the custom domain **anubhab.shop**.

---

## Step 1 — Push to GitHub

This folder is already a git repo with an initial commit. On your machine:

```bash
cd ~/Downloads/slice-of-heaven        # (or wherever you saved it)

# create a new empty GitHub repo first (github.com/new) — don't add a README.
# then point this local repo at it:
git remote add origin https://github.com/<your-username>/slice-of-heaven.git
git branch -M main
git push -u origin main
```

## Step 2 — Connect Cloudflare Pages to GitHub

1. Log in to [dash.cloudflare.com](https://dash.cloudflare.com).
2. Left sidebar → **Workers & Pages** → **Create** → **Pages** tab → **Connect to Git**.
3. Authorize Cloudflare to access your GitHub, then pick the `slice-of-heaven` repo.
4. Build settings — leave everything blank / default, just set:
   - **Framework preset:** `None`
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` *(root)*
   - **Root directory:** *(leave empty)*
5. Click **Save and Deploy**. It builds in ~30 seconds and gives you a URL like `slice-of-heaven.pages.dev`.

## Step 3 — Attach anubhab.shop

After the first deploy succeeds:

1. In the Pages project, go to the **Custom domains** tab.
2. Click **Set up a custom domain** → enter `anubhab.shop` → **Continue**.
3. Because the zone is already in your Cloudflare account, it auto-creates the CNAME for you — just click **Activate domain**.
4. Optionally repeat for `www.anubhab.shop`.
5. SSL provisions within a minute or two. You're live at **https://anubhab.shop**.

## Making changes

```bash
# edit index.html, then:
git add .
git commit -m "update copy"
git push
```

Cloudflare Pages auto-rebuilds on every push to `main`.

---

## Notes

- The site is one file (`index.html`) with all CSS/JS inline. No build step, no dependencies.
- Pizza and reviewer images are loaded from Unsplash (permissive license, hotlinking allowed). Swap them later if you want your own.
- The oven temperature widget flickers every 2.5s for flavor.
