# Metasploit Meterpreter
## Task 1 - Introduction
**Meterpreter** is a powerful **Metasploit** **payload** that supports the **penetration testing** process by providing many valuable **post-exploitation** capabilities. It runs directly on the target system and acts as an agent within a **Command** and **Control** (**C2**) **architecture**.

Once deployed, **Meterpreter** allows the attacker to interact with the target **operating system**, access **files**, and **execute commands** using its specialized **Meterpreter commands**. These commands are designed specifically for **post-exploitation** activities.
## Task 2 - Meterpreter Types

### Meterpreter Payload Types
**Meterpreter payloads** also come in both:
- Staged
- Inline (stageless) versions

Additionally, **Meterpreter** offers a wide variety of versions depending on the target **operating system** and **environment**.
### Listing Available Meterpreter Payloads
The easiest way to view available Meterpreter payload versions is by using `msfvenom`.
```
msfvenom --list payloads | grep meterpreter
```
### Supported Platforms
**Meterpreter** **payloads** are available for the following platforms:
- Android
- Apple iOS
- Java
- Linux
- macOS (OSX)
- PHP
- Python
- Windows

### Choosing the Right Meterpreter Version
Your choice of **Meterpreter payload** is usually based on three main factors:
#### 1. Target Operating System
- Is the target running Windows, Linux, macOS, or Android?
- Architecture (x86, x64, ARM, etc.) also matters.
#### 2. Available Components on the Target
- Is Python installed?
- Is the target a PHP-based website?
- Is Java available?
#### 3. Network Connectivity Constraints
- Are raw TCP connections allowed?
- Is only HTTP/HTTPS reverse communication possible?
- Are IPv6 connections less monitored than IPv4?
### Payload Limitations Based on Exploits
When Meterpreter is used through an **exploit module**, your **payload** choices may be restricted by that **exploit**.

Some exploits come with a default **Meterpreter payload**.

**Example**: **MS17-010** (**EternalBlue**)
```
msf6 > use exploit/windows/smb/ms17_010_eternalblue
[*] Using configured payload windows/x64/meterpreter/reverse_tcp
msf6 exploit(windows/smb/ms17_010_eternalblue) >
```
### Viewing Compatible Payloads
You can list all compatible **payloads** for an **exploit** using:
```
show payloads
```
## Task 3 - Meterpreter Commands & Post-Exploitation with Meterpreter

### Help Menu
Typing `help` in any active **Meterpreter** **session** will display a list of all available **commands** for that specific **Meterpreter version**.
```
meterpreter > help
```
Each Meterpreter version supports different commands depending on the target **operating system**, **architecture**, and **payload type**.

### Meterpreter Tool Categories
**Meterpreter** provides three primary categories of tools:

- Built-in commands
- Meterpreter tools
- Meterpreter scripting

These tools run directly in memory on the target system and do not require dropping additional **files** to **disk**, which helps with **stealth**.

### Meterpreter Command Groups
When you run the `help` command, **Meterpreter commands** are grouped into the following categories:

- Core commands
- File system commands
- Networking commands
- System commands
- User interface commands
- Webcam commands
- Audio output commands
- Elevate commands
- Password database commands
- Timestomp commands
### Core Meterpreter Commands
**Core commands** are essential for **session control**, **navigation**, and **post-exploitation** workflow.

- `background` – Sends the current session to the background
- `exit` – Terminates the Meterpreter session
- `guid` – Displays the session’s GUID (Globally Unique Identifier)
- `help` – Displays the help menu
- `info` – Shows information about a Post module
- `irb` – Opens an interactive Ruby shell
- `load` – Loads Meterpreter extensions
- `migrate` – Moves Meterpreter to another process
- `hashdump` – extracts password hashes from the SAM database
- `run` – Executes a Meterpreter script or Post module
- `sessions` – Switches between active sessions

### File System Commands
Used to **navigate**, **read**, and **manipulate files** on the **target system**.

- `cd` – Change directory
- `ls` / dir – List files in the current directory
- `pwd` – Display the current working directory
- `edit` – Edit a file
- `cat` – Display file contents
- `rm` – Delete a file
- `search` – Search for files
- `upload` – Upload files or directories
- `download` – Download files or directories

### System Commands
Used to **control processes**, gather **system info**, and **execute commands**.
- `clearev` – Clear event logs
- `execute` – Execute a command
- `getpid` – Show current process ID
- `getuid` – Show the user Meterpreter is running as
- `kill` – Terminate a process
- `pkill` – Terminate processes by name
- `ps` – List running processes
- `reboot` – Reboot the target system
- `shell` – Drop into a system command shell
- `shutdown` – Shut down the target system
- `sysinfo` – Display system information (OS, architecture, etc.)
## Task 4 - Conclusions
**Meterpreter** is a powerful **Metasploit payload** designed to support the **post-exploitation** phase of **penetration testing**. It operates in **memory** and provides **extensive control** over the target system without writing **files** to **disk**. Through **staged** and **stageless payloads**, **Meterpreter** adapts to different **operating systems**, **architectures**, and **network conditions**. Mastering **Meterpreter commands** is essential for effective **system interaction**, **privilege assessment**, and **post-exploitation** activities.
### What I Learned
- How **Meterpreter** works as a post-exploitation payload
- **Staged** and **stageless** **Meterpreter payloads**
- Different **Meterpreter versions** for different platforms
- Core **Meterpreter commands**
- How to dump **hashes** and search for **files**
- How to choose the correct **payload**
  
