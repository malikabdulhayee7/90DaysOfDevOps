# Linux Architecture, Processes, and systemd

## Core Architecture Components
1. **Hardware:** The physical or virtualized CPU, RAM, and storage.
2. **Kernel:** The core software that talks directly to the hardware. It manages memory, CPU scheduling, and hardware drivers. 
3. **User Space:** The isolated environment where user applications, shells, and daemons run. It cannot access hardware directly and must make "system calls" to the kernel.
4. **Init / systemd:** The very first process started by the kernel (always PID 1). It is responsible for bootstrapping the rest of the user space and managing background services.

## Process Management & States
A process is a running instance of a program. In Linux, new processes are typically created using the `fork()` system call (which duplicates the parent process) followed by `exec()` (which replaces the duplicate with the new program).

**Core Process States:**
* **Running (R):** The process is currently executing on the CPU or in the run queue waiting for its turn.
* **Sleeping (S / D):** 
  * *Interruptible (S):* Waiting for an event or signal (can be woken up).
  * *Uninterruptible (D):* Deep sleep, usually waiting for hardware I/O. Cannot be killed immediately.
* **Stopped (T):** Execution suspended, often by a user signal (e.g., pressing `CTRL+Z`).
* **Zombie (Z):** The process has finished executing, but its parent hasn't read its exit status yet. It consumes a process ID but no CPU/RAM.

## The Role of systemd
`systemd` is the modern standard init system and service manager for Linux. 
* **Why it matters:** It manages daemons (background services like Docker, Nginx, or SSH). It parallelizes service startup for faster boots, handles dependencies (e.g., ensuring the network interface is up before starting a web server), and centralizes logging via `journald`.
* For a DevOps engineer, `systemd` is the primary interface for ensuring applications stay running, automatically restart on failure, and start in the correct order.

## 5 Daily Use Commands
1. `systemctl status <service>`: Check the health, uptime, and recent logs of a background service.
2. `journalctl -u <service> -f`: Continuously tail the live logs for a specific systemd service.
3. `top` / `htop`: Monitor real-time CPU/memory usage and process states.
4. `ps aux | grep <name>`: Take a snapshot to find the Process ID (PID) of a specific application.
5. `kill -9 <PID>`: Send the SIGKILL signal to forcefully terminate an unresponsive process.
