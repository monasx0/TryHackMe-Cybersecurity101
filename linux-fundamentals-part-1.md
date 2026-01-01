# Linux Fundamentals Part 01

## Task 1 - Introduction to Linux
We are likely using a **Windows** or **Mac** machine, both of which differ in visual design and operation. Just like Windows, iOS, and MacOS, Linux is another operating system, and one of the most popular in the world — powering smart cars, Android devices, supercomputers, home appliances, enterprise servers, and even more.

In this room we cover some history of Linux and also:
1. Learn essential commands
2. search for files and explore basic shell operators

## Task 2 - Background of Linux
### where is linux used?
It is likely fair to say that Linux is more intimidating than OSs like Windows, but it is lightweight, has its own advantages over other OSs
where Linux is used include:
1. Internet Infrastructure and Servers
2. Mobile Devices (Android)
3. Supercomputers
4. Automotive Industry
5. Linux Distributions

### Linux Distributions
Linux actually refers to UNIX-based operating systems. Linux is a free and open source operating system created in 1991 that allows anyone to view, modify and redistribute its source code.
Ubuntu and Debian are some common distributions of linux

## Task 3 - Interaction with machine (Browser-Base) 
In this room, you can interact with Ubuntu Linux directly in your browser
To do this simply press start machine button and wait for the machine to deploy

## Task 4 - Running First Few Commands
We often use command line instead of graphical user interface because it uses less resource and it can be faster to use commands rather than using GUI.
Commands I Learnt:
1. echo     output any text i put after it
2. whoami   output the current user

## Task 5 - Interacting with Filesystem
I can do really cool things that i do in GUI like:
1. ls      list everything in the directory
2. cd      change directory
3. cat     concatenate
4. pwd     print my current working directory

Additionally i learnt the tree command that displays the tree structure starting from a specified directory path.

## Task 6 - Searching files
### Use of Find:
I can find something on my machine just by using find -name filename.txt
But if i dont know the file name i only know that it end with the extension say ".txt". So i can esaily find it by just typing the command find -name *.txt
The symbol * known as wildcard can help me list up everything that ends with the extension .txt
### Use of Grep:
Grep is a command that help us find content of the file.
Usage: grep requiredtext filename.txt
## Task 7 - Shell Operators
I learnt some basic operators that would help me in future
1. &      this operator allows us to execute commands in background
2. &&     execute the second command if the first command succeeds
3. '>'     it takes input and save that input into the given file, also it will overwrite if something is written in the file
4. '>>'     same as > but it will append the output to the bottom of the file rather than replacing content

