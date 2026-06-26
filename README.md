# nouraroussi.github.io

Personal resume website — auto-deploys via GitHub Pages with automated Credly badge updates.

## Features

- **Single-page resume** — Skills, certifications, experience timeline, GitHub projects
- **Automated badge updates** — GitHub Actions workflow fetches Credly badges weekly
- **Dark mode** — Toggle with localStorage persistence
- **Responsive** — Mobile-friendly layout with sticky navigation
- **Security hardened** — CSP meta tag, XSS-safe DOM manipulation, email/phone obfuscation
- **SEO ready** — Open Graph tags, social preview image, sitemap.xml, robots.txt
- **Print stylesheet** — Clean output when printed (hides floating badges, nav, buttons)
- **Floating badge background** — Decorative animated certification badges (toggleable)

## How the Badge Automation Works

The workflow (`.github/workflows/update-badges.yml`) runs every Monday at 8am UTC:

1. Fetches all public badges from `credly.com/users/<username>/badges.json`
2. Filters out expired badges
3. Sorts certifications by tier (configured in `get_priority()`)
4. Updates `index.html`:
   - `const certs = [...]` — displayed badges (excludes stackable)
   - `const badges = [...]` — floating background (includes stackable)
   - `const count = N` — number of floating badges
5. Commits and pushes if anything changed

### To customize for your own profile:

1. Replace `nouraroussi` with your Credly username in the workflow file
2. Update the `get_priority()` function to match your certifications
3. Trigger manually: **Actions** → **Update Credly Badges** → **Run workflow**

## Deploy Steps

### 1. Create the repo on GitHub

- Go to https://github.com/new
- Name: `<yourusername>.github.io`
- Visibility: **Public**
- Do NOT add a README (already exists)
- Click **Create repository**

### 2. Push the code

```bash
cd ~/<yourusername>.github.io
git init
git add .
git commit -m "Initial commit: resume site"
git branch -M main
git remote add origin https://github.com/<yourusername>/<yourusername>.github.io.git
git push -u origin main
```

### 3. Verify GitHub Pages

- Go to `https://github.com/<yourusername>/<yourusername>.github.io/settings/pages`
- Source: **Deploy from a branch**
- Branch: `main` / `/ (root)`
- Click **Save**

### 4. Visit the site

```
https://<yourusername>.github.io
```

Live within 1-2 minutes after pushing.

## Customization

| What | Where |
|------|-------|
| Name, title, summary | `index.html` — header section |
| Skills list | `index.html` — Skills section |
| Experience & Education | `index.html` — timeline section |
| Badge ordering | `.github/workflows/update-badges.yml` — `get_priority()` |
| Credly username | `.github/workflows/update-badges.yml` — curl URL |
| Social preview image | `preview.png` — regenerate with your own info |
| Colors/theme | `index.html` — CSS variables (`#4f46e5` is the primary indigo) |

## Custom Domain (Optional)

1. Buy a domain (e.g., `yourdomain.com`)
2. Add a `CNAME` file to this repo containing: `yourdomain.com`
3. In your domain registrar, add DNS records:
   - `A` records pointing to GitHub Pages IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - `CNAME` for `www` → `<yourusername>.github.io`
4. Enable "Enforce HTTPS" in GitHub Pages settings

## File Structure

```
├── index.html                          # Main resume page
├── preview.png                         # Social preview image (og:image)
├── sitemap.xml                         # SEO sitemap
├── robots.txt                          # Search engine crawl rules
├── README.md                           # This file
└── .github/workflows/update-badges.yml # Automated badge update workflow
```

## Author

**Nour Aroussi** — Cloud Security & Network Engineer
