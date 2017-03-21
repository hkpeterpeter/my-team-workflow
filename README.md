
### Key ideas

- Keep the master branch as a stable release branch
- Each team member will create a new feature branch (e.g. feature-XXX)
- Sync with the master branch and resolve conflicts
- Commit your changes and publish to the feature branch 
- Send a pull request to the master branch
- Code review and merge OR reject the changes

### Step 1 - Team member clone the shared repository

```
git clone [Repo URL]
```

### Step 2 - Create a feature branch

`git checkout -b` is used to create a new branch

```
git checkout -b [branch-name]
```

`git branch` is used to query the current branches

```
git branch 
```

`git checkout` is used to switch different branches
```
git checkout [branch-name]
```

### Step 3 - Development the feature and commit (locally)

After your develope the feature, you should:

```
git add .                      # stage files (new, modified, deleted, equivalent to ``git add -A``)
git commit -m "[Comment]"      # write a reasonable commit log    
```

### Step 4 - Sync with the master branch and resolve conflicts

The following steps will first pull the changes from the remote repository in the master branch. After that, the local master branch should be synchorized. Then, we switch to the feature branch and finally merge from the local master branch

```
git checkout master            # switch to the local master
git pull                       # pull from remote master
git checkout [branch name]     # switch to the feature branch
git merge master               # merge diff from master
```

Please don't push to the remote repository if some errors happen

### Step 5 - Commit to your feature branch and push to the remote repo

If there are no conflicts after syncing with the master branch, we can push the changes to the remmote repo and prepare for a pull request

```
git checkout [branch name]      # switch to the feature branch
git push                        # push from local to remote feature branch
```

If it is the first time to push from local to remote, additional parameters are needed:

```
git push --set-upstream origin [branch name]
```

### Step 6 - Pull request and Merge

1. Switch to the GitHub web interface
2. Select the `branch name` you would like to merge to master
3. Click `New pull request` button
4. Type in the pull request title and comments
5. Review commit log messages and file changes
6. Discussion. If needed, the feature branch maintainer should make changes and commit to the feature branch. Ideally, the pull request will be updated.
7. Approve/Reject the merge

### Step 7 - [Optional] Delete local and remote branch

Once the branch is merged, we may consider to delete the feature branch if needed

Delete a local branch:

```
git branch -d [branch name]
```

Delete a remote branch (or use a web interface to delete)

```
git push origin --delete [branch name]
```
