# :cat: :octopus: Git Guide

## :man_cook: Git Cookbook Guides
Check out the [cook book](/gitcookbook) for videos and guides for common issues.

## `> git init`
The `init` command creates a new repository in the current directory.

_Use it when you already have a directory you've been working on, and you want to turn it into a git repository._

**Command**
```
git init
```

**Response**
```
Reinitialized existing Git repository in /path/to/repo/.git/
```
## `> git status`
The `status` command shows the status of the current repository. What files are being tracked or not tracked, and what files have been modified or not.

_Use it to determine what is going on inside your git repository._

**Command**
```
git status
```

**Response**
```
On branch main

No commits yet

Untracked files:
  (use "git add file..." to include in what will be committed)
  index.html

nothing added to commit but untracked files present (use "git add" to track)
```

## `> git add`
The `add` command adds files to the staging area. You can add all files in the current directory with `git add .`. Or you can add specific files with `git add file1 file2`.

_Use it to add files to the staging area._

## `> git commit`
The `commit` command commits the changes in the staging area to the repository. You can commit all the changes in the staging area with `git commit -a`. Or you can commit specific files with `git commit -a file1 file2`. You can also commit with a message with `git commit -m "message"`.

_Use it to commit changes to the repository._

## `> git commit -am "message"`
This is the same as 
```
git add .
git commit -m "message"
```

## `> git push`
The `push` command pushes the changes in the staging area to the remote repository. You can push all the changes in the staging area with `git push`. Or you can push specific files with `git push file1 file2`.

## `> git pull`
Pull changes from the current branch remote repository to the current branch local repository.
If you want to get changes from another branch. You can use `git pull origin <branch>`.

## `> git clone`
This creates a repository in the current directory. So don't use this command if you want the current directory you are in, to be a git repository. If you want your current directory to be a git repository. Use `git init` instead.

## `> git remote add origin <origin_uri_from_github>`
This adds a remote repository to the current repository.

_Use this after you have created a git repo locally from a directory. And then you created a remote repo on github and you want to combine them._

## `> git remote -v`
Check what your remote repository is. It should look something like this:
```
origin	https://github.com/nickgraffis/uci-resources.git (fetch)
origin	https://github.com/nickgraffis/uci-resources.git (push)
```

## `git checkout <branch>`
Switch from your current branch, to a different branch.

## `> git checkout -b new-branch`
Create a new branch with the name of new-branch

## `--force`
This flag can be added at the end of things like `git push` or `git pull` to force the command to run.

## `> git stash`
Stash some changes you've made in your current working directory away.

_Use this when you want to save the changes you've made, but you don't want to commit them and you want to pull from another branch first and your getting errors that your branch is not clean_