# git commands

- [Switch between github accounts](./switch-between-github-accounts.md "Switch between github accounts")
- [Push a new Git branch to a remote repo](#push-a-new-git-branch-to-a-remote-repo "Push a new Git branch to a remote repo")
- [Turn off auto CRLF](./turn-off-autocrlf.md "Turn off auto CRLF")

---

## Push a new Git branch to a remote repo

1. Create and switch to a new local branch to be pushed to the remote GitHub repo:

   ```shell
   git switch -c new-branch
   ```

2. `git branch -a` will verify that the new Git branch to be pushed to the remote GitHub repo was indeed created locally.

3. Commit the changes to this new branch.

4. Push the changes to the new branch:

   ```shell
   git push --set-upstream origin new-branch
   ```

   With a new branch created, the `--set-upstream` switch must be run the first time a push is performed.
   This step tells the new branch which remote repository to use every time it synchronizes its commit history.

   Failure to perform the `--set-upstream` step will causes pushes of the new branch to the remote repo to fail with the following error:

   > fatal: The current branch has no upstream branch
