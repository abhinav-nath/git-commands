### Commands to set Beyond Compare 4 as difftool and mergetool for git

```
git config --global diff.tool bc4
git config --global difftool.bc4.cmd "\"C:/Program Files/Beyond Compare 4/BCompare.exe\" \"\$LOCAL\" \"\$REMOTE\""
git config --global difftool.prompt false

git config --global merge.tool bc4
git config --global mergetool.bc4.cmd "\"C:/Program Files/Beyond Compare 4/BCompare.exe\" \"\$LOCAL\" \"\$REMOTE\" \"\$BASE\" \"\$MERGED\""
git config --global mergetool.bc4.trustExitCode true
```