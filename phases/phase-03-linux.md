# Phase 3: Linux Command Line

Most servers, security tools, and attack targets run on Linux. Over the next 14 days you will build real comfort in the terminal: navigating the filesystem, managing users and permissions, handling processes and networking, and writing your first bash scripts. By Day 28 you will apply everything by playing the first levels of OverTheWire Bandit, a game that teaches Linux through a capture-the-flag format.

## Day 15: Install a VM and open the terminal
- **Learn:** A virtual machine lets you run a full Ubuntu Linux system safely inside your current computer, so you can break things and reinstall without any risk to your real machine.
- **Do:** Download VirtualBox from https://www.virtualbox.org, download an Ubuntu Desktop ISO from the official Ubuntu site, create a new VM with 4 GB of RAM and 25 GB of disk, install Ubuntu, then open a terminal (Ctrl+Alt+T) and run `pwd`, `ls`, and `cd /` followed by `ls` to see where you are and what the root folder holds.
- [ ] Done: Ubuntu VM boots, terminal opens, and I ran pwd, ls, and cd commands.

## Day 16: The filesystem layout and file commands
- **Learn:** Linux organizes everything in one tree starting at `/`, with fixed folders like `/home` (your files), `/etc` (settings), and `/var` (logs), and paths are either absolute (start with `/`) or relative (from where you are now).
- **Do:** In your VM terminal, run `mkdir practice`, `cd practice`, `touch notes.txt`, `cp notes.txt notes-copy.txt`, `mv notes-copy.txt renamed.txt`, `ls -la`, then `rm renamed.txt`, and use `ls` after each step so you can see exactly what every command changed.
- [ ] Done: I created, copied, moved, listed, and deleted files in a practice folder.

## Day 17: Reading files and getting help
- **Learn:** You almost never need an editor to read a file, since `cat`, `less`, `head`, and `tail` show contents quickly, and every command documents itself through `man` pages and the `--help` flag.
- **Do:** Run `cat /etc/os-release`, `head -5 /etc/passwd`, `tail -5 /etc/passwd`, then `man ls` (press q to exit) and `ls --help`, and practice `less /etc/services` using / to search for the word http and q to quit.
- [ ] Done: I read files with cat, less, head, and tail, and looked up help with man and --help.

## Day 18: Users, groups, and sudo
- **Learn:** Linux tracks who you are with a user account and groups, and the `sudo` command lets a normal user run single commands as the administrator (root), which is how almost all system changes are made.
- **Do:** Run `whoami`, `id`, `groups`, `cat /etc/passwd | grep $USER`, `sudo whoami`, then create a practice group with `sudo groupadd cybercrew` and inspect it with `getent group cybercrew` before removing it with `sudo groupdel cybercrew`.
- [ ] Done: I checked my user and groups with whoami and id, and used sudo to create and delete a group.

## Day 19: File permissions
- **Learn:** Every file has read, write, and execute permissions (rwx) set separately for the owner, the group, and everyone else, and `chmod` sets them either with letters (u+x) or with octal numbers like 755, while `chown` changes who owns a file.
- **Do:** Create a test file and a test script (`touch test.txt`, `echo 'echo hello' > test.sh`), run `ls -l` on both, then try `chmod 600 test.txt`, `chmod 755 test.sh`, `./test.sh`, and `sudo chown root test.txt` followed by `ls -l` again to see how the permission string changed each time.
- [ ] Done: I changed permissions with chmod using octal numbers and changed ownership with chown.

## Day 20: Processes and services
- **Learn:** Everything running on Linux is a process with an ID number, and long-running background programs called services are managed by systemd through the `systemctl` command, which starts, stops, and checks their status.
- **Do:** Run `ps aux | head -20`, `top` (press q to quit), start a sleep process with `sleep 300 &`, find its PID with `ps aux | grep sleep`, kill it with `kill <PID>`, then run `systemctl status ssh` or `systemctl status sshd` to see how a service reports its state.
- [ ] Done: I listed processes, killed one by PID, and checked a service status with systemctl.

## Day 21: Networking commands and SSH
- **Learn:** Linux networking is inspected from the terminal with tools like `ip` (addresses and interfaces), `ss` (open connections and listening ports), `ping` (reachability), and `curl` (fetching web pages), and SSH lets you log into another machine securely over the network.
- **Do:** Run `ip addr`, `ss -tlnp`, `ping -c 4 8.8.8.8`, and `curl -I https://example.com`, then install the SSH server in your VM (`sudo apt install -y openssh-server`), find the VM IP with `ip addr`, and SSH into your own VM from another terminal with `ssh <your-username>@<vm-ip>`.
- [ ] Done: I checked my IP, open ports, ping, and fetched a web page with curl, then SSHed into my VM.

## Day 22: Pipes, redirection, and text tools
- **Learn:** Pipes (`|`) send one command's output into the next command, redirection (`>`, `>>`) saves output to files, and small tools like `grep`, `find`, `sort`, `uniq`, and `wc` become powerful when chained together.
- **Do:** Run `ls /etc | grep conf | sort > conf-files.txt`, `wc -l conf-files.txt`, `cat /etc/passwd | cut -d: -f1 | sort | uniq -c | sort -nr | head -10`, and `find /etc -maxdepth 1 -name "*.conf"`, then read conf-files.txt with cat to confirm the redirect worked.
- [ ] Done: I chained grep, sort, uniq, and wc with pipes and saved output to a file with redirection.

## Day 23: sed and awk basics
- **Learn:** `sed` edits text as a stream (find and replace without opening an editor) and `awk` processes column-based data line by line, which makes both perfect for log files and command output.
- **Do:** Make a sample file with `printf "alice:25\nbob:30\ncarol:22\n" > ages.txt`, then run `sed 's/bob/robert/' ages.txt`, `awk -F: '{print $1}' ages.txt`, `awk -F: '$2 > 23 {print $1 " is over 23"}' ages.txt`, and `awk -F: '{sum += $2} END {print "average:", sum/NR}' ages.txt`.
- [ ] Done: I used sed to replace text and awk to filter and summarize columns.

## Day 24: Environment variables, PATH, and aliases
- **Learn:** Environment variables like `PATH` and `HOME` configure your shell, `PATH` decides where the shell looks for commands, and the `~/.bashrc` file lets you set variables and short aliases that load every time a terminal opens.
- **Do:** Run `echo $HOME`, `echo $PATH`, `export GREETING=hello`, `echo $GREETING`, then add `alias ll='ls -lah'` to `~/.bashrc` with `echo "alias ll='ls -lah'" >> ~/.bashrc`, run `source ~/.bashrc`, and test the new `ll` alias.
- [ ] Done: I inspected PATH and HOME, set a variable, and added a permanent alias in .bashrc.

## Day 25: Bash scripting part 1
- **Learn:** A bash script is just a file of commands that runs top to bottom, and variables, `if` statements, and `for`/`while` loops let it make decisions and repeat work instead of you typing each command by hand.
- **Do:** Write a file called `day25.sh` containing a shebang line `#!/bin/bash`, a `NAME` variable, an `if` that checks whether `/etc/passwd` exists, and a `for` loop that prints the numbers 1 to 5, then run `chmod +x day25.sh` and execute it with `./day25.sh`.
- [ ] Done: I wrote and ran a script using a variable, an if statement, and a loop.

## Day 26: Bash scripting part 2
- **Learn:** A useful script solves one real problem well, like backing up a folder with a timestamped name or scanning a log for suspicious lines, and combining commands you already know keeps it simple and reliable.
- **Do:** Write `backup.sh` that creates a timestamped tar backup of your practice folder (`tar -czf backup-$(date +%F-%H%M).tar.gz practice/`), verifies the file with `ls -lh backup-*.tar.gz`, then extends it to log-checking by adding a line that runs `grep -i "failed" /var/log/auth.log | tail -5` and echoes how many failed lines were found.
- [ ] Done: I wrote a script that makes a timestamped backup and checks a log for failed logins.

## Day 27: Package management with apt
- **Learn:** Ubuntu installs and updates software through the `apt` package manager, which pulls trusted programs from online repositories, so one command installs tools that would take manual downloads on other systems.
- **Do:** Run `sudo apt update`, then `sudo apt upgrade -y`, install three tools with `sudo apt install -y nmap tree htop`, verify each with `nmap --version`, `tree --version`, and `htop --version` (q to quit htop), and list what you installed with `apt list --installed | grep -E "nmap|tree|htop"`.
- [ ] Done: I updated my system and installed nmap, tree, and htop with apt.

## Day 28: OverTheWire Bandit levels 0 to 5
- **Learn:** OverTheWire Bandit is a free wargame at https://overthewire.org that teaches Linux by making you find passwords hidden in files, and each level only unlocks after you solve the previous one, which forces you to actually use the terminal.
- **Do:** Read the Bandit rules on the OverTheWire site, connect with `ssh bandit0@bandit.labs.overthewire.org -p 2220` (password: bandit0), solve levels 0 through 4 to reach level 5 (reading a hidden file, a file with spaces and dashes in its name, and finding a file by size), and write down which command solved each level plus what the trick was.
- [ ] Done: I solved Bandit levels 0 to 4 and recorded the solving command for each level.
