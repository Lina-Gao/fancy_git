# Collaborating and getting fancy with Git

*by Eric Earl and Anders Perrone*

**GitHub repository** at **https://github.com/ericearl/fancy_git**

### A practical guide to some advanced features of Git version control

Many people are familiar with the basic Git commands and can easily create and track repositories for personal use, but when multiple people are working on a project that has active users it can be difficult to organize and easy to step on each other’s toes. In this presentation on intermediate Git usage we will be sharing our experience using Git to organize and collaborate on the development of a project that is currently in use.

We will cover Git features like [merging](https://www.atlassian.com/git/tutorials/git-merge), [rebasing](https://www.atlassian.com/git/tutorials/rewriting-history#git-rebase), [resolving conflicts with **KDiff3**](http://kdiff3.sourceforge.net/), [syncing (fetch/pull/push)](https://www.atlassian.com/git/tutorials/syncing), [pull requests](https://www.atlassian.com/git/tutorials/making-a-pull-request), and [branching](https://www.atlassian.com/git/tutorials/using-branches). This presentation will draw heavily from the tutorials featured on the [**Atlassian website**](https://www.atlassian.com/git) with special attention to the [collaborating](https://www.atlassian.com/git/tutorials/syncing) and [advanced tips](https://www.atlassian.com/git/tutorials/advanced-overview) sections.

This presentation's PDF was written from a README.md markdown file in [**Atom**](https://atom.io/) using the [**markdown-preview-plus**](https://atom.io/packages/markdown-preview-plus) and [**markdown-themeable-pdf**](https://atom.io/packages/markdown-themeable-pdf) packages. Each page will cover a topic by way of syntax-highlighted shell code.

## For starters

Here is an assumed minimal Git setup and the initial commit of this README for use with this presentation.  (more on `git remote` and `git push` later)

```shell
# setting up the ~/.gitconfig file
git config --global user.name "Eric Earl"
git config --global user.email "earl@ohsu.edu"
git config --global diff.tool kdiff3
git config --global merge.tool kdiff3

# creating a repository folder and beginning the README.md
mkdir fancy_git
cd fancy_git
git init
touch README.md

# (EDITING)

# staging and committing the README.md
git add README.md
git commit --message="Initial commit

A presentation in a README written by way of command history."

# (CREATING fancy_git REPOSITORY ON GitHub)

git remote add origin https://github.com/ericearl/fancy_git.git
git push --set-upstream origin master
```

Or you could just clone the [current repository on GitHub](https://github.com/ericearl/fancy_git).

```shell
git clone https://github.com/ericearl/fancy_git.git

```

<div class="page-break"></div>

## branching



## synchronizing (fetch/pull/push)



## resolving conflicts

Meanwhile, back on the master branch...

```shell
# (EDITING)

# staging and committing the README.md
git add README.md
git commit --message="Begin conflict section

Beginning the conflict section with details of the master branch activity."

# sending the changes along o GitHub
git push

```

<div class="page-break"></div>

## merging



## rebasing



## pull requests
