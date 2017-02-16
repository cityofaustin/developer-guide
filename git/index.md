---
title: Git Workflow
layout: page
---

## Git and GitHub

Developers contributing to the City’s projects on GitHub should be familiar with (or plan on learning about) Git, GitHub, and the concepts of distributed version control.

If you’re new to these tools, that’s okay—it’s cool to ask questions—but please also invest some time learning about them. We recommend starting with GitHub’s list of [Good Resources for Learning Git and GitHub](https://help.github.com/articles/good-resources-for-learning-git-and-github/) and the free book [Pro Git](https://git-scm.com/book/en/v2/).

* [“How GDS uses Git and GitHub” from the UK Government Digital Service](https://gdstechnology.blog.gov.uk/2014/01/27/how-we-use-github/)
* [“Coding in the open” from the UK Government Digital Service](https://gds.blog.gov.uk/2012/10/12/coding-in-the-open/)

### Using branches and pull requests

Most teams and projects should use [the branch-based workflow recommended by GitHub](https://guides.github.com/introduction/flow/), including pull requests and code review. Consider using GitHub’s features to [protect the master branch, require status checks, and require reviews](https://github.com/blog/2051-protected-branches-and-required-status-checks).

One caveat: GitHub suggests deploying production before merging pull requests, but if your project’s deployment environment has other staging and rollback features, or automates deploys of `master`, it’s typically fine to merge first.

Name branches using whole words separated by hyphens.

* [“Understanding the GitHub Flow” from GitHub](https://guides.github.com/introduction/flow/)
* [“GitHub - Contributing to a Project” from Pro Git](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)
* [“About protected branches” from GitHub](https://help.github.com/articles/about-protected-branches/)
* [“About required status checks” from GitHub](https://help.github.com/articles/about-required-status-checks/)
* [“Approving a pull request with required reviews” from GitHub](https://help.github.com/articles/approving-a-pull-request-with-required-reviews/)

### Writing commit messages

You should think of writing a commit message as telling a story about a change to a colleague sitting next to you. The commit diff shows _what_ changed, but not why: your message explains the why. The people who might read it include the teammates who review your code, developers who join the team or contribute to the project in the future, members of the public who may be interested in our work, and even yourself in the future.

If this style of commit message is new to you, you might find it helpful to review these resources:

* [“A Note About Git Commit Messages” by Tim Pope](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
* [“Deliberate Git” by Stephen Ball](http://rakeroutes.com/blog/deliberate-git/)
* [“Hidden Documentation” by Mislav Marohnić](http://mislav.net/2014/02/hidden-documentation/)

These expectations apply at every stage of a project:

* **Write the commit subject as a present tense command.** This style matches Git’s own, but more importantly, it helps you think about commits as actions applied to the repository, which makes them easier to reason about them when merging and rebasing.

  * Capitalize the first word
  * Punctuate sparingly
  * Limit the subject line to 70 characters

* **Use the commit body to explain why.** The body doesn’t have to be formal or present tense. Answer these questions: Why is this change necessary? How does it address the issue?  What side effects does it have? What alternatives did you consider?

  * Include a blank line between the subject and body
  * Use proper spelling and punctuation
  * Wrap lines at about 70 characters

  Use GitHub to link issues, other issue trackers

### Cleaning up commits

You don’t have to write a detailed commit message every time you call `git commit`. Most of the time, your first pass at a commit message might be a quick note to self, or even just “WIP” (work-in-progress).

That’s encouraged. Writing good commit messages doesn’t need to take you out of your coding flow. Instead, think of your WIP commits as rough drafts you’ll return to later.

While you’re working, it’s a good idea to create small commits frequently, because it’s easier to combine, reorder, and remove small commits than to split big commits. If necessary, [selectively stage files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#Staging-Modified-Files) before committing.

When you’re ready, you can write, edit, and structure your commits using git’s tools for rewriting history, `git commit --amend` and `git rebase --interactive`. If you’re learning about these tools for the first time, start with [Chapter 7 of Pro Git](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

Rewrite your WIP commits before you push your branch and open a pull request. Each pushed commit should represent a logical change: if you did some tangential refactoring, for example, keep that in a separate commit.

* [“Git Tools - Rewriting History” from Pro Git](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
* [“About Git rebase” from GitHub](https://help.github.com/articles/about-git-rebase/)

### Rewriting commits after you’ve pushed

If you’ve already pushed a branch before you rewrite its history, `git push` will refuse to overwrite the remote copy with the new history. Forcing the overwrite is called a force push.

Force pushing runs the risk of overwriting someone else’s commits, but you can mitigate this in two ways:

* **Communicate with your teammates.** If you might not be the only person working on a branch, talk to each other before rewriting commits.

* **Use `--force-with-lease` instead of `--force`.** The “with lease” option tells Git to check if the remote branch has changed since you last pulled. If it has, that’s a good sign that you may be overwriting someone else’s work.

If you’re working from a local copy of a branch when it’s force pushed by someone else, you can usually replay your local commits on top of the new history with `git pull --rebase`.

* [“--force considered harmful; understanding git's --force-with-lease” from the Atlassian Developers blog](#)

* [“Recovering from Upstream Rebase” from Git Reference](https://git-scm.com/docs/git-rebase#_recovering_from_upstream_rebase)

### Merging pull requests

While your branch is under review in a pull request, push changes you make in response to feedback as new commits on the same branch. The new commits will be added to the pull request, so reviewers will be able to see any changes that were based on their comments.

Once the pull request is approved, rewrite the history again to combine new commits with the originals, and force push the new history before merging. Delete the remote branch from GitHub after it’s merged.

