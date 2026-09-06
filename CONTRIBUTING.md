# Contributing guide

This repo is a GitHub Pages site: **anything pushed to `main` deploys to the
live site (tiarto.com) immediately.** To avoid accidents, we never push
directly to `main` — we follow the flow below instead.

## Onboarding checklist for a new teammate (for admins)

1. **Settings → Collaborators and teams → Add people**
   - Invite with the **Write** role (promote to Admin later once trust is established).
2. **Settings → Branches → Add branch protection rule** (target `main`, one-time setup that persists)
   - `Require a pull request before merging` + `Require approvals` (at least 1)
   - `Do not allow bypassing the above settings` (applies to admins too — prevents accidental direct pushes)
   - `Block force pushes`, `Restrict deletions`
3. Add the new teammate's GitHub username to `.github/CODEOWNERS`
   - Example: `* @donghyup-shin @new-username`
   - This makes review requests go out automatically when a PR is opened

> Steps 1-2 can only be done in the GitHub web UI, so Claude can't do them for you — an admin needs to click through the paths above.

## Everyday workflow (all contributors)

```bash
# 1. Get the latest main
git checkout main
git pull origin main

# 2. Create a working branch (any name, e.g. yourname-task)
git checkout -b yourname/update-hero-text

# 3. Make changes and commit
git add .
git commit -m "Update hero copy"

# 4. Push your branch
git push -u origin yourname/update-hero-text
```

Then click **"Compare & pull request"** on the repo page to open a PR.
Opening a PR auto-fills the checklist from `.github/pull_request_template.md`,
and automatically requests a review from whoever is listed in `CODEOWNERS`.

Once a reviewer approves, click **"Merge pull request"** to merge into `main` —
that's when the site deploys.

## TL;DR

- No direct pushes to `main` ❌
- Branch → PR → review → merge ✅
- With branch protection on, skipping this order is blocked at the push/merge level.
