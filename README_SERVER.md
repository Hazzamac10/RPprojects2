# Quick Start - Deploy Your Server

## 🚀 Easiest Method: Railway (5 minutes)

### Step 1: Push to GitHub
```bash
git add .
git commit -m "Add contact form server"
git push
```

### Step 2: Deploy on Railway
1. Go to [https://railway.app/](https://railway.app/)
2. Sign up with GitHub
3. Click "New Project" → "Deploy from GitHub repo"
4. Select `RPprojects2` repository
5. Railway auto-detects Node.js and deploys!

### Step 3: Add Environment Variables
In Railway dashboard → Variables tab, add:
- `EMAIL_USER` = `hhmccarthy26@outlook.com`
- `EMAIL_PASS` = Your Outlook app password (see guide)

### Step 4: Get Your Server URL
Railway gives you a URL like: `https://your-project.railway.app`
Copy this URL!

### Step 5: Update Website
Open `script.js` line 2973, replace:
```javascript
const SERVER_URL = 'YOUR_SERVER_URL_HERE/api/contact';
```
With:
```javascript
const SERVER_URL = 'https://your-project.railway.app/api/contact';
```

Then push again:
```bash
git add script.js
git commit -m "Update server URL"
git push
```

**Done!** Your form now uses your own server! 🎉

---

## 📧 Get Outlook App Password

1. Go to [https://account.microsoft.com/security](https://account.microsoft.com/security)
2. Enable "Two-step verification" (if not already)
3. Go to "App passwords"
4. Create new app password named "RP PROJECTS Server"
5. Copy the password (use in `EMAIL_PASS`)

---

See `SERVER_SETUP_GUIDE.md` for detailed instructions!

