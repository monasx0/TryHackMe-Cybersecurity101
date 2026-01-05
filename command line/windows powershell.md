# Windows PowerShell

## Task 1 - Introduction
### PowerShell
The **Windows Command Prompt** (**CMD**) was limited in its ability to manage systems and perform advanced automation. **CMD** supports basic commands and simple batch scripts, it lacks the power needed for modern system administration.

**PowerShell** was created to address these limitations. It allows administrators to manage computers and infrastructure more erficiently using advanced scripting, automation, and object-based commands that **CMD** cannot provide. In simple words, **PowerShell** is much more powerful than **CMD**.

Throughout this lesson, we are learning to:
- Understand what **PowerShell** is and its capabilities
- Understand the basic structure of **PowerShell's** language
- Learn and run some basic commands


## Task 2 - Objects in PowerShell
To proceed further in **PowerShell**, we first need to understand what an object is.
In programming, an object is an item that contains properties and behavior. For example, a car has properties such as color, model, horsepower, fuel type, and interior features.

Similarly, in **PowerShell**, an object is a fundamental unit that encapsulates data and functionality, making it easier to manipulate information. A **PowerShell** object can contain data such as file names, usernames, and passwords, and it can also perform functions like copying data or starting a process.

## Task 3 - PowerShell Basics
**PowerShell** commands are known as `cmlets` (command-lets). They are much powerful than **Windows commands** and can perform advanced data manipulaton.

To run **PowerShell**, press `Windows + R` and type `powershell` and hit Enter.
### Basic Cmdlets
To retrieve the list of all **cmdlets**, functions and aliased that can be executed in **PowerShell**, use `get-command` command. We can also filter commands property by just executing `Get-Command -CommandType "Function"`. 

You can display the help page using the Get-Help command. For example, to get help about a specific command, you can use Get-Help Get-Date.

To perform tasks more quickly, **PowerShell** provides aliases. Aliases are shortcuts that act as alternatives to full cmdlet names and are commonly used for quick navigation and simple tasks. For example, dir is an alias for Get-ChildItem, and cd is an alias for Set-Location.
#### Where to Find Additional PowerShell Cmdlets
You can find additional **PowerShell** cmdlets using Find-Module, which searches for modules online that contain new commands. If you don’t know the exact name, you can use wildcards. For example, `Find-Module *Azure*` lists all modules with “Azure” in their name.


## Task 4 - Navigating the File System and Working with Files

To create an item in **PowerShell**, you need to specify the path and the type of item.

**For example**: `New-Item -Path ".\Desktop\New Folder" -ItemType "Directory"`. This command creates a new folder named “New Folder” on the Desktop.

To remove an item in **PowerShell**, use the `Remove-Item` cmdlet and specify the path of the item.

For example: `Remove-Item -Path ".\Desktop\New Folder"`. This command deletes the folder named “New Folder” from the Desktop.

To work with files in **PowerShell**, you can use the following cmdlets:
- **Copy-Item**: Copies a file or folder to a new location. Example: `Copy-Item -Path ".\file.txt" -Destination ".\Backup\file.txt"`
- **Move-Item**: Moves a file or folder to a new location. Example: `Move-Item -Path ".\file.txt" -Destination ".\Archive\file.txt"`
- **Get-Content**: Displays the contents of a file. Example: `Get-Content -Path ".\file.txt"`

## Task 5 - Piping, Filtering and Sorting Data
### Piping
**Piping** in **PowerShell** sends the output of one command as input to another command. 
**Example**: 
`Get-Process | Sort-Object CPU`

This takes the list of running programs and sends it to the sort command so the programs are arranged by CPU usage.

### Filtering

Filtering in **PowerShell** lets you pick only the items you need from a list. **Example**: 
`Get-Service | Where-Object -Property Status -eq Running`.

This command lists only the services on your computer that are currently running.

### Sorting Data
Sorting in **PowerShell** means arranging data in order, like alphabetically or numerically. **Example**: `Get-Process | Sort-Object CPU -Descending`

This lists all processes sorted by CPU usage, with the highest usage first.

## Task 6 - System and Network Information
In **PowerShell**, you can gather system and network information using a few key commands. `Get-ComputerInfo` shows detailed information about your computer, like OS version, memory, and hardware. `Get-LocalUser` lists all user accounts on the system. For network details, ipconfig or `Get-NetIPConfiguration` displays IP addresses, subnet masks, and gateway information, helping you check and troubleshoot your network setup.

## Task 7 - Real-Time System Analysis
In **PowerShell**, real-time system analysis lets you monitor and check your computer’s current state. `Get-Service` shows all services running or stopped on your system. `Get-NetTCPConnection` lists active network connections, helping you see which programs are using the network. `Get-FileHash` calculates a file’s hash value, which is useful for verifying file integrity or detecting changes in real time.

## Task 8 - Scripting
In **PowerShell**, scripting allows you to automate tasks and run commands on local or remote computers. The `Invoke-Command` cmdlet is used to execute a script or command on one or more remote machines, making it powerful for system administration.

**For example**: `Invoke-Command -ComputerName Server01 -ScriptBlock { Get-Process }`

This command runs `Get-Process` on the remote computer named `Server01` and returns the list of running processes to your local session.

## Task 9 - Conclusions
**PowerShell** is a powerful tool for managing and analyzing your system and network. With commands for filtering, sorting, real-time monitoring, and remote scripting, it helps automate tasks, check system status, and work efficiently across multiple computers.

### What I Learned

- **Data management** to organize and extract the information efficiently.
- **System and network information** to check computer details and network settings.
- **Real-time system analysis** to monitor the current state and activity of the system.
- **Scripting and remote execution** to automate tasks and run commands on other computers.

