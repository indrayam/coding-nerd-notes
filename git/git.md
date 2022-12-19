# Git Skills to Learn

## Git Internals
- 3 Objects: Commit, Tree, and Blobs
- 3 States: Working Directory, Index and Object Storage

## Local Version Control Git Commands (git init, git add, git rm, git commit, git diff)
- 3 Objects: Commit, Tree, and Blobs
- 3 States: Working Directory, Index and Object Storage
- Init repo or Clone repo
    + Change default branch name from `master` to `main`
- Add/Stage changes
- Remove files accidentally added
- Commit
- Create a branch and have it track a remote branch
- Switch between branches
- View branches and their associations with remote branch
- See what's the difference between 
    - Your working directory and staged changes
    - Staged changes and a commit
    - Changes between two commits
- Show what happened (name of the files that was changed or what was specifically changed) in a commit
- See compact view of changes for a commit
- See exactly what changed in a commit for a specific file
- Compare changes between commits
- Compare changes between branches

## Distributed Version Control Git Commands (git remote, git branch, git fetch, git merge, git rebase, git push)
- Add remote(s)
- View remote(s)
- Setup to track local branch with a remote branch
- View branches and their associations with remote branch
- Get updates without merging
- Merge (with Fast Forward or actual Merge Commit)
- Rebase changes
- Push changes to remote
- Create pull request
- Pull down pull request into a local branch
- Delete local branch and remote branch that it is tracking

## Typical Distributed Development Workflow with Git (Git aliases - git sync, git update, git squash)
- Create a branch and set it to track remote branch
- Perform updates  to pull down any new changes that your teammates might have pushed while you were working locally
- Always pull in changes from the integration branch (main/develop/integration) that you branched off of
    - git sync
    - git update
    - git squash
## Fixing Changes (git restore, git reset)
Source: [Turn around your Git mistakes in 17 ways](https://dev.to/smitterhane/turn-around-your-git-mistakes-in-17-ways-2mn1)
- Change last commit message
- Change the things that should be committed as part of the last commit
- Modify an old commit message
- Remove a file/folder that got accidentally committed 
- Discard all changes in your working directory
- Discard all changes made to a particular file
- Restore a file to an old version (from an older commit)
- Restore a deleted file
- Discard all changes in your local repo to exact state in remote
- Delete Untracked files and folder
- Rewind/Undo an erroneous commit
- Rollback to an older version
- Revert a particular file back to an earlier version
- Switch a commit to a different branch
- Resurrect a deleted branch
- Undo a Git Merge
- Delete an old commit
- Edit an old commit and add new changes
## Advanced Git Commands
- squash commits using rebase
- reflog
- worktree
- bisect
- cherry-pick
- restore
- stash
- sparse-checkout
- shallow clone 

