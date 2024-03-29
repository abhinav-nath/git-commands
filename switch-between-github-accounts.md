### Switch between github accounts


1. Create separate ssh keys for personal and work accounts

   ```shell
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   ```shell
   -rw-------  1 abhinavnath  staff  419 Aug 17 16:23 id_ed25519
   -rw-r--r--  1 abhinavnath  staff  111 Aug 17 16:23 id_ed25519.pub
   -rw-r--r--  1 abhinavnath  staff  802 Aug 17 18:50 known_hosts
   -rw-------  1 abhinavnath  staff  411 Sep 13 22:55 id_ed25519_personal
   -rw-r--r--  1 abhinavnath  staff  103 Sep 13 22:55 id_ed25519_personal.pub
   -rw-r--r--  1 abhinavnath  staff  240 Sep 13 22:56 config
   ```


2. ssh config file

   ```shell
   # Work account - the default config
   Host github.com
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_ed25519

   # Personal account
   Host github.com_abhinav-nath
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_ed25519_personal
   ```


3. To set only single active key

   - List the currently active key(s):

     ```shell
     $ ssh-add -l
     256 SHA256:abcdxyz work@email.com (ED25519)
     ```

   - Delete all active keys:

     ```shell
     ssh-add -D
     ```

   - Make another key active:

     ```shell
     ssh-add id_ed25519_personal
     ```

   - List the currently active key(s) again:

     ```shell
     $ ssh-add -l
     256 SHA256:1234abcd personal@email.com (ED25519)
     ```


4. Set git username and email for different accounts

   Create different `.gitconfig-*.inc` files for different accounts
   
   **.gitconfig-personal.inc**
   ```shell
   # file location: ~/.gitconfig-personal.inc

   [user]
     name = Abhinav Nath
     email = abhinavnath@ymail.com
   ```
   
   **.gitconfig-otheracc1.inc**
   ```shell
   # file location: ~/.gitconfig-otheracc1.inc

   [user]
     name = Other User 1
     email = otheracc1@xyz.com
   ```

   **.gitconfig**

   ```shell
   # Note: Even though this will show up twice in `git config -l`, it will still be overridden based on the order of the includeIf lines below
   [includeIf "gitdir/i:~/dev/personal/"]         # Personal
     path = ~/.gitconfig-personal.inc
   [includeIf "gitdir/i:~/dev/otheracc1/"]        # Other Account 1
     path = ~/.gitconfig-otheracc1.inc
   [includeIf "gitdir/i:~/dev/otheracc2/"]        # Other Account 2
     path = ~/.gitconfig-otheracc2.inc
   ```


Check current git configuration

```shell
git config -l
```

Update username and email

```shell
git config user.name "Abhinav Nath"
git config user.email "personal@email.com"
     
# To set globally
git config --global user.email "personal@email.com"
```
