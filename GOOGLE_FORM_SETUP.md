# Google Form Setup Guide for Account Deletion

This guide walks you through creating and configuring the Google Form for SwimHub account deletion requests.

## Step 1: Create the Form

1. Go to [Google Forms](https://forms.google.com/)
2. Click **"+ Blank"** to create a new form
3. Click on "Untitled form" at the top and change it to: **SwimHub Account Deletion Request**

## Step 2: Configure Form Settings

1. Click the **Settings** icon (⚙️) at the top right
2. Go to the **"General"** tab:
   - ✅ Check "Limit to 1 response" (prevents spam)
   - ✅ Check "Collect email addresses"
   - Set "Respondent can edit after submit" to **ON** (allows corrections)

3. Go to the **"Presentation"** tab:
   - ✅ Check "Show progress bar"
   - Add confirmation message:
     ```
     Thank you for your submission. Your account deletion request has been received.

     We will process your request within 30 days and send a confirmation email once completed.

     If you have any questions, please contact: sport.hub.development@gmail.com
     ```

4. Go to the **"Responses"** tab:
   - ✅ Check "Collect email addresses"
   - ✅ Check "Get email notifications for new responses"
   - Click "Save"

## Step 3: Add Form Questions

### Question 1: Account Email (Auto-collected)

This is automatically collected when "Collect email addresses" is enabled in settings.

### Question 2: Name

1. Click the **"+"** button to add a question
2. Question type: **Short answer**
3. Question text: `Full Name`
4. Toggle **"Required"** ON
5. Description (optional): `Enter your full name as registered in SwimHub`

### Question 3: Account Confirmation

1. Click the **"+"** button
2. Question type: **Short answer**
3. Question text: `SwimHub Account Email`
4. Toggle **"Required"** ON
5. Description: `Re-enter your SwimHub account email to confirm`
6. Click the three dots (⋮) → **"Response validation"**
   - Add validation: **Text** → **Email**
   - Custom error text: `Please enter a valid email address`

### Question 4: Understanding Consequences

1. Click the **"+"** button
2. Question type: **Checkboxes**
3. Question text: `I understand that:`
4. Add these options (click "Add option" for each):
   - `All my swimming data will be permanently deleted`
   - `All custom training programs I created will be removed`
   - `This action cannot be undone`
   - `I will lose access to my account within 30 days`
5. Toggle **"Required"** ON
6. Click the three dots (⋮) → **"Response validation"**
   - Select **"Select at least"** → **4**
   - Custom error text: `You must acknowledge all consequences before proceeding`

### Question 5: Deletion Reason (Optional)

1. Click the **"+"** button
2. Question type: **Paragraph**
3. Question text: `Reason for deletion (Optional)`
4. Description: `Help us improve by sharing why you're leaving. This is optional.`
5. Leave **"Required"** OFF

### Question 6: Final Confirmation

1. Click the **"+"** button
2. Question type: **Multiple choice**
3. Question text: `Are you sure you want to permanently delete your SwimHub account?`
4. Add these options:
   - `Yes, I want to permanently delete my account`
   - `No, cancel this request`
5. Toggle **"Required"** ON

## Step 4: Customize Form Appearance

1. Click the **palette icon** (🎨) at the top right
2. Choose a theme:
   - **Theme color:** Select purple/blue to match SwimHub branding (#667eea)
   - **Background color:** White or light gray
   - **Font style:** Choose a clean, modern font (e.g., "Basic" or "Modern")

3. Add a header image (optional):
   - Upload a SwimHub logo or banner image
   - Recommended size: 1600 x 400 pixels

## Step 5: Add Form Description

1. Click on the description area below the form title
2. Add this description:

```
This form is for requesting permanent deletion of your SwimHub account and all associated data.

⚠️ IMPORTANT: Account deletion is permanent and cannot be undone.

What will be deleted:
• Your account credentials
• All swimming results and performance history
• Custom training programs you created
• Training completion records
• Profile information and preferences

Processing time: Up to 30 days

If you have questions, contact: sport.hub.development@gmail.com
```

## Step 6: Get Embed Code

### Option A: Get Embed Code (Recommended)

1. Click the **"Send"** button at the top right
2. Click the **`<>` (Embed HTML)** icon
3. Adjust width and height:
   - Width: `100%`
   - Height: `800px`
4. Copy the entire iframe code

**Example embed code:**
```html
<iframe src="https://docs.google.com/forms/d/e/1FAIpQLSc.../viewform?embedded=true"
        width="100%"
        height="800"
        frameborder="0"
        marginheight="0"
        marginwidth="0">
    Loading…
</iframe>
```

### Option B: Get Shareable Link

1. Click the **"Send"** button
2. Click the **link icon** (🔗)
3. ✅ Check "Shorten URL"
4. Copy the link

**Example link:**
```
https://forms.gle/AbCdEfGhIjKlMnOp
```

## Step 7: Update account-deletion.html

Open `account-deletion.html` and make these updates:

### Update 1: Replace Form Embed (Lines 226-235)

Replace the placeholder with your embed code:

```html
<div class="form-embed">
    <iframe src="YOUR_GOOGLE_FORM_EMBED_URL_HERE"
            width="100%"
            height="800"
            frameborder="0"
            marginheight="0"
            marginwidth="0">
        Loading…
    </iframe>
</div>
```

### Update 2: Add Direct Link (Line 243)

Replace the placeholder link:

```html
<a href="YOUR_GOOGLE_FORM_LINK_HERE" target="_blank" rel="noopener noreferrer">
    Open Deletion Request Form →
</a>
```

### Update 3: Update Contact Email (Line 252)

Replace the placeholder email:

```html
<a href="mailto:sport.hub.development@gmail.com">sport.hub.development@gmail.com</a>
```

## Step 8: Set Up Email Notifications

### Create Email Template for Responses

1. Open the form responses spreadsheet:
   - In your form, click **"Responses"** tab
   - Click the **Google Sheets icon** to create a spreadsheet

2. The spreadsheet will contain all form responses

3. Set up email notifications:
   - You should already receive emails for each response (if enabled in settings)
   - Emails will be sent to the Google account that created the form

### Optional: Set Up Auto-Response Email

Google Forms can send an automatic response email to users:

1. In form settings → **"Responses"** tab
2. Check **"Response receipts"**
3. Select **"Always"**

Users will receive a copy of their submission.

## Step 9: Test the Form

Before deploying:

1. Click **"Preview"** (eye icon) at the top
2. Submit a test response
3. Verify:
   - ✅ All required fields work
   - ✅ Validation rules are enforced
   - ✅ Confirmation message appears
   - ✅ You receive email notification
   - ✅ Response appears in spreadsheet (if created)

## Step 10: Deploy to GitHub Pages

1. Navigate to the swimhub-legal repository:
   ```bash
   cd C:\Users\user\Documents\GIT\SportHubDevelopment\swimhub-legal
   ```

2. Commit the changes:
   ```bash
   git add .
   git commit -m "Add account deletion form with Google Forms integration"
   git push origin main
   ```

3. Enable GitHub Pages:
   - Go to repository **Settings** → **Pages**
   - Set **Source** to `main` branch
   - Click **Save**
   - Wait 2-3 minutes for deployment

4. Your URLs will be:
   - Index: `https://[username].github.io/swimhub-legal/`
   - Privacy Policy: `https://[username].github.io/swimhub-legal/privacy-policy.html`
   - Account Deletion: `https://[username].github.io/swimhub-legal/account-deletion.html`

## Step 11: Add to Google Play Console

1. Go to Google Play Console
2. Navigate to your app → **Policy** → **Data safety**
3. Find the "Delete account URL" field
4. Enter your account deletion page URL:
   ```
   https://[username].github.io/swimhub-legal/account-deletion.html
   ```
5. Save changes

## Managing Deletion Requests

When you receive a deletion request via the Google Form:

### 1. Verify Request

- Check that the email addresses match
- Ensure all confirmations are checked
- Review the "Are you sure?" response

### 2. Process Deletion in Supabase

You'll need to delete data from these tables:

```sql
-- Step 1: Get user ID from email
SELECT id FROM auth.users WHERE email = 'user@example.com';

-- Step 2: Delete user data (replace USER_ID with actual ID)
DELETE FROM users_swimming_results WHERE user_id = 'USER_ID';
DELETE FROM training_catalog_completions WHERE user_id = 'USER_ID';
DELETE FROM users_training_tasks WHERE user_id = 'USER_ID';
DELETE FROM users_training_sets WHERE user_id = 'USER_ID';

-- Step 3: Delete authentication account
-- Do this via Supabase Dashboard → Authentication → Users → Delete
```

### 3. Send Confirmation Email

Send an email to the user confirming deletion:

**Subject:** SwimHub Account Deletion Completed

**Body:**
```
Hello,

Your SwimHub account and all associated data have been permanently deleted as requested.

Deleted data includes:
- Account credentials
- Swimming results and performance history
- Custom training programs
- Training completion records
- Profile information

If you did not request this deletion or have any questions, please contact us immediately.

Thank you for using SwimHub.

Best regards,
SwimHub Development Team
sport.hub.development@gmail.com
```

### 4. Track Completion

- Mark the request as completed in your spreadsheet
- Keep records of deletion requests for compliance (minimum 3 years)

## Security Considerations

1. **Verify Identity:** Always verify the email address matches before deleting
2. **Keep Logs:** Maintain logs of deletion requests for compliance
3. **Backup Policy:** Ensure backups are purged within 90 days as stated
4. **Response Time:** Process requests within 30 days per privacy policy

## Troubleshooting

### Form not embedding?

- Check if iframe is allowed on GitHub Pages (it is)
- Verify the embed URL is correct
- Try using the direct link as a fallback

### Not receiving email notifications?

- Check spam folder
- Verify email notifications are enabled in Form Settings
- Check the email address associated with the Google account

### Form looks broken on mobile?

- The form is responsive by default
- Test on actual devices, not just browser dev tools
- Ensure `width="100%"` is set in the iframe

## Additional Resources

- [Google Forms Help Center](https://support.google.com/docs/topic/9055404)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GDPR Compliance Guide](https://gdpr.eu/right-to-be-forgotten/)

---

**Setup Complete!**

Your account deletion page is now ready to deploy and can be submitted to Google Play Console.
