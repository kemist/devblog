---
title: vi Basics
permalink: "/windows/vi-basics"
layout: simple-class
header:
  overlay_image: cover.jpeg
  overlay_filter: rgba(46, 129, 200, 0.6)
next-page: "/windows/configure-editors"
sidebar:
  nav: windows
main-content: |
  If you haven't defined a `core.editor` for Git to use, it defaults to using [vi](https://en.wikipedia.org/wiki/Vi) for commit messages, interactive rebases, and other commands that require user input. Before we identify how to setup a `core.editor` you might need the following information:

  ## How the *$#@& do I get out of vi?
  First, don't worry, everyone gets stuck in vi. Second, it is _really_ easy to get out of vi using the following:

  ### Saving the Commit
  1. Press the `esc` key.
  1. Enter `:wq` to save (or `w`rite) your commit message.

      > You can enter `:q` to `q`uit the editor without saving your commit message.

  ### Discarding the Commit
  1. Press the `esc` key.
  1. Enter, `:q!`. This will discard the commit without discarding your changes. If you want to double check that your changes still exist, enter `git status` and your changes will still be displayed.

  You have successfully gotten out of vi, nicely done.
---

