# GitHub Database Setup Guide

This guide will help you set up GitHub as a cloud database for your Labor Wage Tracking System.

## ✨ New Feature: Automatic Sync

Once configured, the system **automatically syncs all changes to GitHub** in the background:
- Adding records → Auto-synced ✅
- Deleting records → Auto-synced ✅
- Adding work types → Auto-synced ✅
- Removing work types → Auto-synced ✅

**No manual push needed!** Just configure once and forget about it.

## 📋 Prerequisites

- A computer with internet access
- A web browser (Chrome, Firefox, Edge, etc.)
- Basic understanding of copying and pasting text

## 🚀 Step-by-Step Setup

### Step 1: Create a GitHub Account

1. Go to [https://github.com](https://github.com)
2. Click the **"Sign up"** button in the top right
3. Enter your email address
4. Create a password (make it strong!)
5. Choose a username (e.g., "john-farmer" or "agricultural-records")
6. Complete the verification
7. Click **"Create account"**

### Step 2: Create a Personal Access Token

This token allows the app to save data to your GitHub account.

1. After logging in, click your profile picture (top right)
2. Click **"Settings"**
3. Scroll down and click **"Developer settings"** (bottom left)
4. Click **"Personal access tokens"**
5. Click **"Tokens (classic)"**
6. Click **"Generate new token"** → **"Generate new token (classic)"**
7. Fill in the form:
   - **Note**: "Labor Tracking System"
   - **Expiration**: Choose "No expiration" or "90 days"
   - **Select scopes**: Check the box for **"repo"** (Full control of private repositories)
8. Scroll down and click **"Generate token"**
9. **IMPORTANT**: Copy the token immediately! It looks like: `ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`
10. Save it in a safe place (you won't see it again!)

### Step 3: Create a Repository

This is where your data will be stored.

1. Go to [https://github.com/new](https://github.com/new)
2. Fill in the repository details:
   - **Repository name**: `labor-tracking-data` (or any name you prefer)
   - **Description**: "Labor wage tracking data storage"
   - **Visibility**: Choose **"Private"** (recommended for sensitive data)
   - Leave other options as default
3. Click **"Create repository"**
4. Note down your repository name

### Step 4: Configure the Application

1. Open the file `github-config.js` in a text editor (Notepad, VS Code, etc.)
2. Find these lines:

```javascript
const GITHUB_CONFIG = {
    username: 'YOUR_GITHUB_USERNAME',
    repo: 'YOUR_REPOSITORY_NAME',
    token: 'YOUR_GITHUB_TOKEN',
    branch: 'main',
    ...
};
```

3. Replace the values:
   - `YOUR_GITHUB_USERNAME`: Your GitHub username (from Step 1)
   - `YOUR_REPOSITORY_NAME`: Your repository name (from Step 3)
   - `YOUR_GITHUB_TOKEN`: The token you copied (from Step 2)

4. Example:
```javascript
const GITHUB_CONFIG = {
    username: 'john-farmer',
    repo: 'labor-tracking-data',
    token: 'ghp_1234567890abcdefghijklmnopqrstuvwxyz',
    branch: 'main',
    ...
};
```

5. Save the file

### Step 5: Test the Connection

1. Open `index.html` in your web browser
2. Click **"📊 Data Management"** button in the header
3. In the **"🔗 GitHub Sync"** section, click **"🔍 Check Status"**
4. You should see: "✅ GitHub connection successful!"

If you see an error, double-check your configuration in Step 4.

## 📊 Using GitHub Sync

### Automatic Sync (Recommended)

The system now **automatically syncs** to GitHub whenever you:
- ✅ Add a new work record
- ✅ Delete a work record
- ✅ Add a new work type/category
- ✅ Remove a work type/category

**No manual action needed!** Your data is automatically backed up to GitHub in the background.

### Manual Sync (Optional)

You can also manually sync using the buttons:

#### Push Data to GitHub (Backup)

1. Click **"📊 Data Management"**
2. Click **"☁️ Push to GitHub"**
3. Your data is now safely stored in GitHub!

#### Pull Data from GitHub (Restore)

1. Click **"📊 Data Management"**
2. Click **"📥 Pull from GitHub"**
3. Confirm the action
4. Your data is restored from GitHub!

## 🔄 Workflow Recommendations

### Daily Workflow (Simplified)

**Morning:**
- Open the application
- Click "📥 Pull from GitHub" to get latest data (if using multiple devices)

**Throughout the day:**
- Add work entries as usual
- Delete/modify entries as needed
- **Everything syncs automatically to GitHub!** ✨

**No need to manually push** - the system does it for you!

### Multiple Devices

**Device 1:**
- Add entries → **Auto-synced to GitHub** ✅

**Device 2:**
- Pull from GitHub → See all entries from Device 1
- Add more entries → **Auto-synced to GitHub** ✅

**Device 1:**
- Pull from GitHub → See all entries from Device 2

## 🔒 Security Best Practices

1. **Keep Your Token Secret**
   - Never share your Personal Access Token
   - Don't post it online or in public repositories
   - Treat it like a password

2. **Use Private Repositories**
   - Always use private repositories for sensitive data
   - This ensures only you can access your labor records

3. **Regular Backups**
   - Push to GitHub daily
   - GitHub keeps version history, so you can recover old data

4. **Token Expiration**
   - If you set an expiration date, remember to renew your token
   - Update `github-config.js` with the new token

## ❓ Troubleshooting

### "GitHub is not configured" Error
- Check that you've edited `github-config.js`
- Make sure you replaced ALL placeholder values
- Refresh the page after saving changes

### "Cannot connect to GitHub" Error
- Check your internet connection
- Verify your username and repository name are correct
- Make sure the repository exists and is accessible

### "Authentication failed" Error
- Your token might be expired or invalid
- Generate a new token (Step 2) and update `github-config.js`
- Make sure you selected the "repo" scope when creating the token

### "Repository not found" Error
- Check the repository name is spelled correctly
- Make sure the repository exists in your GitHub account
- Verify the repository is not deleted

## 📱 Benefits of GitHub Sync

✅ **Cloud Backup** - Your data is safely stored in the cloud
✅ **Automatic Sync** - No manual push needed, syncs on every change
✅ **Version History** - GitHub keeps all previous versions
✅ **Multi-Device** - Access your data from any device
✅ **Free** - GitHub offers free private repositories
✅ **Reliable** - GitHub has 99.9% uptime
✅ **Secure** - Industry-standard security and encryption
✅ **Real-time** - Changes sync immediately in the background

## 🆘 Need Help?

If you encounter issues:
1. Check this guide again carefully
2. Verify all configuration values
3. Try generating a new token
4. Make sure your repository is private and accessible

## 📝 Quick Reference

**GitHub URLs:**
- Sign up: https://github.com/signup
- Create token: https://github.com/settings/tokens
- Create repo: https://github.com/new

**Configuration File:**
- `github-config.js` - Edit this file with your credentials

**Required Information:**
- GitHub username
- Repository name
- Personal Access Token
- Branch name (usually "main")

---

**Remember**: Always push to GitHub at the end of each day to keep your data safe!
