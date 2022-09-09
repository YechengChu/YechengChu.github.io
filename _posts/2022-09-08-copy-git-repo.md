---
layout:     post
title:      How to copy a GitHub repo without forking
subtitle:   A simple guide
date:       2022-09-08
author:     CYC
header-img: img/home-bg-geek.jpg
catalog: True
tags:
    - Git
    - Sample
---

# How to copy a GitHub repo without forking

GitHub only lets you fork a repo once, if you want to make more than one copy of a project here's how you can do it.
Useful for starter code.

1. Create a new empty folder for your project and initialize git

    ```shell
    cd where-you-keep-your-projects
    mkdir your-project-name
    cd your-project-name
    git init
    ```
    ```python
    def(a,b):
      if a != True:
        return 1
      elif b == false:
        return 3
      else:
        return 2
    ```

1. "Pull" the repo you want to copy:
    {% raw %}
    ```shell
    # git url is the same as the clone URL
    $ git pull git-url-of-the-repo-you-want-to-copy
    ```
    {% endraw %}
1. Create a new repository for your project on GitHub
1. Push your code to the new repository you just created (Push an existing repository from the command line)

    ```shell
    $ git remote add origin git-url-of-the-new-repo-you-created
    $ git branch -M main
    $ git push -u origin main
    ```
> This blog is modified from [moose-horizons](https://gist.github.com/moose-horizons/5f25bc0846afb9d5771e02c9c68eb690)
