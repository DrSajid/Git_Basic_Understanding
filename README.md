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
8. [Push changes to remote repository](#push-changes-to-remote-repository)

---

## Git Installation

[Instructions on setting up Git](https://help.github.com/articles/set-up-git/)

## Basic Configuration

    git init (to initialized version control in current directory, I.e. git)
    git config –l <!--list git configuration-->
    git config –-global user.name="write_name"
    git config –-global user.email="write_email_address"
    git config –-global user.name   <!--Should print your name-->
    git config –-global user.email    <!--Should print your email address-->
    git config --global alias.logg "log --graph --decorate --oneline --all"         <!-- add alias ie. logg>
    git config --global alias.logg "log --graph --decorate --oneline --all --stat"  <!-- add alias ie. logs>

## Adding files for tracking

    git add –A (to add the all files in the working directory to staging)
    git status (To see the current status of files, modified/stagged)
    git restore --stagged filename.txt (to unstagged the file (I.e. filename.txt))
    git restore filename.txt (to restore the file to its previous commit level)
    git commit –m "write message you want to add" (to commite files from the staggging stage )

    Every git commit have "
    1.   Commit hash,
    2.   Auther name & Email,
    3.   Date,
    4.   Commit Message

## Adding files to ignore

touch .gitignore

Write in all the file extension _.txt _.doc etc, that you don’t want to be tracked, even folder paths. on Linux use "touch" command to create empty file, on window create it manually and name it ".gitignore"

## Review log

    git log
    git log --oneline
    git log --oneline --all --graph --decorate
    git log --stat
    git log --format=oneline <~--short, >
    git log --since=2022-06-15
    git log --since=2022-06-15 --until=2023-01-01
    git log -3               <!--last 3 commits>
    git log --author="NameofAuthor"
    git log --grep="Search_word"

## Branches

    git branch –v                    <!--List all the branches-->
    git branch testing               <!--will create branch with the name of testing-->
    git checkout testing             <!--will switch you to testing branch-->
    git branch –a                    <!--list all branches both lcoal & remote -->
    git branch –r                    <!--list all branches in the remote repository-->
    git branch –v                    <!--list all branches in the local repository-->
    git branch –va                   <!--branches and data-->
    git branch –vva                  <!--both local and remote repository info, and data-->
    git checkout –b testing          <!--will create branch with the name of testing and will checkout-->
    git branch testing               <!--will create branch with the name of testing-->
    git branch –d testing            <!--will delete the branch-->
    git branch –dr origin/testing    <!--will delete both local and remote branch-->
    git push –u origin testing       <!--will create new branch in remote repository and push changes-->
    git push                         <!--will push changes to remote repository-->
    git pull                         <!--will pull remote branch, fetch + merge-->
    git checkout –-track origin/branchName <!--will checkout the remote branch-->
    git push origin –-delete testing <!--will delete the branch form remote repository-->

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

## Push changes to remote repository

    git log --oneline 5 master                   <!-- Log of our local master branch -->
    git log --oneline 5 origin/master            <!-- Log of remote master tracking branch in local, not remote -->
    git diff origin/master..master --color-words
    git push origin master                       <!-- will push chages to origin from master -->
    git push                                     <!-- as it was tracing branch -->
    git fetch                                    <!-- will fetch changes from the remote repository, do it often -->
    git diff origin/master..master --color-words <!-- To see differene between local and fetch >
    git merge origin/master                      <!-- merge fetch updated to local branch of repository -->
    git pull                                     <!-- good at the start of the day, its fetch + merge changes from remote>
    git branch -r                                <!-- list all the remote branches>
    git branch non_tracking origin/non_tracking  <!-- to add non-tracking remote branch for local use>
    git checkout -b origin/my_untracked          <!-- will add untracked branch, and checkout -->
                                                 <!-- always fetch, merge and then push changes to remote repository>
    git push origin :my_untracked                <!-- will delete my_tracked branch from the remote>
    git push origin --delete my_untracked        <!-- will delete my_tracked branch from the remote>
