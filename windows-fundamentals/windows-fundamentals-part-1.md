# Windows Fundamentals Part 01

## Task 1 - Windows Editions
Windows has evolved over decades. Windows XP (2001) brought a stable, user-friendly interface. Windows 7 (2009) improved performance, security, and introduced Aero visuals. Windows 10 (2015) unified PC and tablet experiences with regular updates and Cortana integration. Windows 11 (2021) introduced a modern, centered UI, rounded corners, and better multitasking with Snap layouts, focusing on productivity and security. Each edition built upon the last with improved usability and features.

## Task 2 - The Desktop (GUI)
A Desktop GUI (Graphical User Interface) lets users interact with the computer visually instead of using only commands. Its main parts include:
| Component | Description |
| --------- | ----------- |
| The Desktop | The main screen area where icons, files, and shortcuts are displayed. |
| Start Menu | Central hub to access programs, settings, and recently used files. |
| Search Box | Lets users quickly find apps, files, or settings. |
| Task View | Displays all open windows and virtual desktops for multitasking. |
| Taskbar | Shows running apps, pinned shortcuts, and allows quick navigation. |
| Toolbars | Small panels on the taskbar providing quick access to specific tools/features. |
| Notification Area | Displays system alerts, background apps, and quick settings like volume/network. |

## Task 3 - Introduction to Windows
Windows is a complex operating system with many files, utilities, and features. This module gives a general overview of the OS, helps navigate the interface, and shows how to manage system settings, aimed at users who want to use Windows more confidently.

## Task 4 - The File System
The file system used in modern versions of  Windows  is the New Technology File System or simply  NTFS .  
Before NTFS, there was  FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System). 
NTFS overcomes many limitations of earlier file systems; such as:
- Supports files larger than 4GB
- Sets specific permissions on folders and files
- File and folder compression
- Provides Encryption ( Encryption File System or **EFS** )

Below is the list of permissions that you can set to files and folders to grant or deny access on **NTFS**.
- Full control
- Modify
- List folder contents
- Read
- Write
- Read and Execute

#### How can you view the permissions for a file or folder?
1. Right click the file or folder you want to check
2. From the context menu, select `Properties`.
3. In the `Properties` section, click on the `Security` tab.
4. In the Group or user names list, select the user,groups, or computers whose permissions you want to view.

#### Alternate Data Streams (ADS)
ADS is a feature of the Windows NTFS file system that allows a file to contain more than one stream of data. By default, Windows Explorer does not show ADS, but they can be viewed using PowerShell or other tools.

## Task 5 - The Windows\System32 Folders
#### Windows Folder and System32
The Windows folder `C:\Windows` contains the core files of the operating system, though it can reside on other drives or locations. Its path is stored in the system environment variable `%windir%`. Inside the Windows folder, the **System32** folder holds critical system files required for Windows to function. Modifying or deleting files in System32 can make the OS inoperable, so caution is essential. Many built-in Windows tools are located in this folder.

## Task 6 - User Accounts, Profiles, and Permissions

#### User Account Types
On a local Windows system, there are two main user account types:
1. Administrator
2. Standard User

- **Administrator**: The highest-privilege account type, capable of performing any action on the system. This includes adding or removing users, modifying groups, changing system settings, installing software
- **Standard User**: The account type with limited privileges, able to modify only their own files and folders, but unable to perform system-level changes such as installing programs or managing other users

#### Viewing User Accounts
To see the existing user accounts:
1. Click the Start Menu and type Other Users.
2. Select the shortcut to System Settings > Other Users.
3. **Administrators** will see an option to Add somone else to this PC. **Standard Users** will not see this option.

Clicking on a local user account allows you to Change account type or Remove the account. The drop-down box in Change account type shows the current account type.

#### User Profiles
When a new user logs in for the first time, Windows creates a user profile under `C:\Users\Username`.
Each user profile contains default folders such as:
- Desktop
- Documents
- Downloads
- Music
- Pictures
Windows displays a **User Profile Service** message during initial login while creating the profile.

#### Local Users and Groups
Administrators can manage users and groups through **Local Users** and **Groups Management**:
1. Right-click the **Start Menu**, click **Run**, and type `lusrmgr.msc`.
2. The console displays two sections: **Users** and **Groups**.
- **Groups** list all local groups and their descriptions
- Users can be assigned to one or more groups, inheriting the permissions of those groups

## Task 7 - User Account Control

#### Local Administratos and Security Risks
Most home users run Windows as a **Local Administrator**, giving full system control. Running constantly with these privileges increases the risk of malware infections, as malicious programs can run with the same permissions.
#### User Account Control (UAC)
**UAC** protects the system by prompting for permission when tasks need elevated privileges. Programs show a shield icon, and confirmation or credentials are required to proceed, helping prevent unauthorized changes.
#### How UAC Works
1. Programs requiring higher privileges display a **shield icon** on their default icon.
2. When such a program is run, a **UAC prompt** appears asking the administrator to confirm or enter credentials.
3. If no action is taken, the program does not execute, preventing unauthorized system changes.

## Task 8 - Settings and the Control Panel
#### System Settings and Control Panel
- **Control Panel**: The traditional interface for system management, used for tasks like adding printers, uninstalling programs, or accessing advanced settings.
- **Settings Menu**: Introduced in Windows 8 for touch devices, now the primary interface in Windows 10 and later for most system changes.

### Viewing Installed Applications
To check installed programs:
- `Open Control Panel → Programs → Programs and Features`
This lists all installed software along with publisher names and versions, helping verify what’s on the system.
#### Tips for Finding Settings
- Use the Start Menu search to locate specific settings quickly.
- Clicking a search result opens either Settings or Control Panel, depending on the task.

## Task 9 - Task Manager

#### Task Manager
The **Task Manager** provides information about running applications and processes, including system resource usage such as **CPU** and **RAM**, which can be viewed under the **Performance tab**.
- Access Task Manager by right-clicking the taskbar.
- By default, it opens in **Simple View**, showing limited information. Click **More details** to view all running processes, performance metrics, and additional deatails.
## Task 10 - Conclusions
This module provided a practical overview of the Windows operating system, focusing on its structure, tools, and user management. It helped me understand how to navigate the system, manage accounts, maintain security, and monitor system performance effectively.
#### What I Learned
- Different user account types and their privileges (Administrator and Standard User)
- The purpose and functioning of **User Account Control** (**UAC**)
- How to use **Settings** and **Control Panel** to configure the system
- Viewing and managing installed applications
- Using the **Task Manager** to monitor running processes and system performance




