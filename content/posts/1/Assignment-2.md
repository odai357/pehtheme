---
publishDate: 2025-05-20T00:40:04-07:00
title: Assignment 2
---

# Static Personal Blog Website Documentation

**Student Name**: ODAI OTHMAN 

**Student ID**: LS2425241

**Submission Date**: May 20. 2025

**Website URL:**    https://odai357.github.io/pehtheme/  
**Repository:**    https://github.com/odai357/pehtheme



## Table of Contents
1. [Project Overview](#project-overview)
2. [Environment Setup](#environment-setup)
3. [Website Development Process](#website-development-process)
4. [Git Version Control](#git-version-control)
5. [Deployment Process](#deployment-process)
6. [Integration with Assignment 1](#integration-with-assignment-1)
7. [Challenges and Solutions](#challenges-and-solutions)
8. [Conclusion](#conclusion)

---

## 1. Project Overview

For this assignment, I created a static personal blog website using Hugo, a fast and flexible static site generator. I chose the Hugo Profile theme for its modern design and professional appearance that aligns with my goal of showcasing my work as a web developer.

### Why Hugo?
- **Speed**: Hugo is one of the fastest static site generators
- **Flexibility**: Easy to customize themes and content
- **GitHub Pages Integration**: Seamless deployment workflow
- **Markdown Support**: Natural integration with assignment requirements

---

## 2. Environment Setup

### Prerequisites Installation

1. **Install Hugo** :
```bash
# For Windows (using Chocolatey)
choco install hugo-extended

2. **Verify Installation**:
```bash
hugo version
# Output: hugo v0.XX.X extended
```

3. **Install Git**:
```bash
# Verify git installation
git --version
```

---

## 3. Website Development Process

### Step 1: Create New Hugo Site

```bash
# Create new Hugo site
hugo new site pehtheme
cd pehtheme
```

### Step 2: Install Hugo Profile Theme

```bash
# Initialize git repository
git init

# Add theme as submodule
git submodule add https://github.com/gurusabarish/hugo-profile.git themes/hugo-profile
```

### Step 3: Configure the Website

1. **Copy example configuration**:
```bash
cp themes/hugo-profile/exampleSite/config.toml ./config.toml
```

2. **Customize config.toml**:
```toml
baseURL = "https://odai357.github.io/pehtheme/"
languageCode = "en-us"
title = "Odai-泽鑫"
theme = "hugo-profile"

[params]
  title = "Odai-泽鑫"
  description = "I build things for the web"
  favicon = "/favicon.ico"
  
  # Hero section
  [params.hero]
    enable = true
    intro = "Hi, my name is"
    title = "Odai-泽鑫"
    subtitle = "I build things for the web"
    content = "A passionate web app developer. I tend to make use of modern web technologies to build websites that look great, feel fantastic, and function correctly."
    image = "/images/profile.jpg"
```

### Step 4: Create Content Structure

```bash
# Create assignment pages
hugo new content/posts/assignments/assignment1.md
hugo new content/posts/assignments/assignment2.md
hugo new content/posts/assignments/assignment3.md
hugo new content/posts/assignments/assignment4.md
```

### Step 5: Customize Homepage

Created custom homepage layout to display only navigation links without blog posts:



### Step 6: Local Development and Testing

```bash
# Run local server
hugo server 

# View at http://localhost:1313
```


---

## 4. Git Version Control

### Meaningful Commits History

| Commit # | Command | Message | Purpose |
|----------|---------|---------|---------|
| 1 | `git add .` <br> `git commit -m "Initial commit: created Hugo site"` | Initial project setup with Hugo structure |
| 2 | `git add themes/ config.toml` <br> `git commit -m "Added Ananke theme and updated config.toml"` | Theme installation and basic configuration |
| 3 | `git add content/assignments/*.md` <br> `git commit -m "Created assignment1-4 Markdown pages"` | Content structure for assignments |
| 4 | `git add layouts/index.html` <br> `git commit -m "Customized homepage layout and _index.md"` | Homepage customization to show only navigation |
| 5 | `git add public/` <br> `git commit -m "Switched publishDir to docs and deployed to GitHub"` | Deployment configuration for GitHub Pages |
| 6 | `git add .gitmodules` <br> `git commit -m "Add .gitmodules file"` | Fixed theme submodule configuration |
| 7 | `git add content/posts/` <br> `git commit -m "setup assignments links"` | Added assignment navigation links |

### Git Commands Used

```bash
# Initialize repository
git init

# Add remote origin
git remote add origin https://github.com/odai357/pehtheme.git

# Create and switch to main branch
git checkout -b main

# Stage and commit changes
git add .
git commit -m "commit message"

# Push to GitHub
git push -u origin main
```
![Alt text](/images/2.jpg )
---

## 5. Deployment Process

### GitHub Pages Configuration

1. **Update config.toml for deployment**:
```toml
publishDir = "docs"
baseURL = "https://odai357.github.io/pehtheme/"
```

2. **Generate static files**:
```bash
hugo 
```

3. **Configure GitHub Pages**:
   - Went to repository Settings → Pages
   - Source: Deploy from branch
   - Branch: main
   - Folder: /docs

4. **GitHub Actions Workflow** (.github/workflows/gh-pages.yml):
```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true
          fetch-depth: 0
      
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true
      
      - name: Build
        run: hugo --minify
      
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

### Deployment URL
The website is successfully deployed at: **https://odai357.github.io/pehtheme/**

---

## 6. Integration with Assignment 1

Successfully integrated Assignment 1 by:

1. **Creating dedicated assignment page**:
```bash
hugo new content/assignments/assignment1.md
```

2. **Adding content with front matter**:
```markdown
---
title: "Assignment 1"
date: 2025-05-10
draft: false
---

# Assignment 1 Report

[Assignment 1 content in Markdown format]
```

3. **Linking from homepage navigation**:
   - Modified menu configuration in config.toml
   - Created custom navigation links pointing to `/posts/assignment-1/`

---

## 7. Challenges and Solutions

### Challenge 1: Theme Not Loading
**Problem**: Theme appeared broken after deployment  
**Solution**: Fixed baseURL in config.toml and ensured publishDir was set correctly

### Challenge 2: Homepage Showing Blog Posts
**Problem**: Default theme showed blog posts on homepage  
**Solution**: Created custom layout in `layouts/index.html` to display only navigation

### Challenge 3: GitHub Actions Failing
**Problem**: Submodule not being fetched correctly  
**Solution**: Added `submodules: true` to checkout action and created .gitmodules file

### Challenge 4: Assignment Links Not Working
**Problem**: Navigation to assignment pages returned 404  
**Solution**: Ensured correct permalink structure and updated menu configuration

---

## 8. Conclusion

This project successfully demonstrates:
- ✅ Static site generation with Hugo
- ✅ Version control with meaningful Git commits
- ✅ Deployment to GitHub Pages with accessible URL
- ✅ Integration of previous assignment work
- ✅ Professional documentation in Markdown

---

**Repository Link**: https://github.com/odai357/pehtheme  
**Live Website**: https://odai357.github.io/pehtheme/