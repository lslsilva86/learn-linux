# Linux Essentials & File Management

- https://www.bosscoderacademy.com/blog/platform-introduction-to-linux
- https://www.bosscoderacademy.com/blog/platform-linux-essentials-file-management

## 🔍 Navigating the Filesystem

- `ls` – List directory contents.
- `ls -l` – List with detailed file info.
- `ls -la` – List including hidden files.
- `pwd` – Print current directory.
- `cd ..` – Go one level up.
- `cd` – Return to home directory.

## 📁 File Operations

- `touch filename` – Create an empty file.
- `cat > filename` – Create a file with content (ends with Ctrl + Z).
- `cat >> filename` – Append content to file.
- `cat filename` – View file content.

## 🗂️ Directories

- `mkdir foldername` – Create a directory.
- `mkdir folder1 folder2` – Create multiple directories.
- `rmdir foldername` – Remove empty directory.
- `rm -r foldername` – Delete directory with contents.

## 📄 Copy, Move, Rename, Delete

- `cp file newfile` – Copy file.
- `cp file folder` – Copy file to directory.
- `sudo cp file folder` – Copy file with elevated permissions.
- `mv source dest` – Move or rename file/directory.
- `rm file` – Delete a file.
- `sudo rm file` – Delete a file (with sudo).
- `mv oldname newname` – Rename file or directory.

## 🧹 Terminal Utility

- `clear` – Clear the terminal screen.
- `echo "text"` – Display text output.

## 🔧 Pipes & Redirection

- `ps -ef | grep processname` – Filter process list.
- `ls -1 | wc -l` – Count number of files.
- `>` – Redirect output (overwrite).
- `>>` – Append output to file.

## 🔗 Command Chaining

- `cmd1 && cmd2` – Run cmd2 _only if_ cmd1 succeeds.
- `cmd1 || cmd2` – Run cmd2 _only if_ cmd1 fails.
- `cmd1 && echo "Success!" || echo "Failed!"` – Combined logic.

## ⚙️ Process Management

- `ps` – View current terminal session processes.
- `ps aux` – View all running processes.
- `ps -u username` – View user-specific processes.
- `top` – Real-time process monitoring.
- `kill PID` – Terminate a process.
- `kill -9 PID` – Force terminate.

## 👤 User & Group Management

- `sudo adduser username` – Add user.
- `sudo deluser username` – Delete user.
- `sudo deluser --remove-home username` – Delete user & home dir.
- `sudo usermod -l newname oldname` – Change username.
- `sudo usermod -d /path -m username` – Change home dir.
- `sudo groupadd groupname` – Add group.
- `sudo usermod -aG group user` – Add user to group.
- `sudo deluser user group` – Remove user from group.

## 👥 Viewing Users in Linux

### List All Users

```bash
cat /etc/passwd
```

Displays all user accounts on the system.

### List Only Usernames

```bash
cut -d: -f1 /etc/passwd
```

Extracts only the usernames from the passwd file.

### Show Currently Logged-In Users

```bash
who
```

Lists currently logged-in users.

```bash
w
```

Displays who is logged in and what they are doing.

### Show Logged-In Users (Summary)

```bash
users
```

Lists logged-in usernames in a single line.

### Check If a Specific User Exists

```bash
id username
```

Shows UID, GID, and groups for the given user.

## 🔐 Permissions

- `chmod 755 filename` – Change file permissions.
- `chown user filename` – Change file owner.
- `chown user:group filename` – Change file owner & group.
- `umask` – View default permission mask.
- `umask 022` – Set default permission mask.

## 💾 Disk Usage

- `du -sh /dir` – Show total usage of a directory.
- `du -h --max-depth=1 /dir` – Subdirectory sizes.
- `df -h` – Check available space (all mount points).
- `df -h /dev/sda1` – Disk usage of specific partition.

## 🗜️ Archiving & Compression

- `tar -cvf archive.tar dir` – Create archive.
- `tar -xvf archive.tar` – Extract archive.
- `gzip file` – Compress file.
- `gunzip file.gz` – Decompress.
- `zip archive.zip file` – Compress using zip.
- `unzip archive.zip` – Extract zip archive.

## 🧱 Volume Management (LVM)

- `lsblk` – List devices and partitions.
- `sudo fdisk /dev/sdx` – Partition disk.
- `sudo mkfs.ext4 /dev/sdx1` – Format partition.
- `sudo mount /dev/sdx1 /mnt` – Mount partition.
- `sudo pvcreate /dev/sdx1` – Create physical volume.
- `sudo vgcreate my_vg /dev/sdx1` – Create volume group.
- `sudo lvcreate -L 10G -n my_lv my_vg` – Create logical volume.
- `sudo mkfs.ext4 /dev/my_vg/my_lv` – Format logical volume.
- `sudo mount /dev/my_vg/my_lv /mnt` – Mount logical volume.
