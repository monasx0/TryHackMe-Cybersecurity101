# Windows Fundamentals Part 02

## Task 1 - Introduction

This room will attempt to provide an overview of some other utilities available within the Windows operating system and different methods to access these utilities.

## Task 2 - System Configuration and Advanced System Settings
#### System Configuration (MSConfig)
The **System Configuration utility** (**MSConfig**) is a tool for advanced troubleshooting, primarily used to diagnose startup issues. You need local administrator rights to open this utility.
#### Launching MSConfig
MSConfig can be launched from the Start Menu or the Run dialog. The utility has five main tabs:
- General - Select which devices and services load at startup
- Boot - Configure operating system boot options
- Services - Lists all services on the system, whether running or stopped
- Startup - Startup items are managed here
- Tools - Provides quick access to various system utilities

#### Advanced System Settings
Windows provides additional configuration for performance and system recovery through Advanced System Settings.
#### Performance Options
- Page file acts as extra virtual memory when physical RAM is full, preventing slowdowns or crashes.
- Displays page file location, initial and maximum size, and whether Windows manages it automatically.

#### Startup and Recovery
- Configures crash dump settings for critical system errors
- Determines how much information Windows saves when a crash occurs, assisting in troubleshooting

## Task 3 - Change UAC Settings

#### User Account Control (UAC) Security Levels
The UAC slider sets how Windows notifies you when apps or users try to make system-level changes. There are four levels:
- **Always notify** - Highest security. Windows alerts you for all changes and dims the desktop
- **Notify for apps** - Alerts only when apps make changes, notifications are not triggered by user changes
- **Notify without dimming** - Same as *Notify for apps*, but the desktop is not dimmed
- **Never notify** - Notifications are disabled, Windows does not warn about any changes

## Task 4 - Computer Management

### Computer Management
The Computer Management utility organizes system administration tools into three main sections:
- System Tools
- Storage
- Services & Applications

#### System Tools
##### Task Scheduler
- Allows automated tasks such as running applications or scripts at a specific time, on logon/logoff, or on a schedule
- View existing tasks under **Task Scheduler Library**

##### Event Viewer
- Provides logs of system events, useful for diagnosing issues and auditing activity
- Standard logs include Application, Security, Setup, System, and Forwarded Events

##### Device Manager
- View and configure hardware; disable or enable devices as needed.
#### Storage
##### Disk Management
Perform advanced storage tasks such as:
- Setting up new drives
- Extending or shrinking partitions
- Assigning or changing drive letters

#### Services and Applications
##### Services
- Services are background applications that run automatically or manually

Startup types:
- **Automatic**: Starts at system boot
- **Manual**: Starts when triggered
- **Disabled**: Does not start at all
##### Windows Management Instrumentation Control
WMI Control manages Windows Management Instrumentation, enabling system management and monitoring through tools like PowerShell.

## Task 5 - System Information

#### System Information
**System Information** (**msinfo32**) is a built-in Windows utility that collects and displays detailed information about a system’s hardware, components, and software environment. It is mainly used to view system specifications.

#### System Summary
The **System Summary** section provides general technical details about the computer, such as the processor, system model, and installed memory. The information here is grouped into three main categories:
- Hardware Resources
- Components
- Software Enviroment

#### Searching in msinfo32
At the bottom of the msinfo32 window, a search bar allows you to quickly locate specific information. Selecting **Components** and searching for **IP Address** will display relevant network details.

## Task 6 - Resource Monitor
#### Resource Monitor
**Resource Monitor** (**resmon**) is a built-in Windows utility used to view detailed, real-time information about system resource usage. It helps monitor how processes are using **CPU**, **memory**, **disk**, and **network** resources and is commonly used for advanced troubleshooting.

In the **Overview tab**, Resource Monitor displays four main sections:
- CPU
- Disk
- Network
- Memory

Each tab provides more detailed and specific information related to it.

## Task 7 - Command Prompt

#### Command Prompt (cmd)
In early operating systems, the command line was the only way users could interact with the system. When the graphical user interface (GUI) was introduced, it allowed users to perform tasks using visual elements instead of typing commands. Despite this, the command prompt remains a powerful way to interact directly with the operating system.

#### Network and Troubleshooting Commands
The **ipconfig** command is commonly used to view network configuration details such as IP addresses and adapters. Most commands include a built-in help manual that can be accessed using `/?`, for example `ipconfig /?`.

Another useful command is `netstat`, which displays active network connections and protocol statistics.

The `net` command is used to manage network resources and supports multiple sub-commands. To view its help menu, use `net help`, and for specific sub-commands such as user management, use `net help user`.
The command `cls` is used to clear the command prompt screen.

## Task 8 - Registry Editor

#### Windows Registry
The **Windows Registry** is a central, hierarchical database used by Windows to store configuration information for users, applications, and hardware. It stores important data such as:
- User profiles
- Installed applications
- Hardware and device information
- File associations and system settings

To open the registry, **press Win + R**, type `regedit`, and press **Enter**.

## Task 9 - Conclusion
In this room, I explored Windows tools that help monitor, configure, and troubleshoot the system. I learned how to check system performance, manage users, and tweak settings safely using built-in utilities.
#### What I Learned
- Use **System Configuration** (**msconfig**) to troubleshoot startup and system settings
- Navigate **Computer Management** tools like Task Scheduler, Event Viewer, and Disk Management
- Monitor resources with **Resource Monitor** (**resmon**)
- Run basic **Command Prompt** (**cmd**) commands to get system and network info
- Understand the **Windows Registry** and access it safely with `regedit`
