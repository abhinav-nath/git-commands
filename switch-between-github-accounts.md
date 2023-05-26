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


4. Set git username and email

   - Check current git configuration

     ```shell
     git config -l
     ```

   - Update username and email

     ```shell
     git config user.name "Abhinav Nath"
     git config user.email "personal@email.com"
     
     # To set globally
     git config --global user.email "personal@email.com"
     ```
