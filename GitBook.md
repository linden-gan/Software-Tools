## Git 2021
- git clone [git@...]: clone repo
- git status: examine current status (updated or not)
- git stage readme.md : prepare change?
- git commit -m "commit message"
- git push: push to remote branch

## Git 2023
- Remote: remote repo online usually named `origin`, in contrary to local
  - `git remote` to list all remote repo
- Branch:
  - local non-tracking branch: local "dummy" branch, can't push or pull from remote branch
    - `git branch <name>` to create
    - `git push origin <name>` to push local branch to remote
  - local tracking branch: track/connect with a remote tracking branch, so can push and pull without specifying which remote branch
    - `git branch --track <remote_branch_name>` to create
  - remote tracking branch: still on local machine, a reference/cache to remote branch
  - remote branch: branch on remote
    - `git remote show origin` to show remote config and branches
