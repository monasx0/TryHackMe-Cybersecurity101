# **John the Ripper Basics**
## **Task 1 - Introduction**
**John the Ripper** is a widely used and highly respected **password‑cracking tool** in **cybersecurity**. It is designed to identify **weak passwords** by attempting to crack **hashed credentials** using various **attack techniques**. John is known for its **speed**, **flexibility**, and **support for a large number of hash formats**, making it a standard tool for both **defensive security audits** and **offensive penetration testing**.

## **Task 2 - Basic Terms**
### **What Are Hashes**
A **hash** is a way of converting data of any length into a **fixed‑length value** using a **hashing algorithm**. This process masks the **original data** and produces a value known as a **hash** or **digest**. The same input will always generate the same hash, but the original input cannot be directly recovered from the hash.

Common hashing algorithms include **MD4**, **MD5**, **SHA‑1**, and **NTLM**.

### **What Makes Hashes Secure**
**Hash functions** are designed to be **one‑way**. Calculating a hash from input data is **computationally easy**, but reversing a hash to recover the original input is **computationally infeasible**. This property makes hashing suitable for **password storage** and **integrity verification**.

### **John the Ripper**
Although hashes cannot be reversed, they can be **cracked**. If the hashing algorithm is known, an attacker can hash large numbers of **potential passwords** and compare them against the **target hash**. When a match is found, the **original password** is revealed.

This technique is known as a **dictionary attack** or **brute‑force attack**. **John the Ripper** is a powerful tool designed to perform these attacks efficiently across many different **hash formats**, making it a key tool for testing **password strength** and identifying **weak credentials**.

## **Task 3 - Setting Up Your System**
### **Installation Overview**
**John the Ripper** supports multiple **operating systems**, including **Linux** and **Windows**. There are several versions available, including the standard **core version** and **community editions** that extend functionality. The most widely used and feature‑rich version is **Jumbo John**, which is required for this lesson.

### **Offensive Linux Distributions**
On **offensive Linux distributions** such as **Kali Linux**, **Jumbo John** comes **pre‑installed**. No additional setup is required.

### **Installing on Windows**
On **Windows systems**, **Jumbo John** can be installed by downloading the **precompiled binary archive** for either **64‑bit** or **32‑bit** systems. Once extracted, John can be run directly from the **command line** without compilation.

### **Wordlists**
In addition to **John the Ripper**, **wordlists** are essential for performing **dictionary‑based password attacks**. A wordlist is a collection of **potential passwords** that John hashes and compares against a **target hash**.

On **Kali Linux**, useful wordlists can be found in:
```
/usr/share/wordlists
```

### **RockYou Wordlist**
For all tasks in this room, we will use the well‑known **rockyou.txt** wordlist. This list originates from a **2009 data breach** and contains **millions of commonly used passwords**.

## **Task 4 - Cracking Basic Hashes**
### **Using John the Ripper to Crack Hashes**
The general syntax for running **John the Ripper** is shown below:
```
john [options] [file path]
```
### Automatic Hash Cracking
John includes built-in logic to automatically detect the hash type and select suitable **cracking rules**. While this approach is not always reliable, it is useful when the **hash** format is unknown and you want to attempt cracking quickly.

The syntax for automatic cracking using a wordlist is:
```
john --wordlist=[path to wordlist] [path to file]
```
### Identifying Hash Types
Automatic detection does not always work correctly, especially when different **hash formats** appear similar. In such cases, identifying the hash type manually is essential before cracking.
### Format-Specific Cracking
Once the **hash** type is identified, **John** can be instructed to use a specific format. This improves accuracy and efficiency during cracking.

The syntax for format-specific cracking is:
```
john --format=[format] --wordlist=[path to wordlist] [path to file]
```
### Understanding John Formats
When working with standard **hash types** such as **MD5** or **SHA-1**, **John** often requires the **raw- prefix** (for example, **raw-md5**). This indicates that the **hash** is basic and **unsalted**, rather than part of a structured format.

To view all supported formats, you can run:
```
john --list=formats
```
## **Task 5 - Cracking Windows Authentication Hashes**
### **NTHash / NTLM**
**NTHash**, commonly referred to as **NTLM**, is the hash format used by modern **Windows operating systems** to store **user and service account passwords**.

### **Where NTLM Hashes Are Stored**
On Windows systems, hashes are stored in the **Security Accounts Manager (SAM)** database. In enterprise environments, hashes are stored in **Active Directory** as **NTDS.dit**.

## **Task 6 - Cracking /etc/shadow Hashes**
### **Cracking Hashes from /etc/shadow**
On **Linux systems**, password hashes are stored in `/etc/shadow`. Access is restricted to the **root user**. If access is obtained, hashes may be crackable depending on **password strength** and **hashing algorithm**.

### **Unshadowing Password Files**
John requires a **specific format**, so **/etc/shadow** must be combined with **/etc/passwd** using **unshadow**.

The basic syntax is:
```
unshadow [path to passwd] [path to shadow]
```

### **Cracking the Hashes**
The output can be passed directly into **John the Ripper**, optionally specifying formats such as **sha512crypt**.

## **Task 7 - Single Crack Mode**
### **Single Crack Mode in John the Ripper**
**Single Crack mode** generates password guesses using **username‑based heuristics** rather than a full wordlist.

### **Word Mangling**
**Word mangling** applies transformations like **capitalisation**, **numbers**, and **symbols** to predictable base words.

### **Using Single Crack Mode**
Single Crack mode uses a syntax similar to other John commands, with the addition of the `--single` flag. As always, specifying the correct hash format is critical.

The general syntax is:
```
john --single --format=[format] [path to file]
```
### Important Note on File Format
When using Single Crack mode, **John** requires the hash file to include the **username** associated with each hash. This allows John to generate relevant word mangling rules based on that username.

### Example
A **hash** file entry must be formatted as:
```
john:1efee03cdcb96d90ad48ccc7b8666033
```

## Task 8 - Custom Rules

### Custom Rules in John the Ripper
As you explored **Single Crack mode**, you may have noticed that many **passwords** follow reusable and predictable patterns. Often, users apply the same transformations repeatedly—such as capitalising the first letter or appending numbers and symbols. Custom rules in **John the Ripper** allow you to formalise these observations by defining your own mangling rules, which John then uses to generate password candidates dynamically.

### Where Custom Rules Are Defined
Custom rules are stored in the `john.conf` configuration file.

### Custom Rule Syntax Overview
Each custom rule begins with a rule list definition, which assigns a name to the rule. This name is later used when running John.
```
[List.Rules:RuleName]
```

#### Some commonly used modifiers include
- **Az** — Appends characters to the end of the word
- **A0** — Prepends characters to the beginning of the word
- **c** — Capitalises characters positionally (commonly the first letter)

### Character Sets in Custom Rules
Modifiers define where changes occur, while character sets define what characters are used. Character sets are written inside square brackets `[ ]` and placed inside double quotes `" "`.

#### Common character sets include
- `[0-9]` — Numbers from 0 to 9
- `[A-Z]` — Uppercase letters
- `[a-z]` — Lowercase letters
- `[A-z]` — Both uppercase and lowercase letters
- `[!£$%@]` — Specific symbols

## Task 9 - Cracking Password Protected Zip Files
### Cracking Password-Protected ZIP Files
It is possible to use **John the Ripper** to crack **passwords** protecting **ZIP archives**. As with other protected file types, **John** cannot work with **ZIP** files directly, so we first need to convert the archive into a **hash** format that **John** understands. This is done using a companion tool from the **John suite**, while the cracking process itself uses the same syntax you are already familiar with.

### Zip2John
Similar to the **unshadow** tool used for `/etc/shadow` files, **zip2john** extracts the password hash from a **ZIP archive** and outputs it in a format suitable for **John**.

The general syntax is:
```
zip2john [options] [zip file] > [output file]
```
### Cracking the ZIP Hash
Once the **hash** has been extracted, it can be passed directly into **John** for cracking.

#### **Example** 
```
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

## Task 10 - Cracking Password Protected RAR Archives
The process for cracking a **password-protected** **RAR archive** is very similar to the method used for **ZIP** files. **RAR archives**, commonly created using **WinRAR**, are compressed containers used to bundle and reduce the size of files and folders. Like **ZIP** files, **RAR** archives cannot be cracked directly by **John the Ripper** and must first be converted into a compatible **hash** format.
### Rar2John
To extract a crackable **hash** from a **RAR archive**, we use the `rar2john` tool, which is part of the **John the Ripper** toolset. This utility converts the **RAR** file into a format that **John** can understand.

The basic syntax is:
```
rar2john [rar file] > [output file]
```

### Cracking the RAR Hash
Once the **hash** has been extracted, it can be passed directly into **John the Ripper** for cracking.
**Example**
```
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```
## Task 11 - Cracking SSH Keys with John
### Cracking SSH Key Passwords
While **archive** files are a common target, **John the Ripper** is also frequently used in real-world scenarios to crack **password-protected** **SSH private keys**, typically named `id_rsa`.
### SSH2John
As with **ZIP**, **RAR**, and **shadow files**, **John** cannot work directly with **SSH private keys**. To handle this, we use another conversion tool from the **John suite** called `ssh2john`, which extracts a **hash** from the `id_rsa` file and converts it into a format **John** understands.

If `ssh2john` is not available as a standalone binary, a Python version can be used instead:
- On Kali Linux: `python /usr/share/john/ssh2john.py`.

The general syntax is:
```
ssh2john [id_rsa private key file] > [output file]
```
### Cracking the SSH Key Passphrase
Once the **hash** has been extracted, it can be passed directly to **John the Ripper** for cracking. 
```
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
```

## **Task 12 - Conclusions**
**John the Ripper** is a powerful and flexible **password‑cracking tool** used to test the strength of **hashed credentials** across multiple systems and file formats.  
It supports **dictionary attacks**, **rule‑based mangling**, and **format‑specific cracking**.  
Auxiliary tools like `zip2john`, `rar2john`, and `ssh2john` significantly extend its capabilities.

### **What I Learned**
1. How **hashing** works and why hashes are **one‑way**.  
2. How **John the Ripper** cracks hashes using **dictionary** and **brute‑force techniques**.  
3. How to **identify hash types** and specify correct formats.  
4. How to crack **/etc/shadow** hashes using **unshadow**.  
5. How **Single Crack mode** exploits **predictable passwords**.  
6. How **custom rules** improve cracking efficiency.  
7. How to crack **ZIP**, **RAR**, and **SSH private keys**.


