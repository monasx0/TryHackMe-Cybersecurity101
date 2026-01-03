# Linux Fundamentals Part 03
## Task 1 - Introduction
This room is showcasing some useful utilities and applications that are likely to be used day-to-day. I am also going to advance my skills by learning about automation, package management, and service/application logging.

Let's proceed!

## Task 2 - Deploy Linux Machine
I’ve logged into the Linux Fundamentals Part 3 machine using SSH and have deployed the AttackBox successfully!

Using the command `ssh tryhackme@machineip` and the provided password `tryhackme`, I have logged into the machine.

## Task 3 - Terminal Text Editors
### Nano
Nano is a simple, user-friendly terminal text editor, ideal for quickly creating or editing text files. If the file exists, Nano opens it; if not, it creates a new file. You can open a file using `nano filename`, type your text, and save it with `Ctrl + O` and exit with `Ctrl + X`. 
### Vim
Vim is a terminal editor designed for efficient text editing. You can open a file with `vim filename`, enter insert mode by pressing `i` to type text, then press `Esc` to switch back to command mode for saving `:w` or exiting `:q`. Vim allows advanced users to navigate and edit files very quickly.
## Task 4 - General/Useful Utilities
### The wget command
The wget command in Linux is used to download files from the internet using protocols like HTTP, HTTPS, or FTP. You can use it by typing `wget` followed by the file URL, for example, `wget http://example.com/file.txt`. It can also resume interrupted downloads and download files in the background.
### Transferring Files From Your Host-SCP (SSH)
Secure copy is just copying files between two devices securely on a remote session and provides both authentication and encryption.
SCP allows us to:
- Copy files & directories from my current system to a remote system
- Copy files & directories from a remote system to my current system
#### Copy files from current system to remote system
`scp myfile.txt user@192.168.1.1:/home/kali/yourfile.txt`
| Value | Variable |
|------| ------------------------------ |
| 192.168.1.1 | IP address of the remote system |
| user | User on the remote system |
| myfile.txt | Name of the file on the current system |
| yourfile.txt | Name that we want to store the file as on remote system |
#### Copy files from remote system to current system
`scp user@192.168.1.1:/home/kali/yourfile.txt myfile.txt`
| Value | Variable |
|------| ------------------------------ |
| 192.168.1.1 | IP address of the remote system |
| user | User on the remote system |
| myfile.txt | Name of the file on the remote system |
| yourfile.txt | Name that we want to store the file as on current system |
### Serving Files From Your Host-WEB
The `python3 -m http.server` is used to quickly start a simple HTTP server in Linux. It shares the current directory over HTTP, allowing other devices on the same network to access files through a web browser. To access the webpage from another device, enter the IP address followed by the port number, such as `http://192.168.1.10:8000`

## Task 5 - Processes 101
### Viewing Processes
We can use `ps` command to get a list of the running processes and some additional information such as their status code, session that is running them, CPU usage time, and the name of the actual program or command that is being executed. The `ps aux` is used to see the processes run by other users and those that don't run from a session. Another useful command is the `top` command that gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics refresh every 10 seconds, also refresh when you use the arrow keys to browse the various rows.
### Managing Processes
To kill a process simply use the `kill` command followed by process ID `kill 765`.
Below are some of the signals that we can send to a process when it is killed:
- SIGTERM-Kill the process, but allow it to do some cleanup tasks
- SIGKILL-Kill the process, but does not allow it to do any cleanup tasks
- SIGSTOP-Stop/suspend a process

### How to Start Services on Boot
To start services on boot, use the command `systemctl start servicename`. We can perform four functions with `systemctl`
* start
* stop
* enable
* disable

## Task 6 - Maintaining Your System: Automation

### Cron Process
Cron processes are those that start during boot, which are responsible for facilitating and managing cron jobs. We can interact with them using the `crontab` command.
Crontabs require six specific values:
| Value | Description |
|----| -------------------------------- |
| MIN | What minute to execute at |
| HOUR | What hour to execute at |
| DOM | What day of the month to execute at |
| MON | What month of the year to execute at |
| DOW | What day of the week to execute at |
| CMD | The actual command that will be executed |

Example usage: `0 */12 * * * cp -R /home/kali/Documents /var/backups`

## Task 7 - Maintaining Your System: Package Management
### Packages & Software Repository
In Linux, software repositories are online storage locations that contain packages ready to be installed. Additional repositories can be added by using the `add-apt-repository` command. Packages are software files that include programs, libraries, and dependencies, and they can be easily installed, updated, or removed using package managers like `apt`.
## Task 8 - Maintaining Your System: Logs
### Logs
Logs in Linux are files that record system activity, errors, and events, helping users and administrators understand what is happening on the system. They are usually stored in the `/var/log` directory.

## Task 9 - Conclusions
After completing this room, I learned:

- Using terminal text editors
- General utilities such as downloading and serving files using a Python web server
- Process management
- Maintaining and automating the system by the use of crontab, package management, and reviewing logs



