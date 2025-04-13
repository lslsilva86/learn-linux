# Shell Scripting and Linux Fundamentals - Summary

- https://www.bosscoderacademy.com/blog/platform-shell-scripting-and-automation

## 1. Shell Scripting Basics

- **Variables & Data Types**: Store values without declaring types. Use `variable=value` and access using `$variable`.
- **Reading Input**: Use `read variable_name` to capture user input.
- **Calculations**: Use `$(( expression ))` for integer operations.

## 2. Conditionals & Loops

- **If-Else**: `if [ condition ]; then ... elif ... else ... fi`
- **Loops**:
  - `for i in {1..5}; do ... done`
  - `while [ condition ]; do ... done`
  - `until [ condition ]; do ... done`
- **Combine loops and conditionals** for more complex logic.

## 3. Functions

- **Syntax**: `function_name() { ... }`
- **With Arguments**: Use `$1`, `$2`, etc.
- **Return Values**: Use `echo` to output and capture using `$(function)`.
- **Local Variables**: Use `local` keyword.
- **Nested Functions**: Functions can call other functions.

## 4. Debugging & Error Handling

- **Debugging**: Use `set -x` to enable and `set +x` to disable.
- **Immediate Exit on Error**: Use `set -e`.
- **Trap Errors**: `trap 'command' ERR` for cleanup or logging.

## 5. Automation

- **Backups**: Create directory, compress files with `tar`, and schedule via `cron`.
- **Log Analysis**: Use `grep` to find error/warning entries and generate reports.

## 6. Linux Security & Permissions

- **SSH**:
  - Use SSH keys for secure login (`ssh-keygen`, `ssh-copy-id`).
  - Edit `/etc/ssh/sshd_config` for security.
- **Firewalls**:
  - Use `ufw enable`, `ufw allow OpenSSH`, `ufw status`.
- **File Permissions**:
  - View: `ls -l`
  - Modify: `chmod`, `chown`
  - Special: `SetUID`, `SetGID`, `Sticky Bit`

## 7. System Admin & Troubleshooting

- **Monitor**:
  - `vmstat`, `htop`, `free -h`
  - `ps aux`, `kill <PID>`
- **Logs**:
  - `/var/log/syslog`, `/var/log/auth.log`, `/var/log/kern.log`
- **Tools**:
  - `strace`, `lsof`, `dmesg`

## 8. Key Commands Table

| Task              | Command                        |
| ----------------- | ------------------------------ |
| Check Memory/CPU  | `vmstat 5 10`, `free -h`       |
| Monitor Processes | `htop`, `ps aux`, `kill <PID>` |
| Restart Services  | `sudo systemctl restart ssh`   |
| Trace Commands    | `strace -c <command>`          |
| List Open Files   | `lsof -p <PID>`                |
| View Logs         | `cat /var/log/syslog` etc.     |
| Set Permissions   | `chmod +x script.sh`           |
| SSH Security      | `ssh-keygen`, `ssh-copy-id`    |
| Enable Firewall   | `sudo ufw enable`              |

---

This summary serves as a quick reference for Linux shell scripting, automation, and system administration.
