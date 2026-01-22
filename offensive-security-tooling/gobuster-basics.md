# Gobuster Basics

## Task 1 - Introduction to Gobuster

### Gobuster
**Gobuster** is a tool used for **reconnaissance** (gathering information). In the world of cybersecurity, it is like a digital private investigator. It helps you find "hidden" parts of a website or a network that aren't immediately visible to a regular visitor.


### Learning Goals
In this module, we will learn how to:
* Find hidden **folders** and **files** on a website.
* Discover **subdomains** (like `blog.example.com`).
* Find **virtual hosts** (different websites living on the same server).
* Use a **wordlist** to automate the searching process.


---

## Task 2 - How Gobuster Works

Gobuster uses two main concepts to find information:

1. **Enumeration:** This simply means making a list of everything that is available. 
2. **Brute Force:** This is trying every possibility until one works. 
   * *Example:* If you have a locked door and a bag of 100 keys, trying every key until the door opens is "brute forcing."

### Wordlists
Instead of keys, Gobuster uses a **wordlist** (a text file full of common names for folders or subdomains). It tries them one by one to see which ones actually exist on the server.

### Basic Options (Flags)

| Short Flag | Long Flag | Description |
| :--- | :--- | :--- |
| **-t** | `--threads` | How many "workers" run at once. More = faster. |
| **-w** | `--wordlist` | Tells Gobuster which file of words to use. |
| **-o** | `--output` | Saves your results into a text file. |
| **-u** | `--url` | The website address you are attacking. |

---

## Task 3 - Finding Folders (Directory Mode)

The `dir` mode is used to find hidden folders like `/admin` or `/backup`.

### Example Command
```bash
gobuster dir -u [http://example.thm](http://example.thm) -w /usr/share/wordlists/dirb/small.txt
```
#### What this does:
- `dir`: Tells Gobuster to look for directories (folders).
- `-u`: The target website URL.
- `-w`: The list of folder names to try.
- `-x`: (Optional) Look for specific file types like `.php` or `.js`.

## Task 4 - Finding Subdomains (DNS Mode)
Sometimes a company has extra websites like `dev.example.com` or `test.example.com`. We use dns mode to find these.
### Example Command
```bash
gobuster dns -d example.thm -w /path/to/subdomains.txt
```
## Task 5 - Virtual Hosts (Vhost Mode)
Virtual Hosts are different websites that all live on the same server IP.

### DNS vs Vhost
- DNS Mode: Checks with a DNS server to see if a name exists.
- Vhost Mode: Talks directly to the web server and asks, "Do you have a website named 'X'?" by changing the Host Header in the request.

#### Example Command
```bash
gobuster vhost -u http://MACHINE_IP -w /path/to/wordlist.txt --append-domain --domain example.thm --exclude-length 250
```
## Task 6 - Conclusion
This room taught us how to use Gobuster to:
- Enumerate Directories (`dir`) to find hidden web folders.
- Enumerate Subdomains (`dns`) to find extra website addresses.
- Enumerate Virtual Hosts (`vhost`) to find websites sharing the same server.
