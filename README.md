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

