# 🌐 ALEX — Developer Portfolio & "About Me"

<div align="center">

[![Live Webpage](https://img.shields.io/badge/Live%20Website-GitHub%20Pages-brightgreen?style=for-the-badge&logo=github)](https://azr-nix.github.io/about-me/)
[![GitHub Repository](https://img.shields.io/badge/GitHub-about--me-blue?style=for-the-badge&logo=github)](https://github.com/azr-nix/about-me)
[![Tech Stack](https://img.shields.io/badge/Tech-React%20%7C%20Tailwind%20%7C%20Vite-61dafb?style=for-the-badge&logo=react)](https://react.dev)
[![Author](https://img.shields.io/badge/Author-azr--nix-purple?style=for-the-badge)](https://github.com/azr-nix)

Official personal portfolio website for **ALEX** (`azr-nix`) — FiveM, Discord.js & Lua Systems Developer.

</div>

---

## 📑 Table of Contents
- [✨ Overview](#-overview)
- [🚀 Live Deployment & Hosting](#-live-deployment--hosting)
- [🛠️ Tech Stack](#️-tech-stack)
- [📁 Project Structure](#-project-structure)
- [🐛 Issues Audited & Fixes Applied](#-issues-audited--fixes-applied)
  - [1. Asset Path Resolution for GitHub Pages](#1-asset-path-resolution-for-github-pages-fixed)
  - [2. SPA Routing & 404 Fallback](#2-spa-routing--404-fallback-fixed)
  - [3. Jekyll File Filtering](#3-jekyll-file-filtering-fixed)
  - [4. Image File Sizes Advisory](#4-image-file-sizes-advisory-performance-optimization)
- [⚙️ How to Enable GitHub Pages](#️-how-to-enable-github-pages)
- [💻 Push to GitHub](#-push-to-github)
- [📄 License & Credits](#-license--credits)

---

## ✨ Overview

A clean, responsive, dark/light theme portfolio showcasing custom software solutions, FiveM resources, and Discord bots built by **ALEX**.

### Featured Sections:
- **Hero & Identity**: Interactive greeting with dark/light mode toggle.
- **Introduction**: Developer background and philosophy.
- **Featured Projects**:
  - *Eclipsed Soul*: Custom FiveM Roleplay framework and ecosystem.
  - *Queen Mikasa*: Advanced Discord moderation and utility bot.
  - *5M-HUB Store*: Digital marketplace for FiveM scripts and systems.
- **Services & Skills**: Lua scripting, server architecture, Discord bot automation, web development.
- **Tech Stack Grid**: Languages, frameworks, and database tools used.
- **Brand Ecosystem**: Digital store and community platforms.

---

## 🚀 Live Deployment & Hosting

When hosted on GitHub Pages under the `about-me` repository, the website URL will be:

```
https://azr-nix.github.io/about-me/
```

*(If you choose to name the repository `azr-nix.github.io` instead, it will be hosted at the root domain: `https://azr-nix.github.io/`)*.

---

## 🛠️ Tech Stack

- **Frontend Framework**: React 18
- **Styling**: Tailwind CSS, custom design tokens, dark mode toggle
- **Animations**: Framer Motion
- **Icons**: Lucide Icons & FontAwesome
- **Build Tool**: Vite
- **Deployment**: GitHub Pages (via GitHub Actions CI/CD)

---

## 📁 Project Structure

```
dist/
├── .github/
│   └── workflows/
│       └── deploy.yml      # Automated GitHub Pages CI/CD workflow
├── assets/
│   ├── index-*.js          # React bundle (relative asset paths configured)
│   └── index-*.css         # Tailwind & custom CSS styles
├── images/                 # Project banners, avatars, and thumbnails
├── .gitignore              # Ignores OS & IDE cache files
├── .nojekyll               # Disables Jekyll processing on GitHub Pages
├── 404.html                # Single Page App fallback for GitHub Pages
├── favicon.svg             # Site favicon
├── index.html              # Main HTML entrypoint
└── README.md               # Repository documentation
```

---

## 🐛 Issues Audited & Fixes Applied

*(Pre-deployment technical audit for GitHub Pages hosting)*

### 1. Asset Path Resolution for GitHub Pages (FIXED)
- **Problem**: The raw build used absolute root paths (`/assets/index-*.js`, `/favicon.svg`, and `/images/...`). On GitHub Pages project repositories (`https://azr-nix.github.io/about-me/`), browsers request `https://azr-nix.github.io/assets/...`, causing all styles, scripts, and images to fail with **404 Not Found**.
- **Fix Applied**: Updated [`index.html`](index.html) and all 12 image references inside [`assets/index-5AbxMnSz.js`](assets/index-5AbxMnSz.js) to portable relative paths (`./assets/`, `./images/`, `./favicon.svg`). The site now works automatically on any subpath or domain.

### 2. SPA Routing & 404 Fallback (FIXED)
- **Problem**: GitHub Pages does not support `_redirects` files (which are designed for Netlify/Cloudflare). Direct link navigation or page reloads on sub-routes can return GitHub's default 404 page.
- **Fix Applied**: Added [`404.html`](404.html) as an exact duplicate of `index.html` to provide seamless SPA client-side routing on GitHub Pages.

### 3. Jekyll File Filtering (FIXED)
- **Problem**: By default, GitHub Pages processes repositories with Jekyll, which ignores files and directories starting with underscores (e.g. `_redirects`).
- **Fix Applied**: Added [`.nojekyll`](.nojekyll) to the root directory to bypass Jekyll and serve static files directly.

### 4. Image File Sizes Advisory (Performance Optimization)
- **Observation**:
  - `images/saslonch.jpg` is **30.7 MB**
  - `images/autumn_seiser.jpg` is **8.8 MB**
  - `images/5m-hub.png` is **3.1 MB**
- **Impact**: While GitHub allows files up to 100 MB, large 30 MB background images can cause slow load times on mobile devices and cellular connections.
- **Recommendation**: In a future update, consider converting large JPEG/PNG backgrounds to compressed `.webp` format under 500 KB each using Squoosh or TinyPNG.

---

## ⚙️ How to Enable GitHub Pages

Once you have pushed the repository to GitHub:

1. Open your repository on GitHub: **`https://github.com/azr-nix/about-me`**
2. Click on **Settings** (top right tab).
3. On the left sidebar, click **Pages**.
4. Under **Build and deployment**:
   - **Source**: Select **GitHub Actions** *(Recommended - uses `.github/workflows/deploy.yml` automatically)*.
   - *(Alternative)*: Select **Deploy from a branch**, choose branch **`main`**, and folder **`/ (root)`**, then click **Save**.
5. Within 1-2 minutes, your site will be live at:
   👉 **`https://azr-nix.github.io/about-me/`**

---

## 💻 Push to GitHub

Run these commands in PowerShell inside `C:\Users\s7094\Music\alex_web\dist`:

```powershell
# 1. Initialize git inside dist
git init

# 2. Stage all files
git add .

# 3. Create initial commit
git commit -m "feat: initial commit of portfolio ready for GitHub Pages"

# 4. Set branch to main
git branch -M main

# 5. Link to your GitHub repository
git remote add origin https://github.com/azr-nix/about-me.git

# 6. Push to GitHub
git push -u origin main
```

---

## 📄 License & Credits

- Designed and developed by [**ALEX (azr-nix)**](https://github.com/azr-nix).
- Built with React, Tailwind CSS, and Framer Motion.
- All rights reserved.
