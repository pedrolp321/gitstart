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
git config -l
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
git log <(-p)> <(branch)>
```

Use -p to show more details.

To create a branch, check which other branches there are, and switch between them, use:

```
git branch <branchname>
git branch -a
git checkout <branchnam e>
```

Once in the branch, to update and merge the changes made to it to the master branch, it is important to add and commit the changes on the branch before merging with the master branch. Else it won't work.

To check the differences between two branches, use:

```
git diff <branch1>..<branch2>
```

If there has been changes in one of the branches, and it is of interest to update one of the branches, then go to the branch which is outdated and use:

```
git merge <updated_branch>
```

Once the branches are up to date, there is no need for the other branch. To delete a local or a remote branch use:

```
git branch -d <localbranch>
git push origin --delete <remotebranch>
```

To change the name of a branch, first checkout to the branch and change the name, then upload the the changes to the remote repository

```
git checkout <oldbranchname>
git branch -m <newbranchname>
```

If the `<oldbranchname>` has already been uploaded to the remote repository, to change it perform the next steps:

```
git push origin -u <newbranchname>
git push origin --delete <oldbranchname>
```
> <span style="color:orange">:red_circle:Check the first command</span>

## Remote repositories

To upload and push a local repository to Github, (making it into a remote repository) first create an empty project `<projectname>` on Github, then run the following commands while staying on the local repository path:

```
git remote add origin https://github.com/<github_username>/<projectname>
git push -u origin master
```
> <span style="color:orange">:red_circle:Check the second command</span>

> **Important:** After an update on Github from August 2021, password authentication service is no longer supported for command line (see [this site](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/) for detailed information). Nonetheless a guide how to overcome this issue is already [on-line](https://stackoverflow.com/questions/68775869/support-for-password-authentication-was-removed-please-use-a-personal-access-to). 
>
> A summary of the commands to follow (after creating a personal access `<token>` on Github) are:
>
> ```
> git config --global user.name "<github_username>"
> git config --global user.email "<github_email>"
> git config -l
> ```
>
> Once GIT is configured, we can begin using it to access Github. Example:
>
> ```
> git clone https://github.com/<github_username>/<projectname>
> ...
> Username for 'https://github.com' : <github_username>
> Password for 'https://github.com' : <token>
> ```
>
> Right after that, cache the given record in your computer to remembers the token:
>
> ```
> git config --global credential.helper cache
> ```
>
> If needed, anytime you can delete the cache record by:
>
> ```
> git config --global --unset credential.helper
> git config --system --unset credential.helper
> ```
>
> Now try to pull with `-v` to verify
>
> ```
> git pull -v
> ```

After updating the information in the local repository, it is time to uplad the changes to the remote repository. :exclamation:But first it is always usefull to check for changes in the remote repository:

```
git fetch
git log <(-p)> HEAD..origin/master
%git l
```

1. To update the remote repository list to the local one
2. To show the log entries between your last common commit and the origin's master branch.
3. test
