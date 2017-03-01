# Collaborating and getting fancy with Git

*by Eric Earl and Anders Perrone*

**GitHub** repository at **https://github.com/ericearl/fancy_git**

### A practical guide to some advanced features of Git version control

Many people are familiar with the basic Git commands and can easily create and track repositories for personal use, but when multiple people are working on a project that has active users it can be difficult to organize and easy to step on each other’s toes. In this presentation on intermediate Git usage we will be sharing our experience using Git to organize and collaborate on the development of a project that is currently in use.

We will cover Git features like [merging](https://www.atlassian.com/git/tutorials/git-merge), [rebasing](https://www.atlassian.com/git/tutorials/rewriting-history#git-rebase), [resolving conflicts with **KDiff3**](http://kdiff3.sourceforge.net/), [syncing (fetch/pull/push)](https://www.atlassian.com/git/tutorials/syncing), [pull requests](https://www.atlassian.com/git/tutorials/making-a-pull-request), and [branching](https://www.atlassian.com/git/tutorials/using-branches). This presentation will draw heavily from the tutorials featured on the [**Atlassian website**](https://www.atlassian.com/git) with special attention to the [collaborating](https://www.atlassian.com/git/tutorials/syncing) and [advanced tips](https://www.atlassian.com/git/tutorials/advanced-overview) sections.

This presentation's PDF was written from a README.md markdown file in [**Atom**](https://atom.io/) using the [**markdown-preview-plus**](https://atom.io/packages/markdown-preview-plus) and [**markdown-themeable-pdf**](https://atom.io/packages/markdown-themeable-pdf) packages. Each page will cover a topic by way of syntax-highlighted shell code.

## For starters

Here is an assumed minimal Git setup and the initial commit of this README for use with this presentation including the setup and push to **GitHub** (more on `git remote` and `git push` later).

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

# (EDITING README.md)

# staging and committing the README.md
git add README.md
git commit --message="Initial commit

A presentation in a README written by way of command history."

# (CREATING fancy_git REPOSITORY ON GitHub)

# setting GitHub as the "upstream" remote repository to simplify synchronizing
git remote add origin https://github.com/ericearl/fancy_git.git
git push --set-upstream origin master

```

Or you could just clone the [current repository on **GitHub**](https://github.com/ericearl/fancy_git).

```shell
git clone https://github.com/ericearl/fancy_git.git

```

<div class="page-break"></div>

## Branching

Branching is a way to either start development on a new feature/functionality or begin separate work within the same repository.  It is named after a tree concept which is why growing a new segment is called "branching".

```shell
# creating a new branch and beginning work on it
git branch devel-eric
git checkout devel-eric

# (EDITING README.md)

# staging and committing the edited README.md to the devel-eric branch
git add README.md
git commit --message="Fix typos and begin branching section

The first commit to the devel-eric branch, meant for further development by Eric.
Fixed typos were mainly bolding GitHub and capitalizing section titles for
consistent formatting."

```

## Synchronizing (fetch/pull/push)

You may have noticed the `git remote` command earlier.  That command is used to add a remote repository (on another server) to the local repository (on your computer).  This allows for communicating commit history changes between the repositories.

```shell
# this command adds "origin" as an alias for the github repository
git remote add origin https://github.com/ericearl/fancy_git.git

```

Once a remote repository is defined you can start using fetch, pull, and push.  `git fetch` is a way to see incoming changes that you can merge to your current branch with `git pull`.  When you're ready to send your changes to the remote repository you use `git push`.  Here is an example of common use pretending I am on the devel-eric branch where I am getting ready to synchronize my changes and there are no new changes to the master branch.

```shell
# (EDITING README.md)

# staging and committing the edited README.md to the devel-eric branch
git add README.md
git commit --message="Begin synchronizing section

Added a comment about the first git push command and started the synchronizing
section."

# fetching from the remote repository
git fetch
# viewing history to see nothing's changed
# "--graph" shows a graph on the left of the current tree
# "--decorate" is shorthand for "--decorate=short"
# "--oneline" is shorthand for "--pretty=oneline --abbrev-commit"
git log --graph --decorate --oneline

# deciding to pull all changes, told there are none
git pull

# ready to push, it's only this simple because "upstream" is already set
git push

```

## Resolving conflicts with KDiff3

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

After a change you may want to see the difference between the last commit and the new file.  Difference tools like KDiff3 make this easier.

```shell
git difftool

```

<div class="page-break"></div>

## Merging

At this point, I purposefully made a new master branch commit before merging the devel-eric branch changes so my development branch will need to merge into the master branch.

```shell
# (EDITING README.md)

# staging and committing the edited README.md to the devel-eric branch
git add README.md
git commit --message="Begin merging section

Beginning the merging section with an example merge from the devel-eric branch
to the master branch."

# pulling reveals a new master branch commit
git pull

# checkout the master branch to merge into and merge in the devel-eric branch
git checkout master
git merge devel-eric

# since there are conflicts that can't be resolved automatically
git mergetool

```

## Rebasing



## Pull requests
