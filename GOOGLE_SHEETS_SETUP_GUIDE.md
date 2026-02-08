# 📊 Google Apps Script Setup Guide

This guide will help you set up Google Apps Script as your cloud database for the Labor Wage Tracking System.

## ✨ Features

- **Automatic Sync**: Data syncs automatically when you open/refresh the page
- **Real-time Updates**: Changes sync immediately after add/delete/edit
- **Cloud Storage**: All data stored safely in Google Sheets
- **Free**: Google Apps Script is completely free
- **No API Key Needed**: Much simpler than API setup
- **Easy Access**: View and edit data directly in Google Sheets
- **No Manual Push**: Everything syncs automatically!

## 📋 Prerequisites

- A Google Account (Gmail)
- Internet connection
- Web browser

## 🚀 Step-by-Step Setup (5 Minutes!)

### Step 1: Create a Google Sheet

1. Go to [https://sheets.google.com](https://sheets.google.com)
2. Click **"+ Blank"** to create a new spreadsheet
3. Name it **"Labor Tracking Data"** (or any name you prefer)
4. Keep this tab open - you'll need it!

### Step 2: Open Apps Script Editor

1. In your Google Sheet, click **"Extensions"** menu (top menu bar)
2. Click **"Apps Script"**
3. A new tab will open with the Apps Script editor
4. You'll see some default code - **delete all of it**

### Step 3: Add the Apps Script Code

1. Open the file **`apps-script-code.gs`** from your project folder
2. **Copy ALL the code** from that file (Ctrl+A, Ctrl+C)
3. Go back to the Apps Script editor tab
4. **Paste the code** (Ctrl+V)
5. Click the **"Save"** icon (💾 disk icon) or press Ctrl+S
6. Name your project: **"Labor Tracking API"**
7. Click **"OK"**

### Step 4: Deploy as Web App

1. In the Apps Script editor, click **"Deploy"** button (top right)
2. Click **"New deployment"**
3. Click the **gear icon** ⚙️ next to "Select type"
4. Choose **"Web app"**
5. Fill in the settings:
   - **Description**: "Labor Tracking API"
   - **Execute as**: "Me (your-email@gmail.com)"
   - **Who has access**: "Anyone"
   
   ⚠️ **Don't worry!** "Anyone" means anyone with the URL can use the API, but:
   - Only YOU can see/edit the actual Google Sheet
   - The data is still private and secure
   - The URL acts like a password

6. Click **"Deploy"**

### Step 5: Authorize the Script

1. A popup will appear asking for authorization
2. Click **"Authorize access"**
3. Choose your Google account
4. You'll see a warning: "Google hasn't verified this app"
5. Click **"Advanced"** (bottom left)
6. Click **"Go to Labor Tracking API (unsafe)"**
   
   ⚠️ **This is safe!** It's YOUR script, Google just hasn't verified it because it's personal.

7. Click **"Allow"** to grant permissions
8. The script needs permission to:
   - Read and write to your spreadsheet
   - Connect to external services (your web app)

### Step 6: Copy the Web App URL

1. After authorization, you'll see a success message
2. **Copy the "Web app URL"** - it looks like:
   ```
   https://script.google.com/macros/s/AKfycbx.../exec
   ```
3. Click **"Done"**

**IMPORTANT**: Save this URL somewhere safe! You'll need it in the next step.

### Step 7: Configure the Application

1. Open the file **`google-sheets-config.js`** in a text editor (Notepad, VS Code, etc.)
2. Find this line:
   ```javascript
   webAppUrl: 'YOUR_WEB_APP_URL_HERE',
   ```
3. Replace `'YOUR_WEB_APP_URL_HERE'` with your actual URL:
   ```javascript
   webAppUrl: 'https://script.google.com/macros/s/AKfycbx.../exec',
   ```
4. **Save the file**

### Step 8: Test the Connection

1. Open **`index.html`** in your web browser
2. The page will automatically try to load data from Google Sheets
3. Open browser console (Press F12) and look for:
   - `"Loading data from Google Sheets..."`
   - `"✅ Data loaded from Google Sheets successfully"`

4. Click **"📊 Data Management"** button (top right)
5. In the **"📊 Google Sheets Sync"** section, click **"🔍 Check Status"**
6. You should see: **"✅ Google Sheets connection successful!"**

## 🎉 You're Done!

Your system is now connected to Google Sheets! Everything will sync automatically.

## 🎮 How It Works

### Automatic Sync

The system automatically syncs in these situations:

1. **On Page Load/Refresh** ✅
   - Opens page → Loads latest data from Google Sheets
   - Refreshes page → Loads latest data from Google Sheets

2. **After Adding Record** ✅
   - Add work entry → Automatically syncs to Google Sheets

3. **After Deleting Record** ✅
   - Delete entry → Automatically syncs to Google Sheets

4. **After Adding Work Type** ✅
   - Add new category/task → Automatically syncs to Google Sheets

5. **After Removing Work Type** ✅
   - Remove category/task → Automatically syncs to Google Sheets

### No Manual Action Needed!

Just use the app normally - everything syncs automatically in the background!

## 📊 Viewing Data in Google Sheets

You can open your Google Sheet anytime to view the data:

### Labor Records Sheet

The script automatically creates a sheet named "Labor Records" with:
- Formatted headers (green background, white text)
- All your work records
- Auto-resized columns for easy reading

### Work Types Sheet

The script automatically creates a sheet named "Work Types" with:
- Categories and tasks
- English and Kannada translations
- Formatted headers

## 🔄 Multi-Device Workflow

### Using Multiple Devices

**Device 1 (Morning):**
1. Open the app
2. Data automatically loads from Google Sheets
3. Add new entries
4. Entries automatically sync to Google Sheets

**Device 2 (Afternoon):**
1. Open the app
2. Data automatically loads (includes Device 1's entries!)
3. Add more entries
4. Entries automatically sync to Google Sheets

**Device 1 (Evening):**
1. Refresh the page
2. Data automatically loads (includes Device 2's entries!)
3. All data is synchronized!

## � Updating the Script

If you need to update the Apps Script code later:

1. Go to your Google Sheet
2. Click **"Extensions"** → **"Apps Script"**
3. Make your changes
4. Click **"Save"**
5. Click **"Deploy"** → **"Manage deployments"**
6. Click the **pencil icon** ✏️ to edit
7. Change **"Version"** to **"New version"**
8. Click **"Deploy"**
9. The URL stays the same - no need to update config!

## 🔒 Security & Privacy

### Your Data is Safe

✅ **Private**: Only you can see the Google Sheet
✅ **Secure**: Google's enterprise-level security
✅ **Controlled**: You own and control all data
✅ **Encrypted**: Data encrypted in transit and at rest

### Web App URL

- The URL is like a password - keep it private
- Anyone with the URL can use the API
- But they can't see your Google Sheet directly
- Only you can edit the sheet

### Permissions

The script needs these permissions:
- **Read/Write Spreadsheet**: To store and retrieve data
- **External Service**: To receive requests from your web app

## ❓ Troubleshooting

### "Google Sheets is not configured"
- Check that you've edited `google-sheets-config.js`
- Make sure you pasted the complete Web App URL
- The URL should start with `https://script.google.com/macros/s/`
- Refresh the page after saving changes

### "Cannot connect to Google Sheets"
- Check your internet connection
- Verify the Web App URL is correct
- Make sure you deployed the script (Step 4)
- Try redeploying: Deploy → Manage deployments → Edit → New version

### "Authorization required"
- You need to authorize the script (Step 5)
- Go to Apps Script editor
- Click Deploy → Manage deployments
- Click the URL to test - it will prompt for authorization

### "Script error" or "500 Internal Server Error"
- Check the Apps Script code was pasted correctly
- Open Apps Script editor
- Click "Executions" (left sidebar) to see error logs
- Make sure you saved the script after pasting

### Data not syncing
- Open browser console (F12) and check for errors
- Verify Web App URL in `google-sheets-config.js`
- Try clicking "🔍 Check Status" in Data Management
- Check Apps Script "Executions" log for errors

### "This app isn't verified" warning
- This is normal for personal scripts
- Click "Advanced" → "Go to [Project Name] (unsafe)"
- It's safe because it's YOUR script

## � Benefits of Apps Script

✅ **No API Key Needed** - Much simpler setup
✅ **Automatic Sync** - No manual push/pull
✅ **Free Forever** - No usage limits for personal use
✅ **Easy Updates** - Update script without changing URL
✅ **Secure** - Google's enterprise security
✅ **Fast** - Direct connection to Google Sheets
✅ **Reliable** - Google's 99.9% uptime
✅ **Multi-Device** - Works on any device

## 🆘 Need Help?

If you encounter issues:

1. Check this guide again carefully
2. Verify all steps were completed
3. Check browser console (F12) for error messages
4. Check Apps Script "Executions" log
5. Try redeploying the script with a new version

## 📝 Quick Reference

**Files to Edit**:
- `google-sheets-config.js` - Add your Web App URL here

**Apps Script File**:
- `apps-script-code.gs` - Copy this to Apps Script editor

**Google Sheet**:
- Create at: https://sheets.google.com
- Access Apps Script: Extensions → Apps Script

**Web App URL Format**:
```
https://script.google.com/macros/s/AKfycbx.../exec
```

**Sheet Names** (created automatically):
- Labor Records
- Work Types
- Translations

---

**Remember**: Everything syncs automatically! Just open the app and start working. 🎉
