# :man_cook: Git Cookbook Guides

## Push a new local directory to GitHub
### Video
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

