This repository is for the theme template of my personal website. It's created by using Jekyll's theme, [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/).


## 🛠️ Safely Rebasing `master` with Upstream Changes

This workflow is to safely update the fork’s `master` branch by rebasing it onto the upstream repo, **without losing your own commits**.

---

### ✅ 1. Create a Backup (Highly Recommended)

Before rebasing (especially interactively), back up your current `master`:

```bash
git checkout master
git checkout -b backup-master-2025-06-08
```

Update the date as needed.

---

### 🔄 2. Fetch the Upstream Repository

If you haven’t added the upstream before:

```bash
git remote add upstream https://github.com/<original-user>/<repo>.git
```

Then fetch:

```bash
git fetch upstream
```

---

### 📌 3. Rebase Your `master` Onto `upstream/master`

```bash
git checkout master
git rebase upstream/master
```

---

### ⚠️ 4. Resolve Any Conflicts

If conflicts occur, resolve them manually:

```bash
# For example, if a file was deleted upstream but modified locally:
git rm <conflicted-file>
```

Then continue:

```bash
git rebase --continue
```

Repeat until the rebase completes.

---

### 👁️ 5. Test Your Site

Make sure everything still works:

```bash
bundle exec jekyll clean && bundle exec jekyll serve
```

Visit `http://localhost:4000` to verify.

---

### 🚀 6. Push the Rebasing Result (Force Push)

```bash
git push origin master --force
```

This is required since rebase rewrites history.

---

### 🧹 7. Delete the Backup (Optional)

Once you're confident your site is stable and working:

```bash
git branch -d backup-master-2025-06-08
```

If Git blocks the deletion due to unmerged commits:

```bash
git branch -D backup-master-2025-06-08
```
