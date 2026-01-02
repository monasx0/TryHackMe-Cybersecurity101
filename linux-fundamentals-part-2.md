# Limux Fundamentals Part 02

## Task 1 - Introduction
In this journey, I will explore flags, arguments, and advanced filesystem operations. I am navigating these tasks to build my understanding of these important concepts.
In this room I will cover:
1. Learn first few commands using flags and arguments
2. Advance knowledge of the filesystem
3. Running first few scripts and executables

## Task 2 - Accessing Linux machine using SSH
### What is SSH?
Secure Shell is a protocol between devices in an encrypred form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network. Once it reaches the remote machine it is then unencrypted.
- SSH allows us to execute commands remotely on another device
- Any data sent between devices is encrypted when it is sent over a network
### Deploying Linux machine
To connect to a device remotely using SSH. We need the device username, password, and ip address. After knowing all of this we can use the command,`ssh user@192.168.1`. Proceeding this command I need to type the password. After this I am now remotely connected to the device.

## Task 3 - Introduction to Flags and Switches
Flags and switches are command-line parameters in Linux that modify a command's behavior, add functionality, or control output formatting. Usually prefixed by one or two hyphens, they allow us to customize how programs run.
| commands | Description |
|----------| ------------|
|ls --all| shows directories that are hidden eg. `."hidden"`
|man ls| displays manual page that includes documentation system for commands and  functions|
## Task 4 - Filesystem Interaction Continued
Here are some commands that I learned throughout this room:
| commands | Full name | Description |
|----------| ----------| ------------|
|touch|touch|creates a file|
|mkdir|make directory| creates a folder|
|cp|copy|copy a file or folder|
|mv|move|move a file or folder|
|rm|remove|delete a file or folder|
|file| file|determine the type of a file|

## Task 5 - Permission101
In Linux, permissions decide who can read, write, or run files and folders. Users and groups help manage these permissions so the right people can access the right things.
When I use `ls -l` it shows file permissions, the number of links, the owner, the group, and other details.
| Value | Meaning |
|------ | ------- |
|-rw-r--r--| File type and permissions |
|1| Number of hard links to the file |
|user| Owner of the file |
|group| Group of the file |
|1024| File size in bytes |
|Jan 02 13:45| Last modified date and time |
|myfile| Name of the file |


