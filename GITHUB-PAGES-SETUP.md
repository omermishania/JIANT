# GitHub Pages Setup for Omer's JIANT Fork

## 🎯 Goal
Enable the web installer at: `https://omermishania.github.io/JIANT/webapp/installer/`

---

## 📋 EXACT CLICKS FOR OMER

### Step 1: Enable GitHub Pages (REQUIRED)

1. Go to: https://github.com/omermishania/JIANT/settings/pages
2. Under **"Build and deployment"**:
   - **Source**: Select **"GitHub Actions"** from the dropdown
   - (NOT "Deploy from a branch" - select "GitHub Actions")
3. Click **Save** (if button appears)
4. Wait 30 seconds for settings to apply

**Screenshot location**: The "Source" dropdown is in the middle of the page

---

### Step 2: Merge the PR (REQUIRED for Deployment)

**Option A: Merge via GitHub UI** (Recommended)
1. Go to: https://github.com/omermishania/JIANT/pull/1
2. Click green **"Merge pull request"** button
3. Click **"Confirm merge"**
4. Wait ~2 minutes for workflow to run

**Option B: Merge via Command Line**
```bash
cd /path/to/JIANT
git checkout main
git merge cursor/omer-melodic-house-features-849d
git push origin main
```

**Why merge is needed**: The workflow only deploys from the `main` branch on the fork's default Pages settings.

---

### Step 3: Check Deployment Status

1. Go to: https://github.com/omermishania/JIANT/actions
2. Look for **"Publish Custom Installer"** workflow
3. Wait for green checkmark (✓) - takes ~1-2 minutes
4. If you see ⚠️ or ❌:
   - Click the failed workflow
   - Check if it says "needs approval for environment"
   - If so, follow Step 4 below

---

### Step 4: (If Needed) Approve Environment Deployment

**Only if the workflow shows "Waiting for approval"**:

1. Go to: https://github.com/omermishania/JIANT/settings/environments
2. Click **"github-pages"** environment
3. Under **"Deployment branches and tags"**:
   - If it says "Selected branches", click **"Change to..."**
   - Select **"All branches"** OR add `main` specifically
4. Click **"Save protection rules"**
5. Go back to Actions tab and re-run the workflow

**Alternative**: Just approve the pending deployment on the Actions page when prompted

---

### Step 5: Access the Installer

**URL**: https://omermishania.github.io/JIANT/webapp/installer/

**If you get 404**:
1. Wait 2-3 minutes (Pages deployment can be slow)
2. Hard refresh: Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows)
3. Check Actions tab to confirm workflow finished successfully

---

## ✅ HOW TO VERIFY IT WORKED

1. Open: https://omermishania.github.io/JIANT/webapp/installer/
2. You should see the JIANT installer with:
   - "JIANT FM dev" or "JIANT FM custom" package listed
   - File size: 596 KB
   - Install button ready to use

3. Connect FM-1 via USB
4. Click **"Install JIANT FM"**
5. Follow backup and install prompts

---

## 🔄 AFTER FUTURE UPDATES

When you push new firmware commits to `main`:
1. Workflow runs automatically
2. Wait ~2 minutes
3. Installer updates at the same URL
4. No need to repeat setup steps!

---

## 🆘 TROUBLESHOOTING

### "404 Not Found" after 5+ minutes
- Check Actions tab for failed workflow
- Verify Pages is set to "GitHub Actions" source
- Ensure PR was merged to `main` (not just the feature branch)

### "Waiting for approval" in Actions
- Go to Settings > Environments > github-pages
- Change deployment branches to "All branches" or add `main`

### Workflow fails with "permission denied"
- Go to Settings > Actions > General
- Under "Workflow permissions", select "Read and write permissions"
- Save and re-run workflow

---

## 📝 WHAT THE WORKFLOW DOES

1. Checks out the repository
2. Installs Python dependencies (Pillow, fonttools)
3. Runs `python3 web/make_site.py release/*.fwsc dev _site`
4. Uploads the built site to GitHub Pages
5. Deploys to: https://omermishania.github.io/JIANT/

**Local test** (to verify before pushing):
```bash
cd /path/to/JIANT
python3 web/make_site.py release/jiant-v10.8.25-omer-features.fwsc dev /tmp/test-site
cd /tmp/test-site && python3 -m http.server 8000
# Open http://localhost:8000/webapp/installer/
```

---

## ✅ SUMMARY: THE THREE REQUIRED CLICKS

1. **Settings → Pages → Source: "GitHub Actions"**
2. **Pull Requests → #1 → "Merge pull request"**
3. **Wait 2 minutes**, then open: https://omermishania.github.io/JIANT/webapp/installer/

**That's it!** 🎉

---

**Repository**: https://github.com/omermishania/JIANT  
**Pull Request**: https://github.com/omermishania/JIANT/pull/1  
**Installer URL** (after setup): https://omermishania.github.io/JIANT/webapp/installer/  
**Direct firmware**: https://github.com/omermishania/JIANT/raw/refs/heads/cursor/omer-melodic-house-features-849d/release/jiant-v10.8.25-omer-features.fwsc
