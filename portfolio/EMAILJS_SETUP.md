# EmailJS Setup Guide

This guide will help you set up EmailJS to receive email notifications when someone contacts you through your portfolio website.

## What is EmailJS?

EmailJS is a service that allows you to send emails directly from JavaScript without requiring a backend server. It's perfect for static websites like your portfolio.

## Step-by-Step Setup

### 1. Create EmailJS Account

1. Go to [EmailJS.com](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

### 2. Add Email Service

1. Log in to your EmailJS dashboard
2. Go to "Email Services" tab
3. Click "Add New Service"
4. Choose "Gmail" (or your preferred email provider)
5. Connect your email account (susheelsharma309@gmail.com)
6. Note down the **Service ID** (you'll need this later)

### 3. Create Email Template

1. Go to "Email Templates" tab
2. Click "Create New Template"
3. Use this template:

**Template Name:** Portfolio Contact Form

**Subject:** New Contact Message from Portfolio - {{subject}}

**HTML Content:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>New Contact Message</title>
</head>
<body style="font-family: Arial, sans-serif; line-height: 1.6; color: #333;">
    <div style="max-width: 600px; margin: 0 auto; padding: 20px;">
        <h2 style="color: #2563eb;">New Contact Message from Portfolio</h2>
        
        <div style="background: #f8fafc; padding: 20px; border-radius: 8px; margin: 20px 0;">
            <h3 style="margin-top: 0; color: #1e293b;">Contact Details:</h3>
            <p><strong>Name:</strong> {{from_name}}</p>
            <p><strong>Email:</strong> {{from_email}}</p>
            <p><strong>Subject:</strong> {{subject}}</p>
        </div>
        
        <div style="background: #f8fafc; padding: 20px; border-radius: 8px; margin: 20px 0;">
            <h3 style="margin-top: 0; color: #1e293b;">Message:</h3>
            <p style="white-space: pre-wrap;">{{message}}</p>
        </div>
        
        <div style="margin-top: 30px; padding-top: 20px; border-top: 1px solid #e2e8f0;">
            <p style="color: #64748b; font-size: 14px;">
                This message was sent from your portfolio contact form at {{to_email}}
            </p>
        </div>
    </div>
</body>
</html>
```

4. Save the template and note down the **Template ID**

### 4. Get Your Public Key

1. Go to "Account" tab in EmailJS dashboard
2. Find your "Public Key" in the API Keys section
3. Copy the public key

### 5. Update Your Code

Replace the placeholder values in your `script.js` file:

```javascript
// In script.js, replace these values:

// 1. Replace YOUR_PUBLIC_KEY with your actual public key
emailjs.init("YOUR_ACTUAL_PUBLIC_KEY");

// 2. Replace YOUR_SERVICE_ID with your service ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)

// 3. Replace YOUR_TEMPLATE_ID with your template ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
```

### Example of Updated Code:

```javascript
// Initialize EmailJS
(function() {
    emailjs.init("user_abc123def456"); // Your actual public key
})();

// In the email sending function:
emailjs.send('service_xyz789', 'template_contact123', templateParams)
```

## Testing the Setup

1. Open your portfolio website
2. Go to the contact section
3. Fill out the form with test data
4. Submit the form
5. Check your email (susheelsharma309@gmail.com) for the notification

## Troubleshooting

### Common Issues:

1. **"Service not found" error:**
   - Make sure you've created the email service correctly
   - Check that the Service ID is correct

2. **"Template not found" error:**
   - Verify the Template ID is correct
   - Make sure the template is published

3. **"Public key invalid" error:**
   - Check that you're using the correct public key
   - Ensure the public key is from the same account as your service

4. **Emails not being received:**
   - Check your spam folder
   - Verify your email service is properly connected
   - Check EmailJS dashboard for any error logs

## EmailJS Free Plan Limits

- **200 emails per month** (free plan)
- **2 email services**
- **5 email templates**

This should be sufficient for a portfolio website. If you need more, consider upgrading to a paid plan.

## Security Notes

- Your public key is safe to expose in client-side code
- EmailJS handles the security of your email credentials
- Never share your private keys or service credentials

## Alternative Setup (If EmailJS doesn't work)

If you prefer not to use EmailJS, you can also:

1. **Use Formspree** - Another popular form handling service
2. **Use Netlify Forms** - If hosting on Netlify
3. **Use Google Forms** - Create a Google Form and embed it
4. **Use a backend service** - Like Firebase Functions or AWS Lambda

## Support

If you encounter any issues:
1. Check EmailJS documentation: https://www.emailjs.com/docs/
2. Visit EmailJS community forum
3. Contact EmailJS support

---

**Note:** After setting up EmailJS, your contact form will send real email notifications to susheelsharma309@gmail.com whenever someone submits the form on your portfolio website.
