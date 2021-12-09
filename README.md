# Git commands

## Local repository

```
git init
```

Creates a non-visible `.git` file, which tracks the changes of the repository.
Once this is created, another important (but not essential) Step is to define the name and Email address of the Author .

```
git config --global user.name "<name>"
git config --global user.email "<email>"
```

And use this command to check the current submitted information.

```
git config --list
```

If there are files containing personal data, or information, which is relevant just for the current machine, then include a `.gitignore` file, where the name or terminations of the files, which should not be synced, are written.

Next step is to put the files in the staging area with the command:

```
git add <filename>
```

or add them all and check status with:

```
git add .
git status
```

To remove single or all the files from the staging area, use:

```
git reset <filename>
git reset
```

Now is time to save the changes in the repository. For this use:

```
git commit -m "<message>"
```

To check which commitments where done, and who did it, use:

```
git log
```

To create a branch, check which other branches there are, and switch between them, use:

```
git branch <branchname>
git branch -a
git checkout <branchname>
```

Once in the branch, to update and merge the changes made to it to the master branch, it is important to add and commit the changes on the branch before merging with the master branch. Else it won't work.

To check the differences between two branches, use:

```
git diff <branch1>..<branch2>
```

## Remote repositories

