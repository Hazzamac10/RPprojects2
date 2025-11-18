# Quick IONOS Email Setup Guide

Since your DNS is managed by IONOS, here's the fastest way to set up email for your contact form.

## Recommended: Email Forwarding (FREE)

This is the easiest and free option. It forwards emails from `info@rpprojects.co.uk` to your personal email.

### Steps:

1. **Log into IONOS**
   - Go to [https://www.ionos.co.uk/](https://www.ionos.co.uk/)
   - Log into your account

2. **Set Up Email Forwarding**
   - Navigate to: **Domains & SSL** → Click on `rpprojects.co.uk`
   - Look for **Email** section or **Email Forwarding**
   - Click **Create Email Forwarding** or **Add Forwarding**
   - **Email address:** `info@rpprojects.co.uk`
   - **Forward to:** Your personal email address (e.g., `yourname@gmail.com`)
   - Click **Save**

3. **Wait for DNS Propagation**
   - Usually takes 5-15 minutes
   - Test by sending an email to `info@rpprojects.co.uk` from another account
   - Check your personal inbox

4. **Set Up EmailJS**
   - Sign up at [https://www.emailjs.com/](https://www.emailjs.com/)
   - Add Email Service → Choose **Gmail** (or your personal email provider)
   - Connect your personal email account
   - Create email template (see main guide)
   - Update `script.js` with your EmailJS credentials

**Done!** Form submissions will be sent to your personal email via EmailJS, and any direct emails to `info@rpprojects.co.uk` will be forwarded there too.

---

## Alternative: Professional Email Account (~£1/month)

If you want a full email account with webmail access:

1. **Log into IONOS**
   - Go to **Domains & SSL** → `rpprojects.co.uk` → **Email** → **Email Accounts**

2. **Create Email Account**
   - Click **Create Email Account**
   - **Email:** `info@rpprojects.co.uk`
   - **Password:** Create a strong password
   - Click **Create**

3. **Access Your Email**
   - Webmail: [https://webmail.ionos.co.uk/](https://webmail.ionos.co.uk/)
   - Login with: `info@rpprojects.co.uk` and your password

4. **Set Up EmailJS with IONOS SMTP**
   - In EmailJS, add **Custom SMTP** service:
     - **SMTP Server:** `smtp.ionos.co.uk`
     - **Port:** `465` (SSL) or `587` (TLS)
     - **Username:** `info@rpprojects.co.uk`
     - **Password:** Your IONOS email password
     - **Security:** SSL/TLS
   - Create email template
   - Update `script.js` with your EmailJS credentials

---

## IONOS Email Settings Reference

**For Email Clients (Outlook, Apple Mail, etc.):**
- **IMAP Incoming:** `imap.ionos.co.uk` (Port 993, SSL)
- **POP3 Incoming:** `pop3.ionos.co.uk` (Port 995, SSL)
- **SMTP Outgoing:** `smtp.ionos.co.uk` (Port 465 SSL or 587 TLS)
- **Username:** `info@rpprojects.co.uk`
- **Password:** Your email password

**Webmail Access:**
- URL: [https://webmail.ionos.co.uk/](https://webmail.ionos.co.uk/)

---

## Need Help?

- **IONOS Support:** [https://www.ionos.co.uk/help/](https://www.ionos.co.uk/help/)
- **IONOS Email Guide:** Check IONOS help center for detailed email setup instructions

