# Git_Basic_Understanding

Basic understanding of git for daily use

### **Table of Contents**

1. [Git Installation](#git-installation)
2. [Basic Configuration](#basic-configuration)
3. [Adding files for tracking](#adding-files-for-tracking)
4. [Adding files to ignore](#adding-files-to-ignore)
5. [Review log](#review-log)
6. [Branches](#branches)
7. [Remote repo](#remote-repo)

---

## Git Installation

[Instructions on setting up Git](https://help.github.com/articles/set-up-git/)

## Basic Configuration

## Adding files for tracking

## Adding files to ignore

## Review log

## Branches

### To compare two branches:

    git diff branch_a..branch_b

    git diff branch_a..<tree-ish>

    git diff --color-words branch_a..branch_b

### To check which branches are merged in current branch:

    git branch --merged

    git branch --no-merged

### To rename branch:

    git -mv old_branch_name new_branch_name

    git -mv new_branch_name <!-- (rename the current branch) -->

### to delete branch:

    git branch -d branch_a

    git branch -D brnach_a  <!-- (force delete with no check) -->

## Remote repo

We can `push` local repository changes to remote server to have similar status. Similarly if some pushed update in the remote server, we can easily `fetch` that changes in our local repo.

### To check remote exist in current project

    git remote

### To add remote

    git remote add origin  <!-- url to your github repo -->

### To get remote repo status

    git remote
    git remote -v
    git remote get-url origin
    cat ./git/config

### To remove remote repository:

    git remote rm origin

### To push our local master branch to remote:

    git push -u origin master          <!-- -u add the tracking option, recommended -->
    git branch -u origin/br_a br_a     <!-- to add tracking to br_a branch -->
    git branch -u-unset-upstream br_a  <!-- to remove br_a from tracking -->
    git help branch                    <!-- to get more option about branches -->

### To get list of all branches:

    git branch -a  <!-- all branches local & remote -->
    git branch -r  <!-- list only remote branches -->
    git branch     <!-- list local branches -->

    ls  -la .git/refs/remotes
    cat .git/refs/remotes/origin/HEAD  <!-- ref to the remote -->
    cat .git/refs/remotes/origin/main  <!-- tree-ish of remote -->
