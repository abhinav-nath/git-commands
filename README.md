# git commands

- [Switch between GitHub accounts](./switch-between-github-accounts.md)
- [Push a new Git branch to a remote repo](#push-a-new-git-branch-to-a-remote-repo)
- [Undo local changes to a specific file](#undo-local-changes-to-a-specific-file)
- [Git Log](#git-log)
- [Create new branch in GitHub](#create-new-branch-in-github)
- [Push empty commit](#push-empty-commit)
- [Git Tags](#git-tags)
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

## Git Tags

Git has the ability to tag specific points in a repository’s history as being important.
Typically, people use this functionality to mark release points (v1.0, v2.0 and so on).

### Listing Your Tags

Just type `git tag` (with optional `-l` or `--list`):

```
$ git tag
v1.0
v2.0
```

You can also search for tags that match a particular pattern.

```
$ git tag -l "v1.8.5*"
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5
```

### Creating Tags

Git supports two types of tags: **lightweight** and **annotated**.

A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

#### Annotated Tags

Creating an annotated tag in Git is simple. The easiest way is to specify `-a` when you run the `tag` command:

```
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
```

The `-m` specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

You can see the tag data along with the commit that was tagged by using the `git show` command:

```
$ git show v1.4
tag v1.4
Tagger: Ben Straub <ben@straub.cc>
Date:   Sat May 3 20:19:12 2014 -0700

my version 1.4

commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```

That shows the tagger information, the date the commit was tagged, and the annotation message before showing the commit information.

#### Lightweight Tags

Another way to tag commits is with a lightweight tag. This is basically the commit checksum stored in a file — no other information is kept. To create a lightweight tag, don't supply any of the `-a`, `-s`, or `-m` options, just provide a tag name:

```
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
v1.5
```

This time, if you run `git show` on the tag, you don't see the extra tag information.
The command just shows the commit:

```
$ git show v1.4-lw
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```
