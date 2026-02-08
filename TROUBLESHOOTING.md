# 🔧 Troubleshooting Guide

## Quick Diagnosis

### Step 1: Test Your Setup

1. Open **`test-google-sheets.html`** in your browser
2. Check the "Configuration Status" section
3. Click "Test Connection" button
4. Look at the results and console log

### Step 2: Common Issues and Fixes

## Issue 1: "Google Sheets is not configured"

**Symptoms:**
- Error message in console
- Connection test fails
- Data doesn't sync

**Solution:**
1. Open `google-sheets-config.js`
2. Make sure `webAppUrl` is filled in (not 'YOUR_WEB_APP_URL_HERE')
3. URL should look like: `https://script.google.com/macros/s/AKfycbx.../exec`
4. Save the file and refresh the page

## Issue 2: "Failed to fetch" or CORS Error

**Symptoms:**
- Console shows "Failed to fetch"
- Network error
- CORS policy error

**Solution:**
1. **Redeploy the Apps Script:**
   - Go to Apps Script editor
   - Click "Deploy" → "Manage deployments"
   - Click the pencil icon ✏️
   - Change "Version" to "New version"
   - Click "Deploy"
   - Copy the NEW URL (it might be different!)
   - Update `google-sheets-config.js` with the new URL

2. **Check "Who has access" setting:**
   - In deployment settings
   - Must be set to "Anyone"
   - NOT "Anyone with Google account"

## Issue 3: "Authorization required"

**Symptoms:**
- Script asks for authorization again
- "This app isn't verified" warning

**Solution:**
1. Go to your Apps Script editor
2. Click "Deploy" → "Test deployments"
3. Click the URL to test
4. Complete authorization again:
   - Click "Advanced"
   - Click "Go to [Project Name] (unsafe)"
   - Click "Allow"
5. Try the main app again

## Issue 4: Data Not Syncing

**Symptoms:**
- No error messages
- Data doesn't appear in Google Sheet
- Console shows success but sheet is empty

**Solution:**
1. **Check the Apps Script code:**
   - Open Apps Script editor
   - Make sure you pasted ALL the code from `apps-script-code.gs`
   - Click "Save"
   - Redeploy (new version)

2. **Check execution log:**
   - In Apps Script editor
   - Click "Executions" (left sidebar)
   - Look for errors in recent executions
   - Check what the error says

3. **Test with sample data:**
   - Open `test-google-sheets.html`
   - Click "Sync Sample Records"
   - Check if it works
   - If yes, the issue is with your main app
   - If no, check Apps Script logs

## Issue 5: "Script error" or "500 Internal Server Error"

**Symptoms:**
- HTTP 500 error
- "Script error" message
- Apps Script execution fails

**Solution:**
1. **Check Apps Script logs:**
   - Apps Script editor → "Executions"
   - Find the failed execution
   - Read the error message

2. **Common causes:**
   - **Missing permissions:** Reauthorize the script
   - **Syntax error:** Check if code was pasted correctly
   - **Sheet name mismatch:** Check SHEET_NAMES in Apps Script matches your config

3. **Fix and redeploy:**
   - Fix the issue in Apps Script
   - Click "Save"
   - Deploy → Manage deployments → Edit → New version

## Issue 6: Date Format Issues

**Symptoms:**
- Dates show as numbers
- Dates are incorrect
- "Invalid date" errors

**Solution:**
The updated Apps Script code handles date formatting automatically. If you still have issues:

1. Make sure you're using the latest `apps-script-code.gs`
2. Redeploy with new version
3. Dates should be formatted as YYYY-MM-DD

## Issue 7: "Redirect" or "HTML response instead of JSON"

**Symptoms:**
- Response is HTML instead of JSON
- Unexpected redirect
- Parse error

**Solution:**
1. **Check the URL:**
   - Must end with `/exec` (not `/dev`)
   - Should be the deployment URL, not the editor URL

2. **Use the correct URL:**
   - ❌ Wrong: `https://script.google.com/d/...`
   - ❌ Wrong: `https://script.google.com/macros/s/.../dev`
   - ✅ Correct: `https://script.google.com/macros/s/.../exec`

## Debugging Steps

### 1. Check Browser Console

Press F12 and look for:
- Red error messages
- Network requests (Network tab)
- Response data

### 2. Check Apps Script Logs

In Apps Script editor:
- Click "Executions" (left sidebar)
- Find recent executions
- Check for errors
- Read the error messages

### 3. Test with Simple Request

Open `test-google-sheets.html` and:
1. Test connection first
2. Then test sync
3. Then test load
4. Check console log at bottom

### 4. Verify Deployment

In Apps Script:
- Deploy → Manage deployments
- Check "Execute as" is "Me"
- Check "Who has access" is "Anyone"
- Try creating a new deployment

## Still Not Working?

### Create a Fresh Deployment

1. **In Apps Script editor:**
   ```
   Deploy → Manage deployments → Archive all
   Deploy → New deployment
   Select "Web app"
   Execute as: Me
   Who has access: Anyone
   Deploy
   ```

2. **Copy the NEW URL**

3. **Update config:**
   ```javascript
   webAppUrl: 'NEW_URL_HERE'
   ```

4. **Test again**

### Check These Settings

- [ ] Apps Script code is complete (all functions present)
- [ ] Code is saved in Apps Script editor
- [ ] Deployment is active (not archived)
- [ ] "Execute as" is set to "Me"
- [ ] "Who has access" is set to "Anyone"
- [ ] URL ends with `/exec`
- [ ] URL is in `google-sheets-config.js`
- [ ] Browser console shows no CORS errors
- [ ] Apps Script executions show no errors

## Getting Help

If you're still stuck:

1. **Open `test-google-sheets.html`**
2. **Run all tests**
3. **Copy the console log**
4. **Check Apps Script executions**
5. **Note the exact error message**

Common error patterns:
- "Failed to fetch" = CORS/deployment issue
- "Authorization required" = Need to reauthorize
- "Script error" = Check Apps Script logs
- "Not configured" = Update config file
- "500 error" = Check Apps Script code

---

**Most issues are solved by redeploying with a new version!** 🔄
