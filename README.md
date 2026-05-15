# klovar-edits.com

Static landing page for **klovar-edits**.
Hosted on GitHub Pages, served from the apex domain `klovar-edits.com`.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The landing page |
| `styles.css` | Styles (Space Grotesk, orange/black palette) |
| `assets/wordmark.png` | The illuminated K·E wordmark (v17c) |
| `favicon.svg` | Favicon |
| `CNAME` | Tells GitHub Pages the custom domain |
| `.nojekyll` | Skips Jekyll processing |

---

## Local preview

From this folder:

```powershell
# Python (already installed for MIKI)
python -m http.server 8000
```

Then open <http://localhost:8000>.

---

## First-time GitHub deploy

You only do this once. After that, see "Updating".

### 1. Create the repo on GitHub
- Sign in to GitHub
- Click **New repository**
- Name: `klovar-edits` (or `klovar-edits.com` — either works)
- Visibility: **Public** (required for free GitHub Pages on a custom domain)
- **Do not** add a README, .gitignore, or license (this folder already has the files)
- Click **Create repository**

GitHub will show you a page with a URL like `https://github.com/<your-username>/klovar-edits.git`. Copy it.

### 2. Push this folder up

From inside the `WEBSITE` folder, in PowerShell:

```powershell
git init
git add .
git commit -m "Initial landing page"
git branch -M main
git remote add origin https://github.com/<your-username>/klovar-edits.git
git push -u origin main
```

### 3. Turn on GitHub Pages
- On the repo page → **Settings** → **Pages** (left sidebar)
- **Source**: Deploy from a branch
- **Branch**: `main` / root (`/`)
- Click **Save**
- Under **Custom domain**, the field should auto-fill from the `CNAME` file with `klovar-edits.com`. If not, type it in and save.
- Tick **Enforce HTTPS** once it becomes available (can take a few minutes after DNS propagates).

### 4. Point the domain at GitHub Pages

At your domain registrar (wherever you bought `klovar-edits.com`), set these DNS records:

**For the apex `klovar-edits.com`** — four A records:
```
A    @    185.199.108.153
A    @    185.199.109.153
A    @    185.199.110.153
A    @    185.199.111.153
```

**For `www.klovar-edits.com`** — one CNAME:
```
CNAME    www    <your-username>.github.io
```

DNS usually propagates in 5–60 minutes. Once it does, https://klovar-edits.com should serve this page.

---

## Updating the page

After first-time setup, every change is just three commands from this folder:

```powershell
git add .
git commit -m "What you changed"
git push
```

GitHub Pages rebuilds in ~30 seconds. Hard-refresh your browser (Ctrl+F5 in Opera GX) to see the new version.

---

## Notes

- The PNG wordmark is large (~1MB). If load time matters later, export an SVG version of v17c and swap it in.
- The `Space Grotesk` font loads from Google Fonts. If you want to drop the external dependency, self-host it later.
- This is a **landing** page only — no portfolio, no rate card, no inquiry form yet. Add those as separate sections or pages when ready.
