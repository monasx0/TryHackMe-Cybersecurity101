# Linux Shells

## Task 1 - Introduction
The **Linux Shell** is a program that acts as an interface between the user and the operating system's **kernel**, accepting and interpreting commands to execute programs and manage system resources. It is a powerful **command-line interface** that provides greater control and **automation** capabilities through **scripting**.

## Task 2 -  How to Interact with a Shell?
Here are some of the basic commands that will help you interact with a shell.
#### Change Directory
To change directory, use the `cd` command.
#### Print Working Directory
To display the working directory, use the `pwd` command.
#### List the Contents of a Directory
To list the contents of a directory, use the `ls` command.
#### Display the Contents of a File
To display the contents of a file, use the `cat` command.
#### Search for a Specific Word in a File
To search for a specific word in a file, use the `grep` command.

## Task 3 - Types of Linux Shells

In **Linux**, there are different types of **shells** available, each **shell** provides its own features and characteristics.

By default, multiple **shells** are installed in most **Linux** distributions. To see which **shell** you are using and all available **shells**, type the `echo $SHELL` and `cat /etc/shells` commands.

### Change Shell 
#### Temporarily
To change the **shell** temporarily, type the shell as listed in the `/etc/shells` directory. 

**Example**: `pwsh` will change your shell to **PowerShell**.
#### Permanently
To change the **shell** permanently, type `chsh -s /usr/bin/pwsh`.
**Example**: `chsh -s /usr/bin/zsh` will change your **shell** to **PowerShell** permanently.

### Common Shells
In **Linux**, there are several types of **shells** available. Each **shell** has its own features and strengths, making it suitable for different tasks. Below are three popular shells you might encounter:

#### Bash (Bourne Again Shell)
**Bash** is the most common **Linux shell**. It is simple, stable, and works on almost every Linux system. **Bash** is great for scripting, automation, and general command-line tasks. Beginners often start with **Bash** because of its wide support and many online tutorials.

#### Fish (Friendly Interactive Shell)
**Fish** is designed to be user-friendly and modern. It comes with features like auto-suggestions, syntax highlighting, and smart tab completion by default. Fish is perfect for users who want a friendly interactive **shell** without much configuration.

#### Zsh (Z Shell)
**Zsh** is a powerful **shell** that combines the features of **Bash** and **Fish**. It supports scripting like Bash but also has interactive features like Fish. Zsh is highly customizable with themes and plugins, making it ideal for users who want a feature-rich and personalized shell experience.

## Task 4 - Shell Scripting and Components
### Shell Script
Basically, a **Shell Script** is a set of commands that a user writes in a special file and then the computer reads those commands and executes them.

The file must be named with the extension `.sh`. It is the default extension for bash scripts.

### Creating Shell Scripts
A shell script starts with a shebang (#!) followed by the shell path, like #!/bin/bash. It tells the system which shell should run the script.

Once you know how to create a shell script, the next step is learning how to control its behavior. Variables let you store and reuse data, loops help you repeat tasks automatically, and conditional statements let your script make decisions based on certain conditions.

#### Variables
Think of a variable like a box where you store something. You can give it a name and put anything inside.

**Example**: `name="Alice"`. The command `echo $name` displays the value of the name that we stored before.
#### Loops
Loops let you repeat tasks automatically in a script. They save time by running the same commands multiple times.

**Example**:
```bash
for i in 1 2 3; do
  echo "Step $i"
done
```
#### Conditional Statement
Conditional statements let your script make decisions based on certain conditions. They run different commands depending on whether a condition is true or false.

```bash
if [ $name = "Alice" ]; then
  echo "Hello Alice"
fi
```

## Task 5 - The Locker Script
### The Locker Script
The **Locker Script** is a small program that checks whether a user is allowed to open a locker.
It asks the user for their **name**, **company name**, and **PIN**.
If the entered details are correct, access is allowed; otherwise, access is denied.
This script helps us understand how **variables** store information, **loops** repeat tasks, and **conditional statements** make decisions.

### Script
```bash
#!/bin/bash

# Asking user details
echo "Enter your Username:"
read username

echo "Enter your Company name:"
read companyname

echo "Enter your PIN:"
read pin

# Checking the entered details
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful. You can now access your locker, John."
else
    echo "Authentication Denied!!"
fi
```
### Script Execution
```bash
user@ubuntu:~$ ./locker_script.sh
Enter your Username:
John
Enter your Company name:
Tryhackme
Enter your PIN:
1349
Authentication Denied!!
```
#### Summary
- The **Locker Script** checks whether a user is allowed to open a locker.
- It asks for the **username**, **company name**, and **PIN**.
- The **script** saves these details and compares them with the correct values.
- If all details match, access is allowed.
- If any detail is wrong, access is denied.

## Task 6 - Conclusion
In this room, we learned about **Linux shells** and their main types. We explored **shell** scripting and saw how it can automate tasks. Finally, we created some practical **scripts**, including one that checks user input, helping us understand how scripts work in real-world scenarios.

#### What I Learned
- The role and types of **Linux shells** (**Bash**, **Zsh**, **Fish**).
- How to write **shell** **scripts** to automate tasks.
- Using **variables** to store information in **scripts**.
- How **loops** and **conditional statements** control **script** flow.
- How to apply scripting knowledge in practical exercises like the Locker Script.
