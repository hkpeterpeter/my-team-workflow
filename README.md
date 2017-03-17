## Recommended team workflow

Git is a version control software. It is just a tool, and we need to agree on a team workflow in order to use this tool effectively. There are 2 common workflows in Git/GitHub:

- Fork and pull approach: Suitable for medium to large scale project
- Shared repository and feature branch approch: Suitable for a small team project

## Shared repository and feature branch

### Key ideas

- Keep the master branch as a stable release branch
- Each team member will have push/pull access to a shared repo
- Create a feature branch (e.g. feature-XXX)
- Develop the feature on the branch "feature-XXX"
- Sync with the master branch and resolve conflicts
- Commit your changes and publish to the feature branch 
- Send a pull request to the master branch
- Code review and merge / reject the changes

### Step 1 - Team member clone the shared repository

```
git clone [Repo URL]
```

### Step 2 - Create a feature branch

`git checkout -b` is used to create a new branch

```
git checkout -b [feature-branch-name]
```

`git show-branch` is used to query the names of the branches

```
git show-branch
```

`git checkout` is used to switch different branches

### Step 3 - Sync with the master branch and resolve conflicts

The following steps will first pull the changes from the remote repository in the master branch. After that, the local master branch should be synchorized. Then, we switch to the feature branch and finally merge from the local master branch

```
git checkout master            # switch to the local master
git pull                       # pull from remote master
git checkout [feature-branch]  # switch to the feature branch
git merge master               # merge diff from master
```

### Step 4 - Commit to your feature branch and push to the remote repo

If there are no conflicts after syncing with the master branch, we can push the changes to the remmote repo and prepare for a pull request

```
git checkout [feature-branch]   # switch to the feature branch
git push                        # push from local to remote feature branch
```

### Step 5 - Pull request


1. Switch to the GitHub web interface
2. Select the `feature-branch`
3. Click `New pull request` button
4. Type in the pull request title and comments
5. Review commit log messages and file changes
6. Discussion. If needed, the feature branch maintainer should make changes and commit to the feature branch. Ideally, the pull request will be updated.
7. Approve/Reject the merge