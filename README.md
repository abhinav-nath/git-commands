# git commands

- [Switch between GitHub accounts](./switch-between-github-accounts.md)
- [Push a new Git branch to a remote repo](#push-a-new-git-branch-to-a-remote-repo)
- [Undo local changes to a specific file](#undo-local-changes-to-a-specific-file)
- [Git Log](#git-log)
- [Create new branch in GitHub](#create-new-branch-in-github)
- [Push empty commit](#push-empty-commit)
- [Git Tags](./git-tags.md)
- [Turn off auto CRLF](./turn-off-autocrlf.md)

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


## Undo local changes to a specific file

```
git restore filename.txt

or

git checkout -- filename.txt
```

## Git Log

```shell
git log -2   # show last 2 commits

git log -3   # show last 3 commits
```

## Create new branch in GitHub

![image](https://user-images.githubusercontent.com/48696735/185187270-adbe7c0f-e93c-4d78-8913-dd82484900a6.png)

## Push empty commit

```shell
git commit --allow-empty -m "Empty-Commit"

git push
```
