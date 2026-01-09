# Metasploit Introduction

## Task 1 - Introduction
**Metasploit** is the most widely used **exploitation framework** in **cybersecurity**. It is a powerful platform that supports all phases of a **penetration testing** engagement, starting from information gathering and **scanning**, through **exploitation**, and ending with **post-exploitation** activities.


## Task 2 - Main Components of Metasploit
### Metasploit Console (msfconsole)
When using the **Metasploit Framework**, your primary point of interaction is the **Metasploit Console**, known as **msfconsole**. The console serves as the central interface where you load, configure, and execute different Metasploit modules. Almost all **Metasploit** activities are performed through this **console**.

### Metasploit Modules
**Modules** are small, reusable components within the **Metasploit Framework**. Each **module** is designed to perform a specific task, such as:
- **Exploiting** a **vulnerability**
- **Scanning** a target
- Performing **brute-force attacks**
- Executing **post-exploitation** actions
### Advanced Concepts
#### Vulnerability
A **vulnerability** is a weakness in a system caused by poor design, coding errors, or logical flaws. If **exploited**, it can allow attackers to:
- Disclose sensitive information
- Execute unauthorized commands
- Gain access to the system
#### Exploit
An **exploit** is a piece of code that takes advantage of a **vulnerability** present on the target system to trigger unintended behavior.
#### Payload
A **payload** is the code that runs on the target system after an **exploit** succeeds. **Payloads** define what action is performed, such as:
- Opening a **shell**
- Executing **commands**
- Creating a backdoor
- Running a benign program (e.g., **calc.exe**) as proof of **code execution**

### Metasploit Module Categories
**Metasploit modules** are organized into categories for easier navigation. These **modules** are accessed and managed through **msfconsole**, even though they physically exist in the framework’s directory structure.

#### Auxiliary Modules
**Auxiliary modules** provide supporting functionality and do not directly **exploit vulnerabilities**. They include:
- Scanners
- Crawlers
- Fuzzers
- Information-gathering tools
- Denial-of-Service testing modules

These **modules** are commonly used during **reconnaissance** and **enumeration** phases.
#### Encoder Modules
**Encoders** are used to encode **payloads** and **exploits** to help bypass signature-based **antivirus** detection. 
**Signature-based security** solutions compare files against known malware signatures. **Encoding** may help avoid detection, but its effectiveness is limited because modern antivirus solutions perform additional behavioral analysis.
#### Evasion Modules
**Evasion modules** are designed specifically to bypass security controls, such as **antivirus** software and **application whitelisting**. 
Unlike **encoders**, **evasion** modules actively attempt to avoid detection techniques, though their success depends on the target environment.
#### Exploit Modules
**Exploit** **modules** contain code that targets known **vulnerabilities**. They are neatly organized based on the target operating system or platform, such as:
- Windows
- Linux
- Android
- Web applications
- Multi-platform exploits

These **modules** are the core of **Metasploit’s exploitation** capabilities.
#### NOP Modules
**NOPs** (**No OPeration instructions**) do nothing when **executed**. In **Intel x86 architecture**, a **NOP** instruction is represented by `0x90`. They are commonly used as buffers to:
- Pad payloads
- Maintain consistent payload sizes
- Improve exploit reliability
#### Payload Modules
**Payloads** define what happens after successful **exploitation**.

Examples include:
- Opening a command shell
- Establishing a reverse connection
- Running a command
- Uploading malware or backdoors

Having an interactive **shell** is often the goal, as it allows continuous command **execution** on the target system.
### Payload Types
**Metasploit** organizes **payloads** into four categories:
- Adapters
- Singles
- Stagers
- Stages
#### Adapters
**Adapters** wrap payloads into different formats.

**Example**: wrapping a payload into a **PowerShell command** for **execution**.

#### Singles
**Single** (**inline**) **payloads** are self-contained and do not require additional downloads.

**Examples**:
- Adding a user
- Launching notepad.exe
#### Stagers
**Stagers** establish an initial connection between **Metasploit** and the target.
They download the remaining **payload** (**stage**) after **execution**.

#### Stages
**Stages** are the main **payload** components downloaded by **stagers**.
They allow larger and more complex payloads to be delivered.
### Identifying Single and Staged Payloads
- **Single** (**Inline**) **Payload**
```
generic/shell_reverse_tcp
```
- **Staged Payload**
```
windows/x64/shell/reverse_tcp
```
The **underscore** (**_**) indicates a **single payload**, while the **slash** (**/**) indicates a **staged payload**.

## Task 3 - Msfconsole
The **Metasploit Console**, known as **msfconsole**, is the primary interface for interacting with the **Metasploit Framework**.

Once started, the **console** displays the **Metasploit** banner along with version details and available **module** statistics. The **command prompt changes** to **msf6 >** (**or msf5 >, depending on the version**), indicating that **Metasploit** is ready for use.

### Using msfconsole Like a Linux Shell
The **Metasploit console** behaves similarly to a **Linux command-line shell**. You can execute many standard **Linux commands** directly from msfconsole.

### Help System in msfconsole
- `help` → displays general help
- `help <command>` → displays help for a specific command (e.g., help set)


### Using a Module (Example: MS17-010 EternalBlue)
**Modules** are loaded using the `use` command.
```
use exploit/windows/smb/ms17_010_eternalblue
```
After loading a **module**, the **prompt** changes to show the active context. You are not entering a directory, but a **module** context.
### Viewing Module Options
The `show options` command displays required and optional parameters for the active module.
#### Example parameters

- `RHOSTS` – target system(s)
- `RPORT` – target port
- `LHOST` / `LPORT` – listener settings for payloads

### Sessions in Metasploit
A **session** represents an active connection to a compromised system.

### Listing Available Payloads
The `show payloads` command lists **payloads** compatible with the selected **exploit**.

Payloads define what happens after exploitation, such as:
- Opening a shell
- Running commands
- Launching Meterpreter
### Searching for Modules
The search command is one of the most powerful features in Metasploit.

You can search by:
- CVE number
- Exploit name
- Target platformsearch ms17-010
- Module type
**Example**:
```
search ms17-010
```


## Task 4 - Working with modules
### Setting Module Parameters
After selecting a **module** using the `use` command, you must configure its parameters. Each module requires specific parameters to function correctly.
```
set PARAMETER_NAME VALUE
```
### Understanding Metasploit Prompts
**Metasploit** operates using different **prompts**, each indicating a specific context. Recognizing them is essential to avoid mistakes.

#### 1. Regular System Shell Prompt
```
root@ip-10-10-XX-XX:~#
```
#### 2. msfconsole Prompt
```
msf6 >
```
#### 3. Module Context Prompt
```
msf6 exploit(windows/smb/ms17_010_eternalblue) >
```
#### 4. Meterpreter Prompt
```
meterpreter >
```
#### 5. Target System Shell
```
C:\Windows\system32>
```
### Setting Parameters
To set the target **IP address**:
```
set RHOSTS 10.10.165.39
```
After setting parameters, always re-run:
```
show options
```
### Commonly Used Parameters
- **RHOSTS** – Target IP address, range, CIDR notation, or file
- **RPORT** – Target service port
- **PAYLOAD** – Code executed after exploitation
- **LHOST** – Attacker machine IP
- **LPORT** – Listening port for reverse connections
- **SESSION** – Existing session ID for post-exploitation modules
### Unsetting Parameters
- Remove a **single** **parameter**
```
unset PARAMETER_NAME
```
- Clear all **parameters**
```
unset all
```
### Global Parameters with setg
The `setg` command sets **global values** that persist across **modules**.

- Clear global values using
```
unsetg PARAMETER_NAME
```
### Run Module
Once **parameters** are configured, **execute** the **module** using:
```
exploit
```
or use
```
run
```
### Background Execution
```
exploit -z
```
- Runs the **exploit**
- Automatically backgrounds the **session** after success
### Backgrounding a Session
```
background
```
or
```
CTRL + Z
```
### Listing Active Sessions
```
sessions
```
### Interacting with a Session
```
sessions -i SESSION_ID
```

## Task 5 - Conclusions
As discussed throughout this lesson, **Metasploit** is a powerful **framework** that simplifies and streamlines the **exploitation** process during **penetration** **testing**.

### What I Learned
- Learned the purpose and core features of the **Metasploit Framework**
- Understood the exploitation process: **find**, **configure**, and **exploit**
- Gained experience using **msfconsole** and **Metasploit modules**
- Learned the roles of **vulnerabilities**, **exploits**, and **payloads**
- Practiced selecting and using different **payload types**, including **reverse shells**
