# Server Setup Guide for RP PROJECTS Contact Form

This guide will help you set up your own contact form server. It's easier than you think!

## 🚀 Quick Setup (Choose One Method)

### Option 1: Railway (Easiest - Recommended)

Railway is the easiest platform to deploy Node.js servers. Free tier available!

#### Step 1: Create Railway Account
1. Go to [https://railway.app/](https://railway.app/)
2. Sign up with GitHub (easiest)
3. Click "New Project"

#### Step 2: Deploy Your Server
1. Click "Deploy from GitHub repo"
2. Select your `RPprojects2` repository
3. Railway will detect it's a Node.js project
4. Click "Deploy"

#### Step 3: Set Environment Variables
1. Go to your project → **Variables** tab
2. Add these variables:
   - `EMAIL_USER` = `hhmccarthy26@outlook.com`
   - `EMAIL_PASS` = Your Outlook password (or app password - see below)

#### Step 4: Get Your Server URL
1. Railway will give you a URL like: `https://your-project.railway.app`
2. Copy this URL - you'll need it for your website

#### Step 5: Update Your Website
- I'll update your `index.html` to use your new server URL
- The form will submit to your server instead of FormSubmit

---

### Option 2: Render (Also Easy)

#### Step 1: Create Render Account
1. Go to [https://render.com/](https://render.com/)
2. Sign up with GitHub

#### Step 2: Create Web Service
1. Click "New" → "Web Service"
2. Connect your GitHub repository
3. Settings:
   - **Name:** rpprojects-contact
   - **Environment:** Node
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Plan:** Free

#### Step 3: Set Environment Variables
Add these in the Environment section:
- `EMAIL_USER` = `hhmccarthy26@outlook.com`
- `EMAIL_PASS` = Your Outlook password

#### Step 4: Deploy
1. Click "Create Web Service"
2. Wait for deployment (2-3 minutes)
3. Copy your URL (e.g., `https://rpprojects-contact.onrender.com`)

---

## 📧 Setting Up Outlook Email

### Important: Use App Password (Recommended)

Outlook requires an "App Password" for third-party apps. Here's how to get one:

#### Step 1: Enable Two-Factor Authentication
1. Go to [https://account.microsoft.com/security](https://account.microsoft.com/security)
2. Sign in with `hhmccarthy26@outlook.com`
3. Enable "Two-step verification" if not already enabled

#### Step 2: Create App Password
1. Go to [https://account.microsoft.com/security](https://account.microsoft.com/security)
2. Click "Advanced security options"
3. Under "App passwords", click "Create a new app password"
4. Name it "RP PROJECTS Server"
5. Copy the generated password (you'll only see it once!)
6. Use this password in `EMAIL_PASS` environment variable

**Note:** If you don't want to use 2FA, you can try your regular password, but it may not work due to Outlook security.

---

## 🔧 Local Testing (Optional)

If you want to test the server locally before deploying:

1. **Install Node.js** (if not installed):
   - Download from [https://nodejs.org/](https://nodejs.org/)
   - Install version 18 or higher

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Create `.env` file**:
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and add your email credentials

4. **Run server**:
   ```bash
   npm start
   ```

5. **Test it**:
   - Server runs on `http://localhost:3000`
   - Test the endpoint: `POST http://localhost:3000/api/contact`

---

## 🌐 Updating Your Website

Once your server is deployed, I'll update your website to use it:

1. **Update form action** in `index.html`
2. **Add JavaScript** to handle form submission
3. **Test the form** on your live website

---

## ✅ What You Get

- ✅ **Full control** - Your own server
- ✅ **No third-party dependencies** - No FormSubmit needed
- ✅ **Better email formatting** - Custom HTML emails
- ✅ **Reply-to functionality** - Click reply to respond directly
- ✅ **No activation needed** - Works immediately
- ✅ **Professional** - Looks more professional

---

## 🆘 Troubleshooting

### Server won't start?
- Check Node.js version (needs 18+)
- Check environment variables are set correctly
- Check server logs in Railway/Render dashboard

### Emails not sending?
- Verify `EMAIL_USER` and `EMAIL_PASS` are correct
- Try using an App Password instead of regular password
- Check server logs for error messages
- Make sure Outlook allows "less secure apps" (if not using app password)

### Form not submitting?
- Check server URL is correct
- Check browser console (F12) for errors
- Verify CORS is enabled (already done in code)

---

## 📝 Next Steps

1. Choose Railway or Render
2. Deploy your server
3. Set environment variables
4. Get your server URL
5. Let me know and I'll update your website!

---

**Need help?** Just ask! The setup is easier than it looks. 🚀

