# GitHub Pages Deployment Guide

## 🚨 Fix for 404 Errors

If you're getting 404 errors, follow these steps:

### Step 1: Repository Structure
Ensure your repository has this EXACT structure:
```
DataAnalytics/
├── index.html
├── README.md
├── _sidebar.md  
├── _navbar.md
├── .nojekyll
└── learning/
    ├── 1.introduction.md
    ├── 2.base.md
    ├── 3.data_analytics_lifecycle.md
    ├── 1.practice/
    └── 2.practice/
```

### Step 2: GitHub Pages Settings
1. Go to your repository on GitHub
2. Click **Settings** tab
3. Scroll to **Pages** section
4. Select **Source**: "Deploy from a branch"
5. Choose **Branch**: `main` 
6. Choose **Folder**: `/ (root)` 
7. Click **Save**

### Step 3: Upload Files
Upload ALL files from your `C:\Users\mkgaj\OneDrive\Desktop\DataAnalytics\root\` folder to the **root** of your GitHub repository.

### Step 4: Wait and Test
- GitHub Pages can take 5-10 minutes to deploy
- Your site will be available at: `https://gajjarkav.github.io/DataAnalytics`

## ✅ Verification Checklist

- [ ] `index.html` is in repository root
- [ ] `learning` folder is in repository root  
- [ ] `.nojekyll` file exists in root
- [ ] Repository is public
- [ ] GitHub Pages is enabled in settings

## 🐛 Common Issues

**404 on homepage**: 
- Make sure `README.md` exists in root
- Check GitHub Pages settings

**404 on content pages**:
- Ensure `learning/` folder is in the same directory as `index.html`
- Check file paths in `_sidebar.md`

**Site not loading**:
- Wait 10 minutes after pushing changes
- Check repository is public
- Verify GitHub Pages is enabled
