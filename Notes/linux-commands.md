# Linux Commands

When I first started using Linux, the terminal felt confusing. It was just a cursor on a screen, and I did not know what to type. But after using it for a while, I realized that Linux commands are actually simple and very useful. You do not need to memorize everything at once. A few basic commands can already help a lot in daily work.

This note is a collection of useful Linux commands with simple explanations. I kept it practical and easy to understand.

---

## Basic Navigation

- `pwd` — prints the current working directory, so you know exactly where you are.
- `ls` — lists files and folders in the current directory.
- `ls -l` — shows a detailed list with permissions, owner, size, and date.
- `ls -a` — shows all files, including hidden ones.
- `ls -la` — combines detailed view and hidden files.
- `ls -lh` — shows file sizes in a human-readable format like KB or MB.
- `ls -R` — lists files recursively inside subfolders too.

- `cd <directory>` — changes to another directory.
- `cd ..` — goes one folder back.
- `cd /` — goes to the root directory.
- `cd ~` — goes to your home directory.
- `cd -` — switches back to the previous directory.

---

## Creating Files and Folders

- `touch file.txt` — creates an empty file.
- `touch a.txt b.txt c.txt` — creates multiple empty files at once.
- `mkdir foldername` — creates a new folder.
- `mkdir folder1 folder2 folder3` — creates multiple folders.
- `mkdir -p a/b/c` — creates nested folders if they do not already exist.
- `rmdir foldername` — removes an empty folder.

---

## Copying, Moving, and Removing

- `cp file1 file2` — copies a file.
- `cp file.txt /home/user/Documents/` — copies a file to another location.
- `cp -r folder1 folder2` — copies folders recursively.
- `cp -i file1 file2` — asks before overwriting a file.
- `cp -v file1 folder/` — shows what is being copied.

- `mv file.txt /tmp/` — moves a file to another location.
- `mv oldname.txt newname.txt` — renames a file.
- `mv -i file.txt folder/` — asks before overwriting.
- `mv -v file.txt folder/` — shows the move operation.

- `rm file.txt` — deletes a file.
- `rm -i file.txt` — asks before deleting.
- `rm -f file.txt` — forces deletion without asking.
- `rm -r foldername` — deletes a folder and everything inside it.
- `rm -rf foldername` — force deletes a folder and its contents. Use this very carefully.

---

## Viewing Files

- `cat file.txt` — displays the full content of a file.
- `cat file1 file2` — shows multiple files one after another.
- `less file.txt` — opens a file in a scrollable view.
- `more file.txt` — another way to view a file page by page.
- `head file.txt` — shows the first few lines of a file.
- `head -n 20 file.txt` — shows the first 20 lines.
- `tail file.txt` — shows the last few lines of a file.
- `tail -n 20 file.txt` — shows the last 20 lines.
- `tail -f logfile.log` — keeps showing new log lines live as they are added.

Inside `less`, you can use `q` to quit, `/text` to search, `n` to go to the next match, and `b` to go back.

---

## Searching Inside Files

- `grep "error" file.txt` — searches for the word “error” inside a file.
- `grep -i "error" file.txt` — searches without caring about uppercase or lowercase.
- `grep -n "error" file.txt` — shows line numbers too.
- `grep -r "error" /var/log` — searches recursively inside a folder.
- `grep -v "error" file.txt` — shows lines that do not match the word.
- `grep -c "error" file.txt` — counts how many matches there are.

- `find . -name file.txt` — finds a file by name.
- `find /home -name "*.log"` — finds all log files under `/home`.
- `find . -type f` — finds only files.
- `find . -type d` — finds only directories.
- `find . -size +100M` — finds files larger than 100 MB.
- `find . -mtime -7` — finds files changed in the last 7 days.

- `locate file.txt` — finds files quickly using a database.
- `updatedb` — updates the locate database so searches stay fresh.

---

## Reading and Writing Text

- `echo "Hello Linux"` — prints text to the terminal.
- `echo "Hello" > file.txt` — writes text to a file and overwrites the old content.
- `echo "World" >> file.txt` — appends text to the end of a file instead of overwriting it.
- `tee file.txt` — writes output to a file and also shows it on the screen.
- `tee -a file.txt` — appends output to a file.

---

## Editing Files

- `nano file.txt` — opens a simple text editor in the terminal.
- `vim file.txt` — opens a more advanced text editor.

In `nano`, `Ctrl + O` saves, `Ctrl + X` exits, and `Ctrl + W` searches.

In `vim`, press `i` to start typing, `Esc` to stop editing, `:w` to save, `:q` to quit, `:wq` to save and quit, and `:q!` to quit without saving.

---

## File Permissions

Linux permissions decide who can read, write, or execute a file.

- `chmod 755 script.sh` — changes file permissions.
- `chmod +x script.sh` — makes a file executable.
- `chmod 644 file.txt` — gives read/write to owner and read-only to others.

- `chown user file.txt` — changes the owner of a file.
- `chown user:group file.txt` — changes both owner and group.

- `chgrp groupname file.txt` — changes the group of a file.
- `umask` — shows the default permission mask for new files.

---

## Users and Groups

- `whoami` — shows the current username.
- `id` — shows user ID and group ID.
- `who` — shows who is logged in.
- `w` — shows logged-in users and what they are doing.
- `groups` — shows which groups the current user belongs to.

- `useradd username` — creates a new user.
- `passwd` — changes the current user password.
- `passwd username` — changes another user’s password, usually with sudo.
- `usermod -aG sudo username` — adds a user to the sudo group.
- `groupadd groupname` — creates a new group.

---

## Process Management

- `ps` — shows running processes.
- `ps aux` — shows all processes with full details.
- `ps -ef` — another way to see running processes in a different format.
- `top` — shows live process usage.
- `htop` — a nicer interactive version of `top` if installed.

- `kill PID` — stops a process by its process ID.
- `kill -9 PID` — force kills a process.
- `pkill processname` — kills a process by name.

- `jobs` — shows background jobs.
- `bg` — sends a stopped job to the background.
- `fg` — brings a background job to the foreground.
- `nohup command &` — runs a command so it keeps running even after logout.

---

## System Information

- `uname` — shows basic system information.
- `uname -a` — shows full system details.
- `hostname` — shows the machine name.
- `uptime` — shows how long the system has been running.
- `date` — shows the current date and time.
- `cal` — shows a calendar.
- `cal 2026` — shows the calendar for a specific year.

- `free -h` — shows memory usage in readable format.
- `df -h` — shows disk usage in readable format.
- `du -sh foldername` — shows the size of a folder.
- `du -sh *` — shows sizes of everything in the current directory.

---

## Networking Commands

- `ip a` — shows network interfaces and IP addresses.
- `ip addr` — same idea, with more detail.
- `ip route` — shows routing information.
- `ifconfig` — older command for viewing network details, still seen on some systems.

- `ping google.com` — checks whether a host is reachable.
- `curl https://example.com` — fetches content from a URL.
- `curl -O https://example.com/file.txt` — downloads a file and keeps the original name.
- `wget https://example.com/file.txt` — downloads files from the internet.

- `netstat -tuln` — shows listening ports and network connections.
- `ss -tuln` — modern alternative to `netstat`.
- `ss -an` — shows all sockets.
- `dig google.com` — performs a DNS lookup.
- `nslookup google.com` — another DNS lookup tool.
- `hostname -I` — shows the machine’s IP address(es).
- `traceroute google.com` — shows the route packets take to reach a host.

---

## Package Management on Debian/Ubuntu

- `sudo apt update` — refreshes the package list.
- `sudo apt upgrade` — upgrades installed packages.
- `sudo apt install package-name` — installs a package.
- `sudo apt remove package-name` — removes a package.
- `sudo apt purge package-name` — removes the package and its config files.
- `sudo apt autoremove` — removes unused dependencies.

---

## Archiving and Compression

- `tar -cvf archive.tar folder/` — creates a tar archive.
- `tar -xvf archive.tar` — extracts a tar archive.
- `tar -czvf archive.tar.gz folder/` — creates a compressed gzip archive.
- `tar -xzvf archive.tar.gz` — extracts a gzip tar archive.

- `zip -r archive.zip folder/` — creates a zip file.
- `unzip archive.zip` — extracts a zip file.
- `gzip file.txt` — compresses a file.
- `gunzip file.txt.gz` — decompresses a gzipped file.

---

## Redirection and Pipes

These are some of the most useful things in Linux.

- `>` — sends output to a file and overwrites it.
- `>>` — sends output to a file and appends it.
- `<` — uses a file as input.
- `|` — takes output from one command and passes it to another command.
- `2>` — sends errors to a file.
- `&>` — sends both output and errors to a file.

Examples:
- `echo "hello" > file.txt`
- `echo "world" >> file.txt`
- `sort < names.txt`
- `ls | grep ".txt"`
- `ps aux | grep ssh`
- `command 2> error.txt`
- `command &> output.txt`
- `cat file.txt | grep "linux" | wc -l`

---

## Text Processing Commands

- `wc file.txt` — counts lines, words, and characters.
- `wc -l file.txt` — counts lines.
- `wc -w file.txt` — counts words.
- `wc -c file.txt` — counts characters.

- `sort file.txt` — sorts lines alphabetically.
- `uniq file.txt` — removes duplicate adjacent lines.
- `sort file.txt | uniq` — sorts and then removes duplicates properly.

- `cut -d: -f1 /etc/passwd` — cuts out the first field using `:` as a separator.
- `awk '{print $1}' file.txt` — prints the first column.
- `awk '{print $2}' file.txt` — prints the second column.
- `awk -F: '{print $1}' /etc/passwd` — uses `:` as a field separator.

- `sed 's/old/new/g' file.txt` — replaces text in a file.
- `tr 'a-z' 'A-Z'` — converts lowercase letters to uppercase.
- `xargs` — takes output from one command and passes it as arguments to another.

Example:
- `find . -name "*.log" | xargs rm` — finds log files and removes them.

---

## Disk and Storage

- `lsblk` — shows block devices like disks and partitions.
- `fdisk -l` — lists disk partitions.
- `mount /dev/sdb1 /mnt` — mounts a device to a folder.
- `umount /mnt` — unmounts a mounted filesystem.
- `blkid` — shows UUID and filesystem type information.

---

## Logging and Monitoring

- `dmesg` — shows kernel messages.
- `journalctl` — shows system logs on systemd-based systems.
- `journalctl -xe` — shows recent logs with extra detail.
- `journalctl -u ssh` — shows logs for a specific service like SSH.
- `tail -f /var/log/syslog` — watches log updates live.

---

## Shell and Environment

- `env` — shows environment variables.
- `printenv` — prints environment variables.
- `export NAME="Linux"` — sets an environment variable.
- `alias ll='ls -la'` — creates a shortcut command.
- `unalias ll` — removes an alias.
- `history` — shows command history.
- `clear` — clears the terminal screen.

---

## Helpful Terminal Shortcuts

These are not commands, but they save a lot of time.

- `Ctrl + C` — stops the current command.
- `Ctrl + Z` — pauses the current command.
- `Ctrl + D` — exits the terminal or ends input.
- `Ctrl + L` — clears the screen.
- `Tab` — auto-completes commands and file names.
- `↑` and `↓` — move through command history.
- `Ctrl + A` — moves to the beginning of the line.
- `Ctrl + E` — moves to the end of the line.
- `Ctrl + U` — deletes everything before the cursor.
- `Ctrl + K` — deletes everything after the cursor.

---

## Other Useful Commands

- `man ls` — opens the manual page for a command.
- `help` — shows help for shell built-in commands.
- `which python3` — shows where a command is located.
- `whereis bash` — shows the binary, source, and manual locations.
- `type cd` — tells how a command is interpreted by the shell.
- `sleep 5` — pauses for 5 seconds.
- `time ls` — shows how long a command takes to run.

---

## A Few Handy One-Liners

- `ls -la` — shows everything in the current folder in detail.
- `ps aux | grep firefox` — checks whether Firefox is running.
- `find . -name "*.txt"` — finds all text files in the current folder.
- `cat file.txt | grep "error"` — searches for the word error inside a file.
- `tail -f logfile.log` — watches logs live.
- `df -h` — checks disk space.
- `free -h` — checks memory usage.
- `history | tail` — shows the latest commands you used.
- `sudo apt update && sudo apt upgrade` — updates package lists and then upgrades installed packages.
- `mkdir -p project/src project/test` — creates project folders in one go.

---

## Final Thoughts

Linux commands may look like a lot at first, but most of them are just small tools for doing simple things faster. Nobody remembers every command all the time. Even people who use Linux daily still look things up now and then.

The best way to learn is to keep using the terminal. Start with the basic commands, then slowly move to the advanced ones. After some practice, it starts feeling natural.