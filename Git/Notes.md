
# Helpful Git Commands 

```bash
    # Run this command to make your script executable
    git config --global core.autocrlf false
    git update-index --chmod=+x pull-commit-push.sh
```




```bash


    # Pull changes from Azure DevOps
    git pull azure main  

    # Commit everything locally that has changed
    git add .
    git commit -m "Committing often is good practice"

    # Push to both remotes when making local changes
    git push origin main
    git push azure main

```


git update-index --chmod=+x git-sync.sh

---


**Local Repository** (VS Code):

```bash
    # Push to both remotes when making local changes
    git push origin main
    git push azure main
```

## Synchronization Flow

When changes occur in different places:
1. **Power Platform** changes will automatically sync to Azure DevOps
2. **Local Changes** (VS Code) need to be pushed to both remotes
3. **Azure DevOps** (primary) will receive changes from both Power Platform and local development
4. **GitHub** serves as a mirror/display repository

## Best Practices for Local Development

1. Always pull before making changes:
```bash
git pull azure main
```

2. When pushing local changes:
```bash
# First push to Azure (primary repository)
git push azure main
# Then push to GitHub (mirror)
git push origin main
```

**Important**: Since Power Platform will be making direct commits to Azure DevOps, make it a habit to pull from Azure before starting any local development work to avoid conflicts.

Citations:
[1] https://exalate.com/blog/azure-devops-github-integration/
[2] https://stackoverflow.com/questions/61229061/how-to-synchronize-github-and-azure-devops-repository
[3] https://www.reddit.com/r/github/comments/ad1sl4/can_i_sync_my_azure_devops_repo_to_github/
[4] https://learn.microsoft.com/en-us/azure/devops/cross-service/github-integration?view=azure-devops

---

Azure DevOps repository (primary)
Power Platform environment with Git integration (where most changes will occur)
GitHub repository (mirror/display)

```bash

    git push origin azure
    git push azure main

    git fetch origin azure
    git fetch azure origin

    git remote show origin
    git remote show azure

```




The command `git update-index --chmod=+x git-sync.sh` sets the executable permission flag for your shell script in Git's index, making it executable on Unix-based systems[1][4].

## What It Does

- Modifies the file permissions from `644` (non-executable) to `755` (executable)[1]
- Stages this permission change in Git's index
- Ensures the script can be executed when checked out on Unix-based systems[1]

## Technical Details

Before running the command, the file permissions would show as:
```bash
100644 (file hash) git-sync.sh
```

After running the command and committing, it changes to:
```bash
100755 (file hash) git-sync.sh
```

This is particularly important when developing on Windows because Windows doesn't use the same permission system as Unix-based systems, but Git needs to maintain these permissions for cross-platform compatibility[4].

Citations:
[1] https://www.augmentedmind.de/2020/05/10/commit-executable-shell-scripts-with-git/
[2] https://git-scm.com/docs/git-update-index
[3] https://git-scm.com/docs/git-update-index/2.1.4
[4] https://dev.to/ku6ryo/chmod-x-by-git-on-windows-5fjd