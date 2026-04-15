---
name: kb-sync
description: >
  Commits and pushes all changes in the Brain knowledge base to GitHub.
  Use whenever the user says /sync, "push to github", "sync to git", or
  "save to github". Also runs automatically after kb-compile and kb-index.
---

# kb-sync — Push Brain to GitHub

Commit all changes and push to https://github.com/fernfant/Brain

## Steps

1. Run `git -C /Users/fernando/Brain add -A`
2. Check if there's anything to commit: `git -C /Users/fernando/Brain status --short`
3. If changes exist, commit: `git -C /Users/fernando/Brain commit -m "[YYYY-MM-DD] auto-sync — <short summary of what changed>"`
4. Push: `git -C /Users/fernando/Brain push origin main`
5. Report: "Synced to https://github.com/fernfant/Brain — N files changed"

If nothing to commit: "Brain is already up to date on GitHub."
