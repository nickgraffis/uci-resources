# :man_cook: Git Cookbook Guides

## How to set up your class repo and homework repos

### Instructions
I would set up my class repo and all of my projects and homework inside of a directory called `bootcamp`. 
So I would have something that looks like this _(⑆ will represent a git repository)_:
```
bootcamp
└───⑆uci-irv-virt-fsf-pt-09-2021-u-c
│   │
│   └───..
│   
└───⑆homework_1
│   │
│   └───..
│ 
└───⑆homework_2
│   │
│   └───..
...etc
```

::: danger
You don't want to have git repos inside other git repos. These are called [submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).
:::

### Using branches inside of your class book repo
If you want to make changes inside of your class repo, I would make them on a seperate branch.
```
git checkout -b bootcamp_homework_1
```

This way you can always go back to the original branch and `git pull` the new content, without messing up the changes you've made.

::: info
If you've already made changes to your `master` branch of the class repo. Check out this [tutorial](#saving-changes-for-later-with-git-stash) to see how to save these changes, and put them into a new branch.
:::
## Push a new local directory to GitHub
### Video 
<p></p>
<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/b07d4d7458a749eda600403e71e2ef7e" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

### Instructions
The scenario here is that we have a local directory, that we want to push up to GitHub, but it isn't current a git directory. So how do we connect our current directory to a git repository?

1. Create a new git repository inside the current directory
```
git init
```

2. Add all the files in the current directory to the git repository
```
git add .
```

3. Commit the changes
```
git commit -m "Initial commit"
```

4. Create the remote repository on GitHub and copy the uri

5. Add the remote repository to the git repository
```
git remote add origin <uri copied from github>
```

6. Push the changes to GitHub
```
git push --set-upstream origin master
```

## Handeling Merge Conflicts
### Video
<p></p>
<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/342b6cbb16004d5fb29b94cf39f12364" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

### Instructions
Lets say that someone you are working with has made changes to file A. You, without knowing that they were making changes to file A, have also made changes to file A. Now when you `git push` your changes, you will get an error saying that:
```
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

1. Fix this by first pulling from the branch you and your teammate are working on
```
git pull
```

2. Take a look at your merge conflicts inside of file A:
```
<<<<<<< HEAD
this is my change
=======
this is another change
>>>>>>> 872659285<random hash that represents the remote commit>
```

3. Resolve the merge conflicts by deleting the info that you don't want to keep:
```
this is another change
```
_We kept the remote change here_

4. Now you can add, commit, and push your changes with the conflict resolved
```
git add .
git commit -m "Resolved merge conflicts"
git push
```

## Saving changes for later with `git stash`

### Video
<p></p>
<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/5128b4ccb0cf424fb020747ff811b296" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

## Instructions
In this demo, you've made some changes to a branch that you didn't want those changes to be in. So you want to save those changes for later and put them in a new branch.

1. Go to your class book on the `master` branch. And make some changes
2. Use `git stash` to save those changes for later.
```
git stash
```
3. Create a new branch and then use `git stash pop` to get the most recent changes you've stashed into your new branch.
```
git checkout -b newbranch
git stash pop
```

## Changing a commit message & using Vim :ghost:

::: warning
This guide will only help you change your most recent commit message.
:::

### Video
<p></p>
<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/7782d71f19414220996aa72c468daa8e" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

## Instructions
You may want to change a commit message, here is how.

1. Make some changes and then commit them with a message.
2. Use the `--amed` flag to change the commit message.
```
git commit --amend
```
3. The Vim editor will open up in your terminal. Hit `i` to start inserting and change your commit message. Vim will look like this:
```
added emojis to the readme file: 🧛🏻  <200d>♂️💯

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Sat Oct 9 15:15:27 2021 -0700
#
# On branch master
# Your branch is up to date with 'origin/master'.
#
# Changes to be committed:
#       modified:   README.md
#
~
~
~
~
~
~
~
~
~
~
~
"~/Desktop/bootcamp/test-portfolio/.git/COMMIT_EDITMSG" 13L, 362B
```

4. Now hit `esc` to enter Vim's command mode. Then `:wq` to save the file and exit Vim.

5. You've changed your commit message! :tada:

6. Optionally, if you've already pushed that commit, you can then use `git push --force-with-lease` to force push your changes to GitHub.

## Change default branch names from `master` to `main`
Because GitHub is now using the `main` branch name as the default, it would be easiser for us to have our local git use the same default name.
### Instructions
1. You can check out your current git configs by running:
```
git config --list
```
You'll probably get something like this in response: 
```
user.name=Nick Graffis
user.email=nicholasgraffis@gmail.com
```

2. We want to create a template for our initial git repositories when we create them. GitHub is already doing this when we make repositories on github.

3. Make a directory for our git templates
```
mkdir ~/.git-template && cd .git-template
```

4. Create a file inside called `HEAD` and open it with a default text editor
```
touch HEAD && code HEAD
```

5. Add the following text to the file:
```
ref: refs/heads/main
```

6. Update your config `init.templateDir` to point to our new template
```
git config --global init.templateDir ~/.git-template
```