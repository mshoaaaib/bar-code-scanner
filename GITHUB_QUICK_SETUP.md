# ⚡ GitHub Auto-Build - 5 Minute Setup

Get automatic APK builds on GitHub in just 5 minutes!

---

## 🎯 What Happens

**You:** Push code to GitHub  
**GitHub:** Automatically builds APK  
**You:** Download APK in 5-10 minutes  
**Repeat:** Every push builds a new APK

---

## 5️⃣ Steps (5 minutes total)

### Step 1: Create GitHub Repo (1 min)
```
1. Go to: https://github.com/new
2. Name: pharmacy-scanner
3. Description: AL REHMAN Pharmacy Mobile Scanner
4. Click: Create Repository
```

### Step 2: Initialize Git Locally (1 min)
```bash
cd pharmacy_scanner
git init
git add .
git commit -m "Initial commit"
```

### Step 3: Add Remote & Push (2 min)
```bash
# Replace USERNAME with your GitHub username
git remote add origin https://github.com/USERNAME/pharmacy-scanner.git
git branch -M main
git push -u origin main
```

### Step 4: GitHub Actions Starts Automatically (1 min)
- Go to: https://github.com/USERNAME/pharmacy-scanner/actions
- See: "Build & Release APK" workflow running
- Wait: 5-10 minutes for build

### Step 5: Download APK (Free!)
- Go to: Actions → Latest workflow run
- Scroll down: "Artifacts" section
- Download: `pharmacy-scanner-apk`
- Extract: Contains `flutter-app.apk`

---

## ✅ That's It!

From now on, every time you push:
```bash
git push origin main
```

The APK builds automatically on GitHub. No local build needed!

---

## 📥 How to Get APK After Each Push

### Option 1: From Artifacts (Fastest)
```
Repository → Actions → Latest Workflow → Artifacts → Download
```

### Option 2: Create Release (Recommended)
```bash
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin v1.0.0
```

Then:
```
Repository → Releases → Download APK
```

### Option 3: Direct Link (Sharable)
```
https://github.com/USERNAME/pharmacy-scanner/releases/download/v1.0.0/flutter-app.apk
```

---

## 🔄 Workflow

```
You write code
        ↓
git push origin main
        ↓
GitHub detects push
        ↓
GitHub Actions starts
        ↓
Installs Flutter & Android
        ↓
flutter build apk --release
        ↓
APK ready! (5-10 minutes)
        ↓
Download from GitHub
        ↓
Install on phone ✓
```

---

## 💡 Pro Tips

### Tip 1: Tag Versions
```bash
# After testing and release
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0

# APK appears in Releases tab
```

### Tip 2: Share Release Link
```
Send to team:
https://github.com/USERNAME/pharmacy-scanner/releases
```

### Tip 3: Status Badge
Add to README.md:
```markdown
![Build Status](https://github.com/USERNAME/pharmacy-scanner/workflows/Build%20%26%20Release%20APK/badge.svg)
```

### Tip 4: Commit Messages Matter
```bash
git commit -m "Fix barcode timeout"
# Describes what changed
```

---

## 🚨 If Build Fails

Check logs:
1. Go to: Actions tab
2. Click: Failed workflow
3. Expand: "Build" section
4. See: Error message
5. Fix: Commit and push again

**Usually just:**
```bash
flutter clean
git add .
git commit -m "Fix build"
git push
```

---

## 📊 Example Workflow

**Your commands:**
```bash
# Make changes to code
git add .
git commit -m "Update barcode timeout to 10s"
git push origin main
```

**GitHub does automatically:**
1. Detects your push
2. Starts Actions workflow
3. Sets up Ubuntu machine
4. Installs Java, Flutter, dependencies
5. Runs: flutter build apk --release
6. Uploads APK as artifact
7. (5-10 minutes later) Ready to download

**You:**
```
Go to Actions → Download APK → Install on phone
```

---

## 🎯 Next: Share with Team

Once APK is built:

### Option A: Download & Share File
- Download APK
- Send via WhatsApp, Email, Drive

### Option B: Share GitHub Link
- Send: https://github.com/USERNAME/pharmacy-scanner/releases
- Team clicks → Downloads APK

### Option C: Direct Download Link
```
https://github.com/USERNAME/pharmacy-scanner/releases/download/v1.0.0/flutter-app.apk
```

---

## 🔒 Private Repository (Optional)

If you want only your team to access:

1. Go to: Repository Settings
2. Scroll to: "Danger Zone"
3. Click: "Make private"
4. Share link with: Team members only

---

## 🚀 Advanced (Optional)

### Auto-Release Notes
GitHub can generate release notes from commits:
1. Create release
2. Click: "Auto-generate release notes"
3. Done!

### Slack Notifications
Get notified when build completes:
1. Create Slack webhook
2. Add to workflow (see GITHUB_AUTO_BUILD.md)
3. Get notifications in Slack channel

### Build Split APKs
For different phone architectures:
Edit `.github/workflows/build.yml` and use:
```yaml
run: flutter build apk --release --split-per-abi
```

---

## 📚 Full Guide

For complete details, see:
👉 **GITHUB_AUTO_BUILD.md** (comprehensive guide)

This document covers:
- Detailed setup with screenshots
- Customization options
- Troubleshooting
- Advanced features
- Security considerations

---

## ❓ FAQ

**Q: Do I need Flutter installed?**
A: No! GitHub installs it for you.

**Q: How often can I build?**
A: As often as you want! GitHub Actions is free.

**Q: Can I build locally too?**
A: Yes! You can do both. Use `build.bat` for local builds.

**Q: Is it secure?**
A: Yes! Use private repository for private code.

**Q: Can I schedule automatic builds?**
A: Yes! Edit workflow to build on schedule.

---

## ✅ Quick Checklist

- [ ] Created GitHub repository
- [ ] Pushed code to GitHub
- [ ] First build completed (check Actions)
- [ ] Downloaded APK
- [ ] Installed on phone
- [ ] Ready to share with team

---

## 🎉 You're Set!

Your APK now builds automatically. Enjoy! 🚀

Next: Commit code → Push → GitHub builds → Download → Done!

---

**Questions?** See: GITHUB_AUTO_BUILD.md
