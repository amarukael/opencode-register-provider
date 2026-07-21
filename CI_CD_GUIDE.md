# 🚀 CI/CD Setup - GitHub Actions

## ✅ What's Configured

Your repository now has **2 GitHub Actions workflows** for automated publishing to NPM.

### 📦 Workflows

#### 1. **Publish to NPM** (`publish.yml`)
- **Trigger:** Push tags starting with `v*` (e.g., `v1.0.0`)
- **Also:** Manual trigger via workflow_dispatch
- **What it does:** Automatically publishes to NPM when you create a version tag

#### 2. **Version Bump and Publish** (`version-bump.yml`)
- **Trigger:** Manual only (workflow_dispatch)
- **Options:** Patch, Minor, or Major version bump
- **What it does:** 
  - Bumps version in package.json
  - Commits and pushes changes
  - Creates git tag
  - Publishes to NPM
  - Creates GitHub Release

## 🔑 Required Secret

✅ **Already configured:** `NPM_TOKEN` in GitHub Secrets

## 🎯 How to Use

### Option 1: Manual Publish (Recommended for first release)

**Using workflow_dispatch in publish.yml:**

1. Go to: https://github.com/amarukael/opencode-register-provider/actions/workflows/publish.yml
2. Click **"Run workflow"**
3. Select branch: `main`
4. Click **"Run workflow"**

This will publish the current version (1.0.0) to NPM immediately.

### Option 2: Version Bump + Publish (For updates)

**Using version-bump.yml:**

1. Go to: https://github.com/amarukael/opencode-register-provider/actions/workflows/version-bump.yml
2. Click **"Run workflow"**
3. Choose version bump type:
   - `patch` → 1.0.0 → 1.0.1 (bug fixes)
   - `minor` → 1.0.0 → 1.1.0 (new features)
   - `major` → 1.0.0 → 2.0.0 (breaking changes)
4. Click **"Run workflow"**

This will:
- ✅ Bump version in package.json
- ✅ Commit: `chore: bump version to X.X.X`
- ✅ Create git tag: `vX.X.X`
- ✅ Push to GitHub
- ✅ Publish to NPM
- ✅ Create GitHub Release

### Option 3: Tag-based Publish (Automatic)

**For future releases:**

```bash
cd /home/openclaw/.openclaw/workspace/opencode-register-provider

# Bump version locally
npm version patch  # or minor, major

# Push tag (this triggers automatic publish)
git push --follow-tags
```

The `publish.yml` workflow will automatically run and publish to NPM.

## 📋 First Release Steps (Now!)

Since this is the first release, here's what to do:

### **Step 1: Commit workflows**

```bash
cd /home/openclaw/.openclaw/workspace/opencode-register-provider

git add .github/workflows/
git commit -m "ci: add GitHub Actions workflows for NPM publish"
git push origin main
```

### **Step 2: Trigger first publish**

**Option A: Manual via GitHub UI (Easiest)**
1. Go to: https://github.com/amarukael/opencode-register-provider/actions/workflows/publish.yml
2. Click "Run workflow"
3. Wait ~1-2 minutes
4. Check: https://www.npmjs.com/package/opencode-register-provider

**Option B: Create tag manually**
```bash
cd /home/openclaw/.openclaw/workspace/opencode-register-provider

git tag v1.0.0
git push origin v1.0.0
```

The workflow will automatically run and publish.

## 🔍 Monitor Progress

After triggering workflow:
1. Go to: https://github.com/amarukael/opencode-register-provider/actions
2. Click on the running workflow
3. Watch real-time logs

## 🎉 Success Indicators

After successful publish, you'll see:
- ✅ Green checkmark in Actions tab
- ✅ Package live at: https://www.npmjs.com/package/opencode-register-provider
- ✅ GitHub Release created (for version-bump workflow)

## 🚨 Troubleshooting

### Workflow fails with 403 error

**Cause:** NPM_TOKEN invalid or IP not whitelisted

**Solution:**
1. Verify token at: https://www.npmjs.com/settings/amarukael/tokens
2. Check IP allowlist includes: `178.238.238.159/32`
3. Regenerate token if needed
4. Update GitHub secret: https://github.com/amarukael/opencode-register-provider/settings/secrets/actions

### Workflow fails with "package already published"

**Cause:** Version already exists on NPM

**Solution:**
1. Bump version: `npm version patch`
2. Commit and push
3. Run workflow again

### Tag already exists

**Cause:** Git tag already created

**Solution:**
```bash
git tag -d v1.0.0        # Delete local
git push origin :v1.0.0  # Delete remote
npm version patch        # Create new version
git push --follow-tags   # Push new tag
```

## 📊 Workflow Files

- `.github/workflows/publish.yml` - Tag-based + manual publish
- `.github/workflows/version-bump.yml` - Version management + publish

Both workflows use the same `NPM_TOKEN` secret for authentication.

---

**Ready to publish?** Commit the workflows and trigger the first release! 🚀💕
