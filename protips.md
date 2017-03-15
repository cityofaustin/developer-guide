---
title: ProTips
position: 1
layout: page
---

## Git ProTips

### Save time with aliases

Create git or shell aliases for common commands like checkout, branch, status, and commit.

* [“Git Basics - Git Aliases” from Pro Git](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

### Clean up merged branches

`git branch --merged` lists local branches that have been merged into master and are safe to delete; `git remote prune origin` cleans up the local copies of deleted remote branches. Periodically clean up “stale” branches on GitHub.

* [“Viewing branches in your repository” from GitHub](https://help.github.com/articles/viewing-branches-in-your-repository/)

### Create a global .gitignore

Use a global .gitignore to avoid committing files specific to your development machine or process, like `.rvmrc` or `.rbenv-gemset`. It’s [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) and tidy.

* [“Ignoring files: Create a global .gitignore” from GitHub](https://help.github.com/articles/ignoring-files/#create-a-global-gitignore)

### Stash is your friend

Use `git stash` to store unfinished changes when you need to switch branches.

* [“Git Tools - Stashing and Cleaning” from Pro Git](https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning)

### Ask questions and share lessons

Git is easier to use than it once was, but it’s still common to encounter unfamiliar errors. There’s almost always a quick way to recover, so use Google and don’t hesitate to ask around. When you learn something new, share it with others.

* [“Git Internals - Maintenance and Data Recovery” from Pro Git](https://git-scm.com/book/en/v2/Git-Internals-Maintenance-and-Data-Recovery)
