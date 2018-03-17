---
title: Just Make it Go Away - Breaking Things With Git
permalink: "/git-trouble/breaking-things-with-git"
layout: simple-class
header:
  overlay_image: cover.jpeg
  overlay_filter: rgba(46, 129, 200, 0.6)
next-page: "/git-trouble/git-scenarios"
facilitator: false
sidebar:
  nav: advanced
main-content: "\nYour well intentioned branch was supposed to introduce that awesome
  new feature, but after making a few commits, things aren't going as planned!   \n\nKeep
  in mind, all exercises expect you to have run the script to create files using the
  scripts found on the [Set Up Your Environment]({{site.baseurl}}/git-set-up) page.\n"
pushed: |
  This is what makes Git awesome! You can try new things and, when they don't work out, just get rid of them. First, ask yourself:

  > Is it all terrible? Or can I use some of it?

  ## Make it all go away!

  Ok, if you really mean it, we can get rid of the entire branch on the remote.

  1. First, let's go back to the `master` branch with: `git checkout master`
  1. Enter: `git push origin :BRANCH-NAME` or `git push --delete BRANCH-NAME` to delete the branch on the remote.
  1. Enter: `git fetch --prune` to delete the remote tracking branch.
  1. Enter: `git branch -D BRANCH-NAME` to delete the local copy of the branch.

  ## It isn't all bad

  If some of it can be salvaged, you can use the following approach:

  1. Ensure you are on the correct branch and enter: `git log --oneline`.
  1. Identify the SHA-1 hash for the last commit you want to keep. For this example, let's pretend files 1 and 2 are good, but we want to get rid of the rest, so grab the SHA-1 for "adding file 2".
  1. Enter: `git reset --hard SHA-1`, where SHA-1 is the SHA-1 hash for the commit where you created **file 2**.
  1. Type: `git status` and `ls`, notice that everything except files 1 and 2 are gone!
  1. Enter: `git push --force`.
didnt-push: "Well, you didn't push, that means no one else knows about your failed
  experiment. Use the following steps to get back to your happy place.\n\nFirst, ask
  yourself:\n\n> Is it all terrible? Or can I use some of it?\n\n## Make it all go
  away!\n\nSometimes the best way to fix a problem is to pretend it never happened.
  The easiest solution is to just delete the branch:\n\n1. Check out to the `master`
  branch with: `git checkout master`\n1. Enter: `git branch -D BRANCH-NAME` to delete
  the local copy of the branch.\n\n## It isn't all bad\n\nIf some of it can be salvaged,
  you can use the following approach:\n\n> If you want to see something kinda cool,
  open your local repository in a file browser (Finder, My Computer, etc.) and leave
  it to the side (but in view).\n\n1. Ensure you are on the correct branch and enter:
  `git log --oneline`.\n1. Identify the SHA-1 hash for the last commit you want to
  keep. For this example, let's pretend files 1 and 2 are good, but we want to get
  rid of the rest, so grab the SHA-1 for \"adding file 2\".\n1. Enter: `git reset
  --hard SHA-1`, where SHA-1 is the SHA-1 hash for the commit where you created **file
  2**.\n    If you have your file explorer open, you might have noticed something
  pretty cool happen!\n1. Type: `git status` and `ls`, notice that everything except
  files 1 and 2 are gone!  \n1. Enter: `git log --oneline`, all of the commits after
  **adding file2.md** are gone!\n\n## Wait, I Shouldn't Have Done That!!!\n\nOK, so
  that one rage-induced moment you 'accidentally' deleted that file because you just
  couldn't stand the sight of it. What if you could bring it back from the dead? You
  can:\n\n### Bring One File Back\n\n1. Enter: `git reflog`.\n1. Identify the SHA-1
  for the **adding file 6** commit.\n1. Enter: `git cherry-pick SHA-1` where SHA-1
  is the commit for \"Adding file 6\".\n1. Enter: `git log --oneline` and `ls` to
  see that file 6 and its commit are back.\n\n### Bring Them All Back\n\nAfter you
  took the dog for a walk, you realized where you were going wrong (fresh air works
  every time) and you want it all back. Don't worry, you can do that too:\n\n1. Enter:
  `git reflog`.\n1. Identify the SHA-1 for the **adding file 6** commit.\n1. Enter:
  `git reset --hard SHA-1` where SHA-1 is the commit for \"Adding file 6\".\n1. Enter:
  `git log --oneline` to see all of the commits are back. Notice the SHA-1 hashes
  of the commit - they match the original commits!\n"
show-me-how: 
tell-me-why: "\n## Reflog\nReflog is a more powerful version of `git log`, it records
  every commit HEAD has pointed to. HEAD is simply a pointer that represents the commit
  you are currently \"checked out\" to.\n\nIn most cases, you will be checked out
  to a branch, but you can also check out to any commit or tag in your history. When
  you are checked out to something other than a local branch, you are in what's called
  a **detached head** state. This is also recorded in the reflog.\n\nThere are a few
  things that you should know about `reflog`, such as:\n\n1. `reflog` is **local**
  only, so, your other collaborators are not going to be able to find files you deleted
  in their `reflog`s.\n1. `reflog` only displays commits for a limited time:\n   -
  30 days: 'Unreachable' objects, aka commits or modifications that were made to a
  branch that no longer exists.\n   - 90 days: 'Reachable' objects, aka commits or
  modifications that were made to a branch that still exists.\n\n## Reset\nFor more
  information about `reset`, check out the 'Tell me why' section in the [Too Many
  (small) Commits]({{site.baseurl}}/too-many-commits) scenario.\n\n## Cherry-pick\nFor
  more information about `cherry-pick`, check out the 'Tell me why' section in the
  [Committed to the Wrong Branch!]({{site.baseurl}}git-commit-wrong-branch) scenario.
  \ \n"
---

