# GitHub Pages Deployment Guide

This guide walks you through deploying your portfolio to GitHub Pages.

## Prerequisites

- Git installed on your machine
- A GitHub account
- Your portfolio repository ready (as it currently is)

## Option 1: Deploy to `username.github.io` (Main Site)

This creates your portfolio at `https://suraiyaahmed.github.io/`

### Steps:

1. **Create a new GitHub repository**
   - Go to https://github.com/new
   - Name it: `suraiyaahmed.github.io` (replace `suraiyaahmed` with your GitHub username)
   - Description: "Personal Portfolio - Finance & HR Professional"
   - Make it **Public**
   - Click "Create repository"

2. **Update your local Git configuration**
   ```bash
   # Navigate to your portfolio directory
   cd d:\Mother_Folder\Tithy_Mother_Folder\portfolio
   
   # Update the remote URL
   git remote remove origin
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io.git
   ```

3. **Update `_config.yml`**
   - Change `baseurl:` from `/portfolio` to `` (empty)
   - Update `url:` to `https://YOUR_USERNAME.github.io`
   
   ```yaml
   url: https://suraiyaahmed.github.io
   baseurl: ""
   ```

4. **Push to GitHub**
   ```bash
   git branch -M main
   git push -u origin main
   ```

5. **Enable GitHub Pages**
   - Go to your repository: https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io
   - Click **Settings** → **Pages**
   - Under "Source", select **Deploy from a branch**
   - Branch: `main` / `/(root)`
   - Click **Save**

6. **Wait for deployment**
   - GitHub will build and deploy automatically
   - Check back in 1-2 minutes
   - Your site will be live at `https://suraiyaahmed.github.io/`

---

## Option 2: Deploy to a Repository (`gh-pages` branch)

This creates your portfolio at `https://username.github.io/portfolio/`

### Steps:

1. **Create a new GitHub repository**
   - Go to https://github.com/new
   - Name it: `portfolio` (or any name you prefer)
   - Description: "Personal Portfolio - Finance & HR Professional"
   - Make it **Public**
   - Click "Create repository"

2. **Update your local Git configuration**
   ```bash
   cd d:\Mother_Folder\Tithy_Mother_Folder\portfolio
   
   git remote remove origin
   git remote add origin https://github.com/YOUR_USERNAME/portfolio.git
   ```

3. **Verify `_config.yml` has correct baseurl**
   ```yaml
   url: https://suraiyaahmed.github.io
   baseurl: /portfolio
   ```

4. **Create and push to `gh-pages` branch**
   ```bash
   # Create orphan gh-pages branch
   git checkout --orphan gh-pages
   
   # Or if using an existing branch:
   git checkout -b gh-pages
   git push -u origin gh-pages
   ```

5. **Enable GitHub Pages**
   - Go to your repository: https://github.com/YOUR_USERNAME/portfolio
   - Click **Settings** → **Pages**
   - Under "Source", select **Deploy from a branch**
   - Branch: `gh-pages` / `/(root)`
   - Click **Save**

6. **Your site will be live at**
   - `https://suraiyaahmed.github.io/portfolio/`

---

## Automated Deployment with GitHub Actions

For automatic builds on every push, create `.github/workflows/jekyll.yml`:

```yaml
name: Build and Deploy Jekyll

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  jekyll:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Build with Jekyll
        uses: helaili/jekyll-action@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          target_branch: gh-pages
```

---

## Custom Domain Setup

To use your custom domain `suraiyaahmed.com`:

1. **Update DNS records** with your domain provider:
   - Add an `A` record pointing to GitHub's IP
   - Or add a `CNAME` record pointing to `USERNAME.github.io`

2. **Configure in GitHub**
   - Repository → Settings → Pages
   - Under "Custom domain", enter `suraiyaahmed.com`
   - Click "Save"
   - Check "Enforce HTTPS"

3. **Update `_config.yml`**
   ```yaml
   url: https://suraiyaahmed.com
   baseurl: ""  # or /portfolio if using subdirectory
   ```

---

## Verification Checklist

After deployment:

- [ ] Site is accessible at the correct URL
- [ ] All images load properly
- [ ] Navigation links work
- [ ] Profile photo appears in header
- [ ] Blog, research, and projects display
- [ ] Mobile responsive layout works
- [ ] No 404 errors in Console

---

## Troubleshooting

### Site not building?
- Check GitHub Actions tab in repository settings
- Review build logs for Jekyll errors
- Ensure `Gemfile` is up to date: `bundle install`

### Images not showing?
- Verify `baseurl` is correct in `_config.yml`
- Check image paths start with `/`
- Clear browser cache (Ctrl+Shift+Del)

### HTTPS not working?
- In GitHub Pages settings, enable "Enforce HTTPS"
- Wait 10-15 minutes for certificate generation

### Domain not resolving?
- Verify DNS records are correct
- Give DNS changes 24-48 hours to propagate
- Check GitHub Pages custom domain settings

---

## Push Updates

After deployment, whenever you update content:

```bash
# Make changes to your files
# Then:

git add .
git commit -m "Update: describe your changes"
git push origin main
```

GitHub will automatically rebuild and redeploy your site!

---

## Local Testing Before Deployment

Always test locally first:

```bash
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000/` to see your site before pushing live.

---

## Need Help?

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Actions for Jekyll](https://github.com/helaili/jekyll-action)
