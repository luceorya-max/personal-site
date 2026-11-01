---
name: feature-commit-push
description: Commit and push every finished feature in the personal-site repo, creating a feature branch when the change is large or isolated. Use whenever a new feature, section, page, or visible change is completed in this repository.
---

# Feature commit and push (personal-site)

Use this after finishing a feature in `/Users/LuceOrya/code/websites/personal-site`. A feature is any visible change to the site: a new section, a new page, a new style, new copy, or a fix that changes what the visitor sees.

## Steps

1. **Check the state first.**
   - Run `git status --short` and `git branch --show-current`.
   - If there are unrelated uncommitted changes, do not mix them in. Ask the user before continuing.

2. **Verify the feature works.**
   - Open `index.html` in the browser preview, check mobile and desktop widths, and confirm there is no horizontal scroll.
   - Do not commit a feature that is visibly broken.

3. **Choose the branch.**
   - Small copy or style tweaks: commit on `main`.
   - A new section, a new page, or a change that touches several parts of the page: create a branch first, named `feature/<short-kebab-slug>`, with `git switch -c feature/<slug>`.
   - If the user has asked for a specific branch, use that one.

4. **Commit.**
   - Stage only the files of this feature, by name when possible, instead of `git add .`.
   - Write a short message that says what the feature does, in English, in the imperative (for example `Add services section`).
   - End the message with the attribution line from the session settings:
     `Co-Authored-By: Claude Haiku 5.5 <noreply@anthropic.com>`

5. **Push.**
   - On a feature branch: `git push -u origin feature/<slug>`.
   - On `main`: `git push`.
   - Never use `--force`. Never push to `main` if the push would be rejected; stop and report instead.

6. **Report.**
   - Tell the user the branch name, the commit hash, and the link to the branch on GitHub, for example `https://github.com/luceorya-max/personal-site/tree/feature/<slug>`.
   - If a feature branch was created, say that it is not merged into `main` yet, and ask whether to merge it.

## Limits

- Do not merge branches into `main` on your own. Merging is a decision for the user.
- Do not deploy to Firebase as part of this skill. Deployment is a separate step the user asks for.
- Do not commit files that contain placeholders in square brackets, such as `[שם]`, unless the user has confirmed they are intended.
