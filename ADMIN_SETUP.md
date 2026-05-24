# YONA Foundation — Admin CMS Setup Guide

## What Was Built

A **no-backend CMS** powered by Google Drive:

- `admin.html` — Password-protected admin panel (you control everything here)
- `drive.js` — Connects admin & public pages to Google Drive
- All public pages now load content **live from Google Drive**

---

## What Admin Can Control

| Section | What You Can Change |
|---|---|
| **Hero & Tagline** | Eyebrow text, main title, description, CTA button text |
| **Stats** | 100+ Meals, 10+ Families, 25+ Volunteers (edit any number/label) |
| **Quotes & Testimonials** | Add, hide, delete community quotes shown on homepage |
| **Events** | Add/edit/remove events with dates, locations, badges, links |
| **Announcements** | Site-wide notices shown on the blog page |
| **Blog Posts** | Write posts with rich text, tags, featured flag, publish/draft toggle |
| **Blog Images** | Upload multiple images per post → stored in named Drive folder |

---

## One-Time Google Drive Setup (15 minutes)

### Step 1 — Google Cloud Project

1. Go to **https://console.cloud.google.com**
2. Click **New Project** → Name it `YONA CMS` → Create
3. In the left menu: **APIs & Services → Library**
4. Search **"Google Drive API"** → Enable it

### Step 2 — API Key (for public reads)

1. **APIs & Services → Credentials → Create Credentials → API Key**
2. Copy the key
3. Click **Edit Key** → Under "API restrictions" select `Google Drive API` → Save

### Step 3 — OAuth Client ID (for admin uploads & saves)

1. **APIs & Services → Credentials → Create Credentials → OAuth 2.0 Client ID**
2. If prompted, configure OAuth consent screen:
   - User type: **External**
   - App name: `YONA Admin`
   - Support email: `supportyona@gmail.com`
   - Add scope: `Google Drive API → .../auth/drive.file`
   - Add your Gmail as a **Test User**
3. Back to Create OAuth Client ID:
   - Application type: **Web application**
   - Name: `YONA Admin`
   - Authorised JavaScript origins: Add your site URL
     - For local testing: `http://localhost` or `file://`
     - For live site: `https://yourdomain.com`
4. Copy the **Client ID**

### Step 4 — Configure Admin Panel

1. Open `admin.html` in your browser
2. Log in (default password: `yona2026admin`)
3. Go to **Settings & Setup**
4. Paste your **API Key** and **Client ID**
5. Click **Save Config**
6. Click **Connect Google Drive** → sign in with `supportyona@gmail.com`
7. Click **Create Content File** — this creates `yona-content.json` in your Drive
8. Done! ✅

### Step 5 — Change Admin Password

In **Settings → Change Admin Password**, set a strong password.
> Note: Password is stored in your browser's localStorage. Use the same browser to access admin.

---

## Daily Usage

### Publishing a Blog Post

1. Go to `admin.html` → **New Post**
2. Write title, tag, summary, full body
3. Enter a **folder name** (e.g. `food-drive-may-2026`)
4. Drop images into the upload zone → they upload to Drive in that folder
5. Toggle **Visible** on, click **Save & Publish**
6. The post appears live on `blog.html` instantly

### Editing Hero / Stats / Quotes

1. Go to the relevant section in admin
2. Make changes
3. Click **Save** — changes go live on the site immediately

### Adding an Event

1. Go to **Events** in admin
2. Fill in title, badge, date, location, description
3. Click **Add Event**
4. Toggle visibility on/off anytime

---

## How It Works (Technical)

```
Admin Panel (admin.html)
    │
    ▼ writes JSON
Google Drive (yona-content.json)   ←→   Drive folders (blog images)
    │
    ▼ reads on page load
Public Site (index.html, blog.html, events.html...)
```

- **Content** = one JSON file in Drive (`yona-content.json`), publicly readable
- **Images** = uploaded to Drive folders named after the post, publicly readable
- **No server, no database, no hosting fees** beyond your site host
- Works on GitHub Pages, Netlify, any static host

---

## Fallback (Before Drive Setup)

Until Google Drive is configured, the admin panel saves content to **browser localStorage**.
Changes will show in that browser only and won't affect the live site.
Once Drive is set up, click **Reload from Drive** to sync.

---

## File Structure

```
yona-foundation/
├── index.html          ← Homepage (loads from Drive)
├── blog.html           ← Blog page (loads from Drive)
├── events.html         ← Events (loads from Drive)
├── about.html
├── contact.html
├── donate.html
├── gethelp.html
├── programs.html
├── admin.html          ← 🔒 Admin CMS (password protected)
├── drive.js            ← Google Drive integration module
├── main.js             ← Scroll/nav animations
├── styles.css          ← All styles
├── logo-full.png       ← YONA logo with text
└── logo-icon.png       ← YONA icon only
```

---

## Security Notes

- `admin.html` has no server-side auth — **do not share the URL publicly**
- The admin password is stored in localStorage — use a private/dedicated device
- For stronger security: rename `admin.html` to something unguessable (e.g. `panel-xk39.html`)
- The content JSON file is publicly readable (needed for the site) but only writable by your Google account
- Images uploaded via admin are publicly viewable (required for the site to show them)

---

*Built for YONA Foundation — You Are Not Alone*
*Guntur, Andhra Pradesh — supportyona@gmail.com*
