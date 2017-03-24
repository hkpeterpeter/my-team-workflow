## Navigation
- [Suggested team workflow](#suggested-team-workflow)
- [Restore from previous commit](#restore-from-previous-commit)
- [Delete files from Git repository](#delete-files-from-git-repository)

## Suggested team workflow
**centralized workflow + feature branching** should be used for a small dev team
- Team members should be the contributors with push permission to the centralized repo
- Keep the master branch as a stable release branch
- Each team member will create a new feature branch (e.g. feature-XXX)
- Sync with the master branch and resolve conflicts
- Commit your changes and publish to the feature branch 
- Send a pull request to the master branch
- Code review and merge OR reject the changes

Further references about different workflows:
- [git-scm: Distributed Workflows](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [atlassian: Comparing workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)

### Step 1 - Clone the repository
```sh
git clone [Repo URL]
```

### Step 2 - Create a feature branch
Create a new branch
```sh
git checkout -b [branch-name]
```
Query the current branches 
```sh
git branch 
```
Switch to another branch
```sh
git checkout [branch-name]
```

### Step 3 - Feature development and commit (locally)
```sh
git add .                      # stage files (new, modified, deleted, equivalent to ``git add -A``)
git commit -m "[Comment]"      # write a reasonable commit log    
```

### Step 4 - Sync with the master branch and resolve conflicts
```sh
git checkout master            # switch to the local master 
git pull                       # pull from remote master branch
git checkout [branch name]     # switch to the feature branch
git merge master               # merge diff from master
```
Please resolve conflicts and errors before pushing to the remote repo

### Step 5 - Push to the remote feature branch

If it is the first time to push from local to remote, additional parameters are needed:
```sh
git checkout [branch name]                     # switch to the feature branch
git push --set-upstream origin [branch name]   # create a new feature branch in the upstream and push
```

Otherwise:
```sh
git checkout [branch name]                     # switch to the feature branch
git push                                       # push from local to remote feature branch
```

### Step 6 - Pull request and Merge
1. Switch to the GitHub web interface
2. Select the `branch name` you would like to merge to master
3. Click `New pull request` button
4. Type in the pull request title and comments
5. Review commit log messages and file changes
6. Code review. If needed, the feature branch maintainer should make changes and commit to the feature branch. The pull request will be automatically updated.
7. The master branch maintainer approves/rejects the merge, or keep the discussing the issues via the pull request

### Step 7 - [Optional] Delete local and remote branch

Once the branch is merged, we may delete the feature branch:

Delete a local branch:
```sh
git branch -d [branch name]
```

Delete a remote branch 
```sh
git push origin --delete [branch name]
```
Alternatively, you can use a web interface to delete a remote branch

## Restore from previous commit

### Step 1 - Query the commit log and unique commit id
```sh
git log
```
The commit ids can also be found via the web interface at GitHub
### Step 2.1 - Temporary detach and view the commit 
```sh
git checkout [commit id]      # temporary detach and view
git checkout [branch name]    # switch to a branch, the temporary view is removed
```
### Step 2.2 - Create a new branch based on a previous commit
```sh
git checkout -b [new branch name] [commit id]   # create a new branch from an old commit
```

Other advanced operations:
[StackOverflow: How to revert Git repository to a previous commit?](http://stackoverflow.com/questions/4114095/how-to-revert-git-repository-to-a-previous-commit)

## Delete files from Git repository

### Step 1 - Remove and commit
If you need to remove a file from both git repo and local filesystem:
```sh
git rm [filename]
```
If you only want to remove a file from git repo (and keep the local copy):
```sh
git rm --cached [filename]
```

### Step 2 - Push to the remote repo
```sh
git push
```
