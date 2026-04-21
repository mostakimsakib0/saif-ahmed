# saif-ahmed

Hugo website powered by the Stack theme:
https://github.com/CaiJimmy/hugo-theme-stack

## Run locally

```bash
hugo server -D
```

Open: http://localhost:1313

## Build for production

```bash
hugo --gc --minify
```

## Admin Dashboard

This site uses **Decap CMS** for post management. Access the admin dashboard at:

```
https://yourusername.github.io/admin/
```

### Setup for GitHub Pages Only

**Option 1: Using GitHub Personal Access Token (Simplest)**

1. Create a GitHub Personal Access Token:
   - Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Click "Generate new token (classic)"
   - Select scopes: `repo` (full control of private repositories)
   - Copy the token

2. Use this token in the admin dashboard:
   - Open `/admin/` and authenticate with your GitHub token
   - Paste the token when prompted

**Option 2: Using GitHub OAuth App (Recommended)**

1. Create a GitHub OAuth App:
   - Go to GitHub Settings → Developer settings → OAuth Apps → New OAuth App
   - Fill in:
     - Application name: `saif-ahmed-admin`
     - Homepage URL: `https://yourusername.github.io`
     - Authorization callback URL: `https://saif-ahmed-auth.herokuapp.com/callback`
   - Copy Client ID and Client Secret

2. Deploy an Auth Proxy (free options):
   - **Option A:** Use Replit to host the auth proxy
     - Fork: https://github.com/decaporg/netlify-cms-oauth-provider
     - Deploy to Replit
     - Update `base_url` in `static/admin/config.yml` to your Replit URL
   
   - **Option B:** Use a serverless function on Vercel (free)
     - Deploy oauth proxy to Vercel
     - Update config.yml with your Vercel URL

3. Update `static/admin/config.yml`:
   ```yml
   base_url: https://your-auth-proxy.herokuapp.com
   auth_endpoint: /auth
   ```

### Features

- Write posts in English and Bangla
- Rich Markdown editor
- Upload and manage images
- Auto-commits to your GitHub repository
- Publish/unpublish posts

## Notes

- Theme is included as a Git submodule at `themes/hugo-theme-stack`.
- If cloning this repository, initialize submodules:

```bash
git submodule update --init --recursive
```