# Windows Command Line

## Task 1 - Introduction

Before mastering **Command Line Interface** (**CLI**) everyone prefers **Graphical User Interface**. However, when you learn Command Line, you will find it faster and more efficient. There can be many advantages to using **CLI** over **GUI** except speed and efficiency. I will mention a few:
- **Lower resource usage**: CLI requires low system resources. It is easy to use **CLI** on old hardware or systems with limited memory.
- **Automation**: Automation using commands is much easier than using **GUI**.
- **Remote management**: Remote management works well on **CLI**. Using **SSH** on the CLI is convenient for managing a remote system such as a server or a router.

## Task 2 - Basic System Information

### System Info
You can run the `systeminfo` command to list various information about the system such as OS information, system details, processor and memory. You can pipe it through `more`. If the output is too long. Then you can view it page by page by pressing the **space bar**.
Use `driverquery | more` to see installed drivers and their properties as page after page. You can exit it using `CTRL+C`.
Some important commands to know:
- `help` - Provides help menu for a specific command
- `cls` - Clears the Command Prompt screen.

## Task 3 - Network Troubleshooting

### Network Configuration
You can check the network statistics using command `ipconfig`. This command displays the **IP address**, **subnet mask**, and **default gateway**.
To view additional information such as DNS and to ensure that DHCP is enabled, you can use the command `ipconfig /all`. It lists detailed information about your network.
### Network Troubleshooting
A common troubleshooting task is to check if the device can access a particular server on the internet. To do this, use the `ping example.com` command. This command sends an ICMP packet and listens for a response from the server. If server responds, it confirms that we can access it on the internet.

#### More Networking Commands
The command `tracert example.com` traces the **network route** used to reach the target. The command `nslookup example.com` gives you additional information about the domain or **IP address**. 
The `netstat` command displays current network connections and listening ports. If you have a connection with a device, it will be listed here.
If you are curious about using these commands with a parameter you can use `-h` after the command to display the help menu.

## Task 4 - File and Disk Management

### Working With Directories

To display **current working directory**, use `cd` command without parameters. You can view **child directories** using `dir` command. You can also use parameters with this command:
- `dir /a` - Displays hidden and system files.
- `dir /s` - Displays files in the current directory and all subdirectories.

To visually represent the child directories, use the `tree` command. To change the directory, use `cd target_directory` command. You can use `cd ..` to go back one directory.

To create a directory, use `mkdir dir_name`. To delete a directory, use `rmdir dir_name`.

### Working With Files
You can easily view the text files, using `type` command. This command will dump the contents of the files on the screen. You can also pipe it using `more` to view longer text files.

The `copy` command copies files from one location to another.
Similarly, the `move` command will move the file from one location to another.

To delete a file, use `del` or `erase` command.

We can use the wildcard character `*` to refer multiple files. The `copy *.txt C:\Desktop` command will copy every file with the extension `.txt` and paste it into  the **Desktop** directory.

## Task 5 - Task and Process Management

To list the running processes, use `tasklist` command. If you want to kill a process, use `taskkill /PID target_pid` command.

To view the help menu and usage, use `tasklist /?` command.

## Task 6 - Conclusions
In this room, we focused on the most practical commands for accessing a networked system over the command line. You should know that the command line can be used for other tasks.

- **chkdsk**: checks the file system and disk volumes for errors and bad sectors.
- **driverquery**: displays a list of installed device drivers.
- **sfc /scannow**: scans system files for corruption and repairs them if possible.
#### What I Learned
- Basic system information can be accessed using commands like `systeminfo` and `driverquery`.
- Networking commands such as `ipconfig`, `ping`, `tracert`, and **netstat** help troubleshoot connections.
- File and directory management is easy with commands like `cd`, `dir`, `mkdir`, `copy`, and `del`.
- Task and process management can be done using `tasklist`, `taskkill`, and help commands like `/?`.





