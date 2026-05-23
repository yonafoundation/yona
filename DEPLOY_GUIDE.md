# 🚀 YONA Foundation Website – GitHub Pages Deployment Guide

## Your Website Files
- `index.html` – Home page
- `about.html` – About Us
- `programs.html` – Programs & Services
- `gethelp.html` – Get Help / Resources
- `donate.html` – Donate
- `events.html` – Events
- `blog.html` – Blog / News
- `contact.html` – Contact Us
- `styles.css` – All styling
- `main.js` – Navigation & animations

---

## Step-by-Step: Deploy to GitHub Pages (FREE)

### Step 1 – Create a GitHub Account
Go to https://github.com and sign up (free).

### Step 2 – Create a New Repository
1. Click the **"+"** icon → **New repository**
2. Name it: `yona-foundation` (or `yonafoundation.github.io` for a cleaner URL)
3. Set it to **Public**
4. Click **Create repository**

### Step 3 – Upload Your Files
**Option A – Upload via Browser (easiest):**
1. Open your new repository
2. Click **"Add file"** → **"Upload files"**
3. Drag and drop ALL your website files (index.html, about.html, programs.html, gethelp.html, donate.html, events.html, blog.html, contact.html, styles.css, main.js)
4. Scroll down and click **"Commit changes"**

**Option B – Use Git (if you have it installed):**
```bash
git init
git add .
git commit -m "Initial YONA Foundation website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/yona-foundation.git
git push -u origin main
```

### Step 4 – Enable GitHub Pages
1. In your repository, click **"Settings"** (top tab)
2. Scroll down to **"Pages"** in the left sidebar
3. Under **"Source"**, select **"Deploy from a branch"**
4. Under **"Branch"**, select **main** and folder **/ (root)**
5. Click **Save**

### Step 5 – Your Website is Live! 🎉
After 1–2 minutes, your site will be live at:
```
https://YOUR_USERNAME.github.io/yona-foundation/
```
(or `https://YOUR_USERNAME.github.io` if you named the repo `YOUR_USERNAME.github.io`)

---

## Custom Domain (Optional)
If you have a domain like `yonafoundation.org`:
1. In **Settings → Pages**, enter your domain under **"Custom domain"**
2. In your domain registrar (GoDaddy, Namecheap, etc.), add a CNAME record pointing to `YOUR_USERNAME.github.io`

---

## Updating Your Website
To update content later:
1. Go to your GitHub repository
2. Click the file you want to edit
3. Click the pencil ✏️ icon to edit
4. Make changes and click **"Commit changes"**
5. Your site updates automatically within 1–2 minutes

---

## Next Steps (Recommended)
- [ ] Replace placeholder contact info with your real details
- [ ] Add your real logo image file and update HTML to use `<img src="logo.png">`
- [ ] Integrate a real payment processor for donations (Stripe, PayPal, or use a free service like GiveLively.org)
- [ ] Connect a Google Form for the contact form
- [ ] Add Google Analytics to track visitors

---

*Built with ❤️ for YONA Foundation – You Are Not Alone*
