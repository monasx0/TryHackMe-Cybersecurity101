# Hydra
## Task 1 - Hydra Introduction

### Hydra
**Hydra** is a powerful tool used for **password cracking**. It works by trying many different **passwords** automatically until it finds the correct one. This process is called **brute forcing**.

Instead of manually typing hundreds or thousands of **passwords** to log into a system, **Hydra** does it automatically for you at high speed. It's commonly used to test the security of **login systems** like **SSH**, **FTP**, **web forms**, and many other services.
### How Does Hydra Work?
**Hydra** takes a list of possible **passwords** (called a **wordlist**) and tries each one until it finds the right **password**. This helps security professionals test if a system is using weak or common **passwords** that could be easily guessed by attackers.
### Supported Protocols

**Hydra** can attack many different types of **login services** and **protocols**, including:

- **SSH**: Secure Shell (remote server access)
- **FTP**: File Transfer Protocol
- **HTTP/HTTPS**: Web-based login forms
- **MySQL**: Database login
- **RDP**: Remote Desktop Protocol
- **SMTP**: Email server login

### Why Strong Passwords Matter

**Hydra** demonstrates why using **strong passwords** is crucial. If your **password** is:
- Common (like "password123")
- Short (less than 8 characters)
- Without **special characters** (like !@#$%)

Then it can be easily cracked by tools like **Hydra** in minutes or even seconds!

Many default systems use weak **credentials** like `admin:admin` or `admin:password`. These should always be changed immediately to prevent unauthorized access.

### Installing Hydra

**Hydra** comes pre-installed on **Kali Linux** (popular penetration testing distribution)

If you're using another **Linux distribution** like **Ubuntu** or **Fedora**, you can install **Hydra** using your package manager with the `apt` or `dnf` command.

---

## Task 2: Using Hydra

### Basic Hydra Command Structure

The way you use **Hydra** depends on what **service** you're attacking. The basic structure involves specifying:
- The **username** to try
- The **password list** to use
- The **target IP address**
- The **service/protocol** to attack

### Example 1 (Attacking FTP)

If you want to **brute force** an **FTP** server with **username** `user` and a **password list** called `passlist.txt`, use:
```bash
hydra -l user -P passlist.txt ftp://MACHINE_IP
```
---

### Example 2 (Attacking SSH)

**SSH** (Secure Shell) is commonly used for remote server access. Here's how to attack it with **Hydra**:
```bash
hydra -l  -P  MACHINE_IP -t 4 ssh
```

#### Understanding the Options

| Option | What It Does |
|--------|--------------|
| `-l` | Sets the **username** you want to try |
| `-P` | Points to the **password list** file |
| `-t` | Sets how many **attempts** to run at the same time (threads) |
| `ssh` | Specifies we're attacking the **SSH** service |

#### Example Usage
```bash
hydra -l root -P passwords.txt MACHINE_IP -t 4 ssh
```
---

### Example 3 (Attacking Web Login Forms)

Many websites have login pages where users enter their **username** and **password**. **Hydra** can attack these too!

First, you need to know:
- Is it a **GET** or **POST** request? (Check your browser's **Developer Tools** → **Network** tab)
- What is the login page URL?
- What are the form field names for **username** and **password**?
- What message appears when login fails?

#### Basic Command Structure
```bash
sudo hydra <username> <wordlist> MACHINE_IP http-post-form "<path>:<login_credentials>:<invalid_response>"
```

#### Understanding the Options

| Option | What It Does |
|--------|--------------|
| `-l` | The **username** to try |
| `-P` | The **password list** to use |
| `http-post-form` | Tells **Hydra** this is a **POST** form (most login forms use POST) |
| `<path>` | The login page URL (like `/login.php` or just `/`) |
| `<login_credentials>` | The form field names (like `username=^USER^&password=^PASS^`) |
| `<invalid_response>` | Text that appears when login fails (like "incorrect" or "failed") |
| `-V` | Shows detailed output for each attempt (verbose mode) |

#### Example Usage
```bash
hydra -l admin -P passwords.txt MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```

**What this does:**
- Tries to log in with **username** `admin`
- Uses all **passwords** from `passwords.txt`
- Targets the main page `/` (the homepage)
- `^USER^` gets replaced with the **username** (admin)
- `^PASS^` gets replaced with each **password** from the list
- Looks for the word "incorrect" in the response to know when login failed
- Shows detailed output for each attempt with `-V`

#### Attacking Non-Standard Ports

If the website runs on a different **port** (not the default port 80), add the `-s` option:
```bash
hydra -l admin -P passwords.txt MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -s 8080 -V
```

This attacks a web server running on **port 8080** instead of the default port.

---

### Summary

**Hydra** is a powerful tool for testing **password** security by automatically trying many **passwords** quickly. At the end of this module you now know how to:
- Attack **SSH** services
- Attack **FTP** services  
- Attack **web login forms**
- Use **wordlists** for **brute force** attacks
- Customize **Hydra** commands for different scenarios

---
