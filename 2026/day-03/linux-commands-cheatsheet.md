# Linux Commands Cheat Sheet for DevOps

## 📁 File System & Disk Management
1. `ls -lah`: List all files (including hidden) with detailed info and human-readable sizes.
2. `find /var/log -type f -name "*.log"`: Search for files by type and name within a specific directory.
3. `df -h`: Show available and used disk space across all mounted filesystems.
4. `du -sh *`: Calculate and display the total disk space used by each file/folder in the current directory.
5. `chmod 755 script.sh`: Modify file permissions (e.g., to make a shell script executable).
6. `chown user:group config.yml`: Change the ownership and group of a file or directory.

## 📝 Log Analysis & Text Processing
7. `tail -f /var/log/syslog`: Continuously output the end of a file (essential for watching live logs).
8. `grep -ir "error" /var/log/`: Recursively search for the string "error" (case-insensitive) across all files in a directory.
9. `awk '{print $1}' access.log`: Extract and print the first column/field of a file (great for parsing IP addresses).
10. `sed -i 's/old_ip/new_ip/g' config.txt`: Find and replace a string in-place within a file.
11. `cat data.txt | wc -l`: Count the total number of lines in a file or standard output.
12. `less config.json`: View large files interactively without loading the entire file into memory at once.

## ⚙️ Process Management
13. `ps aux | grep nginx`: Snapshot all running processes and filter for a specific application name to find its PID.
14. `top` *(or `htop`)*: Display real-time system performance, CPU/Memory usage, and running processes.
15. `kill -9 <PID>`: Send a SIGKILL signal to forcefully terminate an unresponsive process.
16. `pkill -f node`: Kill all processes matching a specific command name or pattern.
17. `nohup ./long-job.sh &`: Run a command in the background that continues running even if the SSH session disconnects.

## 🌐 Network Troubleshooting
18. `ip addr` *(or `ip a`)*: Display all network interfaces and their assigned IP addresses.
19. `curl -Iv https://api.example.com`: Fetch HTTP headers and verbose connection details (perfect for testing endpoints without a browser).
20. `nc -zv 10.0.0.5 3306`: Test if a specific TCP port (e.g., MySQL) is open and accepting connections on a remote host.
21. `dig +short mydomain.com`: Query DNS servers to check how a domain name is resolving.
22. `ss -tulpn`: Show all active listening ports and the processes bound to them.
