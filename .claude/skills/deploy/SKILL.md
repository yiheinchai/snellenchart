---
name: deploy
description: Commit, push to GitHub, and deploy to Cloudflare Pages. Use when the user says "deploy", "push and deploy", "ship it", "publish", or asks to commit and deploy changes.
---

# Deploy Snellen Chart

Commit any pending changes, push to GitHub, and deploy to Cloudflare Pages.

## Steps

1. **Check for changes**: Run `git status` and `git diff --stat` to see if there are uncommitted changes.

2. **Commit** (if there are changes):
   - Stage modified/new files with `git add` (add specific files, not `-A`)
   - Review the diff to write a clear, descriptive commit message
   - Commit with the message ending with:
     ```
     Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
     ```
   - Use a HEREDOC for the commit message

3. **Push**: Run `git push origin main`

4. **Deploy**: Run `npx wrangler pages deploy . --project-name snellenchart` from the project root

5. **Report**: Show the user the deployment URL and confirm success

## Notes

- If there are no changes to commit, skip straight to push + deploy
- Never use `--force` on push
- Never use `--no-verify` on commit
- The Cloudflare Pages project name is `snellenchart`
- The custom domain is `snellenchart.uk`
