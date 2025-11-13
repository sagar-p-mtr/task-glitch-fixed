# Deployment Guide - TaskGlitch App

This guide will help you deploy the TaskGlitch application to Vercel or Netlify.

---

## Prerequisites

- GitHub account
- Vercel or Netlify account (free tier works fine)
- Git installed on your machine

---

## Step 1: Push to GitHub

1. **Initialize Git (if not already done):**
   ```bash
   cd "c:\Assignments by companies\task-glitch-main"
   git init
   ```

2. **Add all files:**
   ```bash
   git add .
   ```

3. **Commit your changes:**
   ```bash
   git commit -m "Fixed all 5 bugs: double fetch, undo snackbar, unstable sorting, double dialog, ROI errors"
   ```

4. **Create a new repository on GitHub:**
   - Go to https://github.com/new
   - Name it `task-glitch-fixed`
   - Don't initialize with README (we already have files)

5. **Push to GitHub:**
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/task-glitch-fixed.git
   git branch -M main
   git push -u origin main
   ```

---

## Option A: Deploy to Vercel (Recommended)

### Step 1: Sign up / Log in to Vercel
Go to https://vercel.com and sign in with GitHub

### Step 2: Import Project
1. Click "Add New..." → "Project"
2. Select your GitHub repository (`task-glitch-fixed`)
3. Click "Import"

### Step 3: Configure Build Settings
Vercel should auto-detect the settings, but verify:
- **Framework Preset:** Vite
- **Build Command:** `npm run build`
- **Output Directory:** `dist`
- **Install Command:** `npm install`

### Step 4: Deploy
1. Click "Deploy"
2. Wait 1-2 minutes for deployment to complete
3. You'll get a URL like: `https://task-glitch-fixed.vercel.app`

### Step 5: Test Your Deployment
1. Open the URL in your browser
2. Verify all features work:
   - ✅ Add, edit, delete tasks
   - ✅ Undo delete works correctly
   - ✅ No double dialogs
   - ✅ ROI calculations are correct
   - ✅ Sorting is stable (no flickering)
   - ✅ No console errors

---

## Option B: Deploy to Netlify

### Step 1: Sign up / Log in to Netlify
Go to https://netlify.com and sign in with GitHub

### Step 2: Import Project
1. Click "Add new site" → "Import an existing project"
2. Choose "Deploy with GitHub"
3. Select your repository (`task-glitch-fixed`)

### Step 3: Configure Build Settings
- **Build command:** `npm run build`
- **Publish directory:** `dist`
- **Base directory:** (leave empty)

### Step 4: Deploy
1. Click "Deploy site"
2. Wait 1-2 minutes for deployment to complete
3. You'll get a URL like: `https://task-glitch-fixed.netlify.app`

### Step 5: Customize Domain (Optional)
1. Go to Site settings → Domain management
2. Click "Options" → "Edit site name"
3. Change to a custom name like `yourname-taskglitch`

### Step 6: Test Your Deployment
Same as Vercel - test all features to ensure everything works!

---

## Option C: Deploy to GitHub Pages

### Step 1: Update `vite.config.ts`
Add base path for GitHub Pages:
```typescript
export default defineConfig({
  base: '/task-glitch-fixed/',  // Your repo name
  plugins: [react()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src'),
    },
  },
});
```

### Step 2: Install gh-pages
```bash
npm install --save-dev gh-pages
```

### Step 3: Add Deploy Script to `package.json`
```json
"scripts": {
  "dev": "vite",
  "build": "tsc -b && vite build",
  "preview": "vite preview",
  "deploy": "npm run build && gh-pages -d dist"
}
```

### Step 4: Deploy
```bash
npm run deploy
```

### Step 5: Enable GitHub Pages
1. Go to your GitHub repository
2. Settings → Pages
3. Source: Deploy from a branch
4. Branch: `gh-pages` / `root`
5. Save

Your site will be live at: `https://YOUR_USERNAME.github.io/task-glitch-fixed/`

---

## Troubleshooting

### Build Fails
- Make sure all dependencies are installed: `npm install`
- Check for TypeScript errors: `npm run build`
- Verify Node.js version (should be 18+): `node --version`

### App Not Loading
- Check browser console for errors
- Verify the base path in `vite.config.ts` matches your deployment
- Clear browser cache and reload

### Features Not Working
- Check if `public/tasks.json` is being served correctly
- Verify environment variables if you added any
- Check network tab for failed API calls

---

## Post-Deployment Checklist

✅ Application loads without errors  
✅ Tasks can be added, edited, and deleted  
✅ Undo snackbar works correctly (closes properly)  
✅ No double dialogs when clicking Edit/Delete  
✅ ROI values display correctly (no NaN/Infinity)  
✅ Sorting is stable (no random reordering)  
✅ Search and filters work  
✅ CSV export/import works  
✅ Metrics and charts display correctly  
✅ Responsive design works on mobile  

---

## Final Submission

When submitting your assignment, provide:

1. **GitHub Repository URL:**
   ```
   https://github.com/YOUR_USERNAME/task-glitch-fixed
   ```

2. **Live Deployment URL:**
   ```
   https://your-app.vercel.app  (or netlify.app)
   ```

3. **Brief Description:**
   ```
   All 5 bugs have been fixed:
   1. ✅ Double fetch issue - Removed duplicate useEffect and StrictMode
   2. ✅ Undo snackbar bug - Implemented clearLastDeleted on close
   3. ✅ Unstable sorting - Added stable alphabetical tie-breaker
   4. ✅ Double dialog opening - Added event.stopPropagation()
   5. ✅ ROI calculation errors - Added validation for division by zero
   
   The app is fully functional and deployed successfully.
   ```

---

## Quick Deploy Commands

**For Vercel CLI (alternative method):**
```bash
npm install -g vercel
vercel login
vercel --prod
```

**For Netlify CLI (alternative method):**
```bash
npm install -g netlify-cli
netlify login
netlify deploy --prod
```

---

**Good luck with your deployment! 🚀**
