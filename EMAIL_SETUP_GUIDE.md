# Email Setup Guide for RP PROJECTS Website

Your website is now configured to use **EmailJS** to receive contact form submissions. Follow these steps to complete the setup:

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Sign up for a free account (free tier includes 200 emails/month)
3. Verify your email address

## Step 2: Set Up Email Service

1. In EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider:

   **If using IONOS Email Forwarding (Option A):**
   - Choose **Gmail**, **Outlook**, or **Yahoo** (your personal email)
   - Follow the setup instructions for your chosen provider
   
   **If using IONOS Professional Email (Option B):**
   - Choose **Custom SMTP**
   - Enter these settings:
     - **Service Name:** IONOS Email
     - **SMTP Server:** `smtp.ionos.co.uk`
     - **Port:** `465` (SSL) or `587` (TLS)
     - **Username:** `info@rpprojects.co.uk`
     - **Password:** Your IONOS email password
     - **Security:** SSL/TLS
   
   **If using other providers:**
   - **Gmail** (recommended for personal use)
   - **Outlook** 
   - **Yahoo**
   - **Custom SMTP** (for other email servers)

4. Follow the setup instructions for your chosen provider
5. **Note your Service ID** (e.g., `service_abc123`)

## Step 3: Create Email Template

1. Go to **Email Templates** in EmailJS dashboard
2. Click **Create New Template**
3. Use this template:

```
Subject: New Contact Form Submission from {{name}}

From: {{email}}
Phone: {{phone}}
Project Type: {{project-type}}

Message:
{{message}}

---
This email was sent from the RP PROJECTS contact form.
```

4. **Note your Template ID** (e.g., `template_xyz789`)

## Step 4: Get Your Public Key

1. Go to **Account** → **General** in EmailJS dashboard
2. Find your **Public Key** (e.g., `abcdefghijklmnop`)

## Step 5: Update Your Website Code

Open `script.js` and replace these placeholders:

1. Find line 2976: Replace `'YOUR_PUBLIC_KEY'` with your actual Public Key
2. Find line 2989: Replace `'YOUR_SERVICE_ID'` with your Service ID
3. Find line 2990: Replace `'YOUR_TEMPLATE_ID'` with your Template ID
4. Find line 2992: Replace `'YOUR_PUBLIC_KEY'` with your Public Key again

**Example:**
```javascript
emailjs.init('abcdefghijklmnop'); // Your Public Key

// In the sendForm call:
const result = await emailjs.sendForm(
    'service_abc123',    // Your Service ID
    'template_xyz789',   // Your Template ID
    form,
    'abcdefghijklmnop'   // Your Public Key
);
```

## Step 6: Test Your Form

1. Commit and push your changes to GitHub
2. Visit your website: `https://rpprojects.co.uk`
3. Fill out the contact form and submit
4. Check your email inbox for the form submission

## Setting Up Email with IONOS (Recommended for Your Setup)

Since your DNS is managed by IONOS, here are the best options:

### Option A: IONOS Email Forwarding (FREE - Easiest)

This forwards emails from `info@rpprojects.co.uk` to your personal email:

1. **Log into IONOS Control Panel**
   - Go to [https://www.ionos.co.uk/](https://www.ionos.co.uk/)
   - Log into your account

2. **Navigate to Email Settings**
   - Go to **Domains & SSL** → Select `rpprojects.co.uk`
   - Click on **Email** or **Email Forwarding**

3. **Create Email Forwarding**
   - Click **Create Email Forwarding** or **Add Forwarding**
   - **Email address:** `info@rpprojects.co.uk`
   - **Forward to:** Your personal email (e.g., `yourname@gmail.com`)
   - Click **Save** or **Create**

4. **Verify Setup**
   - Wait 5-15 minutes for DNS propagation
   - Send a test email to `info@rpprojects.co.uk` from another email account
   - Check your personal inbox - you should receive it

5. **Configure EmailJS**
   - In EmailJS, set up your email service using your **personal email** (the one you forwarded to)
   - When form submissions arrive, they'll be forwarded to your personal inbox
   - The sender will see `info@rpprojects.co.uk` as the recipient

**Note:** Email forwarding is usually free with IONOS domain hosting.

### Option B: IONOS Professional Email Account (~£1/month)

Create a full email mailbox at `info@rpprojects.co.uk`:

1. **Log into IONOS Control Panel**
   - Go to **Domains & SSL** → Select `rpprojects.co.uk`
   - Click on **Email** → **Email Accounts**

2. **Create Email Account**
   - Click **Create Email Account** or **Add Mailbox**
   - **Email address:** `info@rpprojects.co.uk`
   - **Password:** Create a strong password
   - Choose storage size (usually 2GB included)
   - Click **Create**

3. **Access Your Email**
   - IONOS provides webmail access at: `https://webmail.ionos.co.uk/`
   - Or configure email client (Outlook, Apple Mail, etc.) with:
     - **Incoming:** `imap.ionos.co.uk` (port 993 SSL) or `pop3.ionos.co.uk` (port 995 SSL)
     - **Outgoing:** `smtp.ionos.co.uk` (port 465 SSL)
     - **Username:** `info@rpprojects.co.uk`
     - **Password:** Your email password

4. **Configure EmailJS**
   - In EmailJS, choose **Custom SMTP** service
   - Use these SMTP settings:
     - **SMTP Server:** `smtp.ionos.co.uk`
     - **Port:** `465` (SSL) or `587` (TLS)
     - **Username:** `info@rpprojects.co.uk`
     - **Password:** Your email password
     - **Security:** SSL/TLS

**Benefits:** Full email account with webmail access, better for professional use.

### Option C: Other Email Services

If you prefer third-party services:

1. **Google Workspace** (~$6/month per user)
   - Set up `info@rpprojects.co.uk` as a Google Workspace email
   - Use this email in EmailJS

2. **Microsoft 365** (~$5/month per user)
   - Set up `info@rpprojects.co.uk` as an Outlook email
   - Use this email in EmailJS

3. **Zoho Mail** (Free tier available)
   - Set up `info@rpprojects.co.uk` as a Zoho email
   - Use this email in EmailJS

## Troubleshooting

### Form not sending emails?
- Check browser console (F12) for error messages
- Verify all three IDs (Service ID, Template ID, Public Key) are correct
- Make sure EmailJS service is connected and verified
- Check EmailJS dashboard → **Statistics** to see if emails are being sent

### Emails going to spam?
- Add your domain to EmailJS allowed domains
- Consider using a professional email service (Option B above)
- Ask recipients to mark emails as "Not Spam"

### Need more than 200 emails/month?
- EmailJS paid plans start at $15/month for 1,000 emails
- Or use FormSubmit (free, unlimited) - see below

## Alternative: FormSubmit (Simpler, but less control)

If you prefer a simpler solution, you can use FormSubmit instead:

1. Update `index.html` line 245 to:
```html
<form class="contact-form reveal slide-left delay-2" action="https://formsubmit.co/info@rpprojects.co.uk" method="POST">
```

2. Add these hidden fields before the form fields:
```html
<input type="hidden" name="_subject" value="New enquiry from RP PROJECTS website">
<input type="hidden" name="_captcha" value="false">
<input type="hidden" name="_template" value="table">
<input type="hidden" name="_next" value="https://rpprojects.co.uk#contact">
```

3. Remove the EmailJS script and form handler from `script.js`

**Note:** FormSubmit requires you to verify your email address the first time someone submits the form.

---

## Quick Reference

- **EmailJS Dashboard:** https://dashboard.emailjs.com/
- **Documentation:** https://www.emailjs.com/docs/
- **Support:** support@emailjs.com

Your contact form is now ready to receive emails! 🎉

