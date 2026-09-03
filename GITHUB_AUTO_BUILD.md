# 🚀 GitHub Auto-Build APK - Complete Guide

This guide explains how to automatically build the APK on GitHub every time you push code.

---

## ✨ What This Does

**Once configured:**
- ✅ Push code to GitHub
- ✅ Workflow automatically builds APK
- ✅ APK ready for download in 5-10 minutes
- ✅ No local build needed
- ✅ Share download link with team

---

## 🎯 Benefits

| Benefit | Details |
|---------|---------|
| **No Local Build** | Don't need Flutter/Android Studio installed |
| **Automatic** | Just push and wait 5-10 minutes |
| **Shareable** | Direct download link for team |
| **Version History** | Every build is saved |
| **No Manual Steps** | Completely hands-off |

---

## 📋 Setup Steps

### Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Create new repository:
   - Name: `pharmacy-scanner`
   - Description: "AL REHMAN Pharmacy Mobile Barcode Scanner"
   - Public or Private (your choice)
   - **Don't** add README/gitignore (we have them)
3. Click "Create repository"

### Step 2: Push Code to GitHub

On your computer (Windows/Mac/Linux):

```bash
# Navigate to project
cd pharmacy_scanner

# Initialize git (if not already done)
git init
git add .
git commit -m "Initial commit: Complete Flutter app"

# Add remote (replace USERNAME with your GitHub username)
git remote add origin https://github.com/USERNAME/pharmacy-scanner.git
git branch -M main
git push -u origin main
```

### Step 3: GitHub Actions Automatically Starts

Once you push:
1. Go to: https://github.com/USERNAME/pharmacy-scanner
2. Click: "Actions" tab
3. See: Build workflow running
4. Wait: 5-10 minutes for build to complete
5. Download: APK from artifacts

That's it! 🎉

---

## 📥 Download APK from GitHub

### After Build Completes

**Option 1: From Artifacts (Every Push)**
1. Go to: Repository → Actions
2. Click: Latest workflow run
3. Scroll down: "Artifacts" section
4. Download: `pharmacy-scanner-apk.zip`
5. Extract: Contains `flutter-app.apk`

**Option 2: From Releases (Tagged Versions)**
1. Go to: Repository → Releases
2. Click: Latest release
3. Download: `flutter-app.apk`

**Option 3: Direct Download Link**
Once you create a release:
```
https://github.com/USERNAME/pharmacy-scanner/releases/download/v1.0.0/flutter-app.apk
```

---

## 🏷️ Creating Releases (Optional)

To create a release (recommended for versions):

```bash
# Tag a version
git tag -a v1.0.0 -m "Version 1.0.0 - Initial release"
git push origin v1.0.0
```

Then:
1. Go to GitHub → Releases
2. New release appears automatically
3. APK is automatically attached
4. Share the download link

---

## 📊 Workflow Explained

What the GitHub Actions workflow does:

```
1. Code Pushed to GitHub
   ↓
2. Ubuntu Server Starts
   ↓
3. Installs Java, Flutter, dependencies
   ↓
4. Builds APK (flutter build apk --release)
   ↓
5. APK uploaded as artifact
   ↓
6. Ready for download (5-10 minutes)
```

**Time breakdown:**
- Setup: 1-2 min
- Dependencies: 2-3 min
- Build: 2-5 min
- Total: 5-10 min

---

## 📁 File Structure on GitHub

```
pharmacy-scanner/
├── .github/
│   └── workflows/
│       └── build.yml          ← GitHub Actions configuration
├── lib/
│   └── main.dart
├── android/
│   └── ...
├── pubspec.yaml
├── README.md
├── .gitignore
└── ... (all other files)
```

The `.github/workflows/build.yml` file is already included in your project.

---

## 🔧 Customization

### Change Build Trigger

Current triggers (when to build):
- On push to `main` or `master` branch
- On pull requests
- On git tags starting with `v` (e.g., v1.0.0)

To customize, edit `.github/workflows/build.yml`:

```yaml
on:
  push:
    branches:
      - main
      - master
    tags:
      - 'v*'
  pull_request:
    branches:
      - main
      - master
```

### Change APK Name

Edit the workflow file and change:
```yaml
path: build/app/outputs/flutter-app.apk
```

### Change Retention Period

Current: 30 days. To change:
```yaml
retention-days: 30  ← Change this number
```

---

## 🚨 Troubleshooting

### Build Failed in GitHub Actions

**Check logs:**
1. Go to: Actions → Latest workflow
2. Click: "Build" job
3. Expand: See error messages

**Common issues:**
- SDK version mismatch → Update Flutter version in workflow
- Dependency issues → Run `flutter clean && flutter pub get` locally
- Android build issues → Check Android manifest

### APK Not Showing Up

**Solutions:**
1. Refresh page (sometimes takes time)
2. Wait another 2 minutes
3. Check "Actions" tab for any errors
4. Look for red ✗ marks in workflow

### Can't Find Artifacts

**Try this:**
1. Go to: https://github.com/USERNAME/pharmacy-scanner/actions
2. Click: Latest successful workflow
3. Scroll down to "Artifacts"
4. Download the zip file

---

## 📤 Share APK with Team

### Option 1: Share GitHub Link
"Download APK from: https://github.com/USERNAME/pharmacy-scanner/releases/download/v1.0.0/flutter-app.apk"

### Option 2: Release Notes
Include installation instructions in release notes:
```
# Version 1.0.0

## Installation
1. Download flutter-app.apk
2. Copy to phone
3. Enable "Unknown Sources"
4. Tap APK to install

## Configuration
Open app → Settings → Enter desktop IP

## Features
- Real-time barcode scanning
- WiFi sync to POS
- Item management
```

### Option 3: Direct Distribution
```
Release downloads → Right-click → Copy link
Share link with team via email/WhatsApp
```

---

## 🔐 Security Notes

### Public Repository
- Code is visible to everyone
- APK is downloadable by anyone
- Good for open-source

### Private Repository
- Requires GitHub login to access
- Only team members can see code/APK
- Better for business

**To make private:**
1. Repository → Settings
2. Scroll to "Danger Zone"
3. Click "Make private"

---

## 🔄 Workflow Status Badge

Add to your README.md:

```markdown
[![Build Status](https://github.com/USERNAME/pharmacy-scanner/workflows/Build%20%26%20Release%20APK/badge.svg)](https://github.com/USERNAME/pharmacy-scanner/actions)
```

Shows build status with green ✓ or red ✗

---

## 📝 Example Workflow

**What happens when you:**

```bash
git add .
git commit -m "Update barcode timeout"
git push origin main
```

**Then:**
1. GitHub detects push
2. Actions starts automatically
3. 2 min: Build environment setup
4. 3 min: Dependencies installed
5. 4 min: APK compiled
6. 1 min: Upload artifacts
7. **Total: ~10 minutes**
8. APK ready for download

---

## 🎯 Version Management

### Recommended Versioning

**In `pubspec.yaml`:**
```yaml
version: 1.0.0+1
```

**On GitHub:**
```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
```

**Result:**
- Automatic release created
- APK named: `flutter-app.apk`
- Download from: Releases page

---

## 📊 Checking Build Status

### During Build
1. Go to: Actions tab
2. See: Yellow ⏳ (running)
3. Check: Each step's progress

### After Build
1. Go to: Actions tab
2. See: Green ✓ (success) or Red ✗ (failed)
3. Download: From artifacts or releases

---

## 🚀 Advanced Usage

### Build Multiple Architectures

The current setup builds for all ARM architectures (most common).

To build separate APKs:
```yaml
run: flutter build apk --release --split-per-abi
```

Creates:
- `flutter-app-armeabi-v7a-release.apk` (older phones)
- `flutter-app-arm64-v8a-release.apk` (modern phones)

### Automatic Testing

Before build, run tests:
```yaml
- name: Run tests
  run: flutter test
```

Fails build if tests fail (quality gate).

### Slack Notifications (Optional)

Send build notifications to Slack:
```yaml
- name: Notify Slack
  if: always()
  uses: 8398a7/action-slack@v3
  with:
    status: ${{ job.status }}
    text: 'Build ${{ job.status }}'
    webhook_url: ${{ secrets.SLACK_WEBHOOK }}
```

---

## 💡 Tips & Tricks

### Tip 1: Frequent Commits
Make small commits often → Always have latest APK available

### Tip 2: Use Tags for Releases
Tag important versions:
```bash
git tag -a v1.0.1 -m "Bug fix release"
git push origin v1.0.1
```

### Tip 3: Update README
Add download link to README:
```markdown
## Download
[Latest Release](https://github.com/USERNAME/pharmacy-scanner/releases)
```

### Tip 4: Automate Release Notes
GitHub can auto-generate release notes from commit messages

### Tip 5: Monitor Build Time
Check build logs to see which steps are slow

---

## 🎓 Learning Resources

### GitHub Actions Docs
https://docs.github.com/en/actions

### Flutter + GitHub Actions
https://flutter.dev/docs/deployment/cd

### Android CI/CD
https://github.com/marketplace/actions/flutter-action

---

## ❓ FAQ

**Q: Do I need Flutter installed locally?**
A: No! GitHub Actions handles everything. You just push code.

**Q: How long does build take?**
A: 5-10 minutes total on GitHub's servers.

**Q: Can I download old APKs?**
A: Yes! All builds are saved for 30 days.

**Q: Is GitHub free?**
A: Yes! Free tier includes GitHub Actions.

**Q: Can I make the repo private?**
A: Yes! GitHub Actions works with private repos too.

**Q: What if build fails?**
A: Check the Actions tab for error messages. Usually just missing dependencies.

**Q: Can I trigger builds manually?**
A: Yes! Add `workflow_dispatch` to the workflow file.

---

## ✅ Complete Checklist

- [ ] Created GitHub repository
- [ ] Pushed code to GitHub
- [ ] `.github/workflows/build.yml` is in your repo
- [ ] First build completed (check Actions tab)
- [ ] Downloaded APK from artifacts
- [ ] Tested APK on phone
- [ ] Shared link with team
- [ ] Created first release (optional)
- [ ] Updated README with download link (optional)

---

## 🎉 You're Done!

Your APK now builds automatically on GitHub.

**Next time you make changes:**
1. Edit code
2. `git push`
3. Wait 5-10 minutes
4. Download APK from GitHub

**No more local builds needed!** 🚀

---

## 🔗 Quick Links

- **Repository:** https://github.com/USERNAME/pharmacy-scanner
- **Actions:** https://github.com/USERNAME/pharmacy-scanner/actions
- **Releases:** https://github.com/USERNAME/pharmacy-scanner/releases
- **Download:** https://github.com/USERNAME/pharmacy-scanner/releases/latest

(Replace USERNAME with your actual GitHub username)

---

Happy building! 🎯📱
