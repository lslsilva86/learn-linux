# Advanced Linux Commands & Shell Scripting Summary

- https://www.bosscoderacademy.com/blog/platform-shell-scripting-and-automation

## 1. File Transfer & Networking

### File Transfer Tools

- **scp**: Secure copy using SSH.
- **rsync**: Efficient file synchronization.
- **ftp/sftp**: FTP is deprecated, use sftp for secure transfer.

### Networking Tools

- **ping**: Check connectivity.
- **ip a**: View IP addresses (replaces ifconfig).
- **netstat / ss**: Show network connections (`ss` preferred).
- **Common commands**:
  - `scp file user@remote:/path/`
  - `rsync -avz src/ user@remote:/dest/`
  - `ping google.com`
  - `ip a`, `ss -tulnp`

---

## 2. Pro Linux Commands

### AWK

- Pattern scanning and processing.
- `awk '{print $1}' file.txt` → Print first column.
- `awk -F ',' '{print $1, $3}' file.csv`

### GREP

- Search for patterns.
- `grep "error" file.txt`
- `grep -i "error"` → Case-insensitive.
- `grep -n "failed"` → Show line numbers.

### SED

- Stream editor for inline text changes.
- `sed 's/foo/bar/g' file.txt` → Replace `foo` with `bar`.
- `sed '/pattern/d'` → Delete matching lines.
- `sed '/^$/d'` → Delete empty lines.

### FIND

- Search and filter files.
- `find /home -name "*.log"`
- `find /var -type d -name "logs"`
- `find / -size +500M`
- `find /tmp -name "*.log" -delete`

---

## 3. Automation Examples

- **Batch Replace**:  
  `find . -type f -name "*.txt" -exec sed -i 's/old/new/g' {} +`

- **Delete old logs**:  
  `find /var/log -name "*.log" -mtime +30 -delete`

- **CSV Extraction**:  
  `awk -F ',' '{ print $1, $3 }' data.csv`

- **Live Log Monitoring**:  
  `tail -f /var/log/syslog | grep "error"`

- **Batch Rename**:  
  `for f in *.txt; do mv "$f" "${f%.txt}.bak"; done`

---

## 4. Shell Basics

### What is a Shell?

A command-line interface that interacts with the Linux kernel.

### Check Shell Type

```bash
echo $SHELL
echo $0
```

### Shebang

Tells which interpreter to use:

```bash
#!/bin/bash
```

---

## 5. Importance in DevOps & Data Engineering

- **Automation**: Backup, deployment, monitoring.
- **CI/CD**: Integrate with Jenkins, GitHub Actions.
- **Security**: SSH key mgmt, firewalls.
- **Integration**: Python, SQL, APIs, cron jobs.

---

## 6. Shell Types Comparison

| Shell | Best For       | Features         |
| ----- | -------------- | ---------------- |
| Bash  | General Use    | Widely supported |
| Zsh   | Power Users    | Plugins, themes  |
| Fish  | Beginners      | Auto-suggestions |
| Tcsh  | C Devs         | C-like syntax    |
| Ksh   | Enterprises    | Fast, scripting  |
| Dash  | System Scripts | Minimal, fast    |

---

## 7. Running Your First Script

```bash
nano My_script.sh
```

Script Content:

```bash
#!/bin/bash
echo "Hello from my first shell script!"
```

Make it executable:

```bash
chmod +x My_script.sh
./My_script.sh
```

---

## Summary

| Tool       | Use                    |
| ---------- | ---------------------- |
| `scp`      | Secure file transfer   |
| `rsync`    | Efficient sync         |
| `awk`      | Extract columns        |
| `grep`     | Search patterns        |
| `sed`      | Replace text           |
| `find`     | Locate files           |
| `tail -f`  | Real-time logs         |
| `chmod +x` | Make script executable |
| `nano`     | Script editor          |

---

This summary provides a condensed yet comprehensive overview for mastering file transfer, networking, and automation with shell scripting in Linux.

---

# 🔁 File Transfer Cheatsheet (Extended)

## SCP – Secure Copy

```bash
scp myfile.txt user@192.168.1.10:/home/user/
scp user@192.168.1.10:/home/user/myfile.txt .
```

Options: `-r` (recursive), `-P` (port), `-c` (compression), `-i` (private key)

## RSYNC – Remote Sync

```bash
rsync -avz source/ user@remote:/destination/
rsync -avz user@remote:/source/ destination/
```

## FTP – File Transfer Protocol (Not secure)

```bash
ftp ftp.example.com
get filename.txt
put localfile.txt
```

---

# 📦 FTPS (FTP Secure) Cheatsheet

FTPS adds SSL/TLS encryption to standard FTP.

## 🔐 Connect to FTPS Server

```bash
lftp -u username,password ftps://ftp.example.com
```

Or:

```bash
lftp ftps://ftp.example.com
user username password
```

## 📄 Common Commands

| Command                  | Description                |
| ------------------------ | -------------------------- |
| `ls`                     | List files and directories |
| `get filename.txt`       | Download a file            |
| `put localfile.txt`      | Upload a file              |
| `mirror remote local`    | Recursive download         |
| `mirror -R local remote` | Recursive upload           |
| `bye`                    | Exit FTPS session          |

## 🔧 Configuration

```bash
set ftp:ssl-force true
set ftp:ssl-protect-data true
set ftp:passive-mode on
```

## ✅ Example

```bash
lftp -u youruser,yourpass ftps://yourserver.com
set ftp:ssl-force true
set ftp:ssl-protect-data true
set ftp:passive-mode on
ls
put file.txt
get another.txt
bye
```

> ⚠️ FTPS ≠ SFTP. Use `sudo apt install lftp` to install.

---

# 🌐 Networking Cheatsheet

## ping

```bash
ping google.com
ping -c 4 google.com
```

## ip

```bash
ip a
ip link show
ip addr add 192.168.1.100/24 dev eth0
```

## ifconfig (Deprecated)

```bash
ifconfig
```

## netstat / ss

```bash
sudo apt install net-tools
netstat -tulnp
ss -tulnp
```

---

# 🔍 Text Processing Cheatsheet

## awk

```bash
awk '{ print $1 }' file.txt
awk '{ print $2 }' File10.txt
awk '/error/ { print $0 }' File10.txt
```

## grep

```bash
grep "Age" logfile.txt
grep -i "age" File10.txt
grep -n "failed" auth.log
grep -E "error|fail|timeout" logfile.txt
```

## sed

```bash
sed 's/Age/Gender/g' File10.txt
sed '/debug/d' logfile.txt
sed '/^$/d' file.txt
```

---

# 🗂️ File Searching

## find

```bash
find /home -name "*.txt"
find /var -type d -name "logs"
find / -size +500M
find /tmp -name "*.log" -delete
find /home -mtime -7
```

---

# 🧰 Automation Examples

```bash
find . -type f -name "*.txt" -exec sed -i 's/oldtext/newtext/g' {} +
find /var/log -name "*.log" -mtime +30 -delete
awk -F ',' '{ print $1, $3 }' data.csv > output.csv
tail -f /var/log/syslog | grep "error"
for file in *.txt; do mv "$file" "${file%.txt}.bak"; done
```

---

# 🐚 Shell Basics

## Check Shell Type

```bash
echo $SHELL
echo $0
```

## First Script

```bash
nano My_script.sh
```

Inside the file:

```bash
#!/bin/bash
echo "Hello from my first shell script!"
```

## Make It Executable

```bash
chmod +x My_script.sh
```

## Run Script

```bash
./My_script.sh
```
