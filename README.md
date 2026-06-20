# nouraroussi.github.io

Personal resume website — auto-deploys via GitHub Pages.

## Deploy Steps

### 1. Create the repo on GitHub

- Go to https://github.com/new
- Name: `nouraroussi.github.io`
- Visibility: **Public**
- Do NOT add a README (already exists)
- Click **Create repository**

### 2. Push the code

```bash
cd ~/nouraroussi.github.io
git init
git add .
git commit -m "Initial commit: resume site"
git branch -M main
git remote add origin https://github.com/nouraroussi/nouraroussi.github.io.git
git push -u origin main
```

### 3. Verify GitHub Pages

- Go to https://github.com/nouraroussi/nouraroussi.github.io/settings/pages
- Source: **Deploy from a branch**
- Branch: `main` / `/ (root)`
- Click **Save**

### 4. Visit the site

```
https://nouraroussi.github.io
```

Live within 1-2 minutes after pushing.

## Custom Domain (Optional)

1. Buy a domain (e.g., `nouraroussi.com`)
2. Add a `CNAME` file to this repo containing: `nouraroussi.com`
3. In your domain registrar, add DNS records:
   - `A` records pointing to GitHub Pages IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - `CNAME` for `www` → `nouraroussi.github.io`
4. Enable "Enforce HTTPS" in GitHub Pages settings

## Author

**Nour Aroussi** — Cloud Security & Network Engineer
