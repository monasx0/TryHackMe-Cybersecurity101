# Linux Fundamentals Part 01

## Task 1 - Introduction to Linux
Most of us use **Windows** or **macOS** machines, both of which differ in visual design and operation. Just like Windows, iOS, and macOS, Linux is another operating system, and one of the most popular in the world — powering smart cars, Android devices, supercomputers, home appliances, enterprise servers, and more.

In this room, I will cover some history of Linux and also:
1. Learn essential commands
2. Search for files and explore basic shell operators

## Task 2 - Background of Linux
### Where is Linux used?
Linux is used for its superior security, privacy, customization, and stability. It is a free and open-source operating system.
#### Linux is used in:
1. Internet Infrastructure and Servers
2. Mobile Devices (Android)
3. Supercomputers
4. Automotive Industry

### Linux Distributions
Linux refers to a family of UNIX-like operating systems. Linux is a free and open-source operating system, created in 1991, that allows anyone to view, modify, and redistribute its source code.
Ubuntu and Debian are some common distributions of Linux

## Task 3 - Interaction with the machine (Browser-Based) 
In this room, I can interact with an Ubuntu Linux machine directly in my browser. Simply press the Start Machine button and wait for the system to deploy.

## Task 4 - Running First Few Commands
In Linux, tasks are often performed using the command line instead of a GUI, which allows faster and more precise system control.
| Command | Description |
|------| ------------------------------ |
| echo | outputs any text provided after the command |
| whoami | outputs the current working user |

## Task 5 - Interacting with the Filesystem
In this section, I practiced essential Linux commands used for file navigation, system interaction, and data searching through the command line.
| Command | Description |
|----| -------------------------------- |
| ls | list everything in the directory |
| cd | change directory |
| cat | displays the contents of a file |
| pwd | print my current working directory |

Additionally, I learned the tree command that displays the tree structure starting from a specified directory path.

## Task 6 - Searching files
### Use of Find:
Using this command I can find something on my machine just by typing  `find -name filename.txt`
What if I don't know the file name I only know that it ends with the extension say `.txt`. So I can easily find it by just typing the command ` find -name "*.txt"`
The symbol `*` known as a wildcard can help me list everything that ends with the extension `.txt`
### Use of Grep:
Grep is a command that helps us find specified content of the file.

Usage: `grep requiredtext filename.txt`
## Task 7 - Shell Operators
I learned some basic operators that would help me in the future
| Command | Description |
|---| ----------------------------------------------------------|
| & | this operator allows us to execute commands in the background |
| && | execute the second command if the first command succeeds |
| > | Writes output to a file and replaces old content |
| >> | Writes output to a file without deleting old content |
## Task 8 - Conclusion
I've covered quite a bit for my first interactions with Linux. These are the essential commands and functions I'll be using whenever I interact with a Linux machine.

### What I Learned:
- Why Linux is so commonplace today  
- Interacting with my first Linux machine  
- Running fundamental Linux commands  
- Navigating the filesystem efficiently  
- Using `find` and `grep` to locate data quickly  
- Important shell operators to power up commands

