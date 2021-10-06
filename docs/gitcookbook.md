# :man_cook: Git Cookbook Guides

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