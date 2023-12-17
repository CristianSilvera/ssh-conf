# ssh-conf

Generating an SSH key pair using the Ed25519 algorithm and then adding it to the SSH agent. Here's a step-by-step breakdown of the process:

1. Check the location of the `ssh` executable:
   ```bash
   cs@casa:~$ which ssh
   /usr/bin/ssh
   ```

2. List the contents of the `~/.ssh` directory (to check existing SSH keys):
   ```bash
   cs@casa:~$ ls -l ~/.ssh
   total 0
   ```

3. Commented out commands (not executed):
   ```bash
   #ssh-keygen -t ed25519 -C "your_email@example.com"
   #ssh-keygen -t ed25519 -C "cristiansilveraa@gmail.com"
   ```

4. Generate an Ed25519 SSH key pair with a specified email:
   ```bash
   cs@casa:~$ ssh-keygen -t ed25519 -C "cristiansilveraa@gmail.com"
   ```

   - You will be prompted to enter a file to save the key (press Enter to use the default).
   - Enter a passphrase for additional security (or leave it empty for no passphrase).
   - Confirm the passphrase.

   The generated keys are saved in `/home/cs/.ssh/` with filenames `id_ed25519` (private key) and `id_ed25519.pub` (public key).

5. List the contents of the `~/.ssh` directory again:
   ```bash
   cs@casa:~$ ls -l ~/.ssh/
   total 8
   -rw------- 1 cs cs 419 dic 17 12:17 id_ed25519
   -rw-r--r-- 1 cs cs 108 dic 17 12:17 id_ed25519.pub
   ```

6. Display the public key:
   ```bash
   cs@casa:~$ cat ~/.ssh/id_ed25519.pub
   ssh-ed25519 ABCDC3NzaC1lNNNN1NTE5AAAAIGQwz916yf8kDAXn3r9G... cristiansilveraa@gmail.com
   ```

7. Commented out commands (not executed):
   ```bash
   #eval "$(ssh-agent -s)"
   #ssh-add ~/.ssh/id_ed25519
   ```

8. Start the SSH agent:
   ```bash
   cs@casa:~$ eval "$(ssh-agent -s)"
   Agent pid 6165
   ```

9. Add the generated private key to the SSH agent:
   ```bash
   cs@casa:~$ ssh-add ~/.ssh/id_ed25519
   Identity added: /home/cs/.ssh/id_ed25519 (cristiansilveraa@gmail.com)
   ```

Now, your SSH key pair is generated, and the private key is added to the SSH agent for secure authentication.
