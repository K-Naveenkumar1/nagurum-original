# Google Sheets Form Submission Setup

This guide will help you set up the Google Apps Script to connect your contact form to Google Sheets.

## Prerequisites

1. A Google account
2. A Google Sheet where you want to store form submissions

## Setup Instructions

### 1. Create a New Google Sheet

1. Go to [Google Sheets](https://sheets.google.com)
2. Click on "+" to create a new spreadsheet
3. Name it something like "Nagurum Contact Form Submissions"

### 2. Create a Google Apps Script

1. In your Google Sheet, click on "Extensions" > "Apps Script"
2. Delete any code in the editor and paste the contents of `google-apps-script/form-submission.js`
3. Replace `YOUR_GOOGLE_SHEET_ID` in the script with your actual Google Sheet ID
   - You can find the Sheet ID in the URL: `https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit#gid=0`

### 3. Deploy the Web App

1. In the Apps Script editor, click on "Deploy" > "New deployment"
2. Click the gear icon (⚙️) next to "Select type" and choose "Web app"
3. Fill in the deployment configuration:
   - Description: "Contact Form Handler"
   - Execute as: "Me"
   - Who has access: "Anyone"
4. Click "Deploy"
5. Copy the Web App URL that's provided

### 4. Update the Contact Form

1. Open `contact.html`
2. Find the line that says:
   ```javascript
   const SCRIPT_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL';
   ```
3. Replace `'YOUR_GOOGLE_APPS_SCRIPT_URL'` with the Web App URL you copied, making sure to keep the quotes
   ```javascript
   const SCRIPT_URL = 'https://script.google.com/.../exec';
   ```

### 5. Test the Form

1. Open your website and navigate to the contact page
2. Fill out the form and submit it
3. Check your Google Sheet - you should see a new row with the form data

## Troubleshooting

- If you get a permission error, make sure to:
  1. Run the `setupSheet` function once from the Apps Script editor
  2. Check that the Web App is deployed with "Anyone" access
  3. Make sure you've accepted the permissions when prompted

- If the form submission fails:
  1. Open your browser's developer tools (F12)
  2. Go to the Console tab
  3. Submit the form and check for any error messages
  4. Check the "Network" tab to see the response from the server

## Security Notes

- The Web App URL should be kept private
- Consider adding reCAPTCHA to prevent spam
- Regularly monitor the submissions in your Google Sheet
