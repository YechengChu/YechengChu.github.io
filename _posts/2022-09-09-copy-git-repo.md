---
layout:     post
title:      How to copy a GitHub repo without forking
subtitle:   A simple guide
date:       2022-09-09
author:     CYC
header-img: img/home-bg-geek.jpg
catalog: True
tags:
    - Git
    - Tool
---

> This blog is modified from [moose-horizons](https://gist.github.com/moose-horizons/5f25bc0846afb9d5771e02c9c68eb690)

# How to copy a GitHub repo without forking

GitHub only lets you fork a repo once, if you want to make more than one copy of a project here's how you can do it.
Useful for starter code.

1. Create a new empty folder for your project and initialize git

    ```shell
    $ cd where-you-keep-your-projects
    $ mkdir your-project-name
    $ cd your-project-name
    $ git init
    ```

1. "Pull" the repo you want to copy:

    ```shell
    # git url is the same as the clone URL
    $ git pull git-url-of-the-repo-you-want-to-copy
    ```

1. Create a new repository for your project on GitHub
1. Push your code to the new repository you just created (Push an existing repository from the command line)

    ```shell
    $ git remote add origin git-url-of-the-new-repo-you-created
    $ git branch -M main
    $ git push -u origin main
    ```
