# **Nmap Basics**
## **Task 1 - Introduction**
**Nmap** (**Network Mapper**) is a powerful and flexible **open-source network scanning tool** used to discover **live hosts** and running **network services** on a network. Instead of relying on slow and limited manual methods like **ping**, **arp-scan**, or **telnet**, **Nmap** efficiently scans large networks and thousands of ports to identify **active devices** and **services** such as **SSH** and **web servers**. First released in **1997**, **Nmap** has evolved into a reliable tool widely used for **network discovery**, **service enumeration**, and **security assessment**.

## **Task 2 - Host Discovery (Who Is Online)**
**Host discovery** is the process of identifying which **devices** (**hosts**) are alive and reachable on a network before performing deeper scans.

### **Target Specification in Nmap**
**Nmap** provides multiple ways to define **scan targets**, allowing flexibility when scanning **single hosts**, **ranges**, or entire **networks**.

#### **IP Range**
**Example**: `192.168.0.1-10`  
Scans **IP addresses** from 192.168.0.1 to 192.168.0.10.

#### **Subnet**
**Example**: `192.168.0.1/24`  
Scans all **IP addresses** in the **subnet** `192.168.0.0–255`.

#### **Hostname**
**Example**: `example.thm`  
Allows scanning targets using **DNS hostnames** instead of **IP addresses**.

### **Ping Scan**
The `-sn` option performs a **host discovery scan** without scanning **ports** or **services**.

**Main Takeaways:**
- Determines whether a **host** is **up** or **down**
- Does not perform **service enumeration**
- Generates less **network noise**

### **Scanning a Local Network**
A **local network** is one you are directly connected to, such as via **Ethernet** or **WiFi**.

#### **How Nmap Works Locally**
- Sends **ARP requests** to discover **hosts**
- Devices responding to ARP are marked as **“Host is up”**

### **Scanning a Remote Network**
A **remote network** is separated by one or more **routers** from the scanning system.

#### **How Nmap Discovers Hosts Remotely**
- Uses **ICMP echo (ping)**
- **ICMP timestamp requests**
- **TCP probes** (**SYN** and **ACK**) on common ports (e.g., 80, 443)

### **List Scan**
A **list scan** `-sL` displays the **targets** that would be scanned, without sending any probes.

**Example**: `nmap -sL 192.168.0.1/24`  

#### **Purpose**
- Verify **targets** before scanning
- Prevent accidental scanning of unintended **networks**

## **Task 3 - Post Scanning (Who Is Listening)**

### **Service Discovery (Port Scanning)**
**Service discovery** identifies **network services** running on **live hosts** by checking which **TCP** or **UDP ports** are open.

### **TCP Port Scanning**
**TCP port scanning** checks whether a **TCP port** is **open**, **closed**, or **filtered** by interacting with the **TCP protocol**.

### **Connect Scan**
The **connect scan** `-sT` attempts to complete the **TCP three-way handshake** with each **target port**.

#### **How It Works**
- **SYN → SYN-ACK → ACK**
- If successful, the **port** is **open**
- **Nmap** then closes the connection

### **SYN Scan (Stealth Scan)**
A **SYN scan** `-sS` sends only a **TCP SYN packet** and does not complete the **three-way handshake**.

#### **How It Works**
- **Open port** → SYN-ACK → **Nmap sends RST**
- **Closed port** → RST-ACK

### **UDP Port Scanning**
**UDP scanning** `-sU` checks for **services listening** on **UDP ports**, which do not use **connection-based communication**.

### **Common UDP Services**
- **DNS**
- **DHCP**
- **NTP**
- **SNMP**
- **VoIP**

### **Fast Mode**
**Fast mode** `-F` scans the **100 most common ports** instead of the default **1,000**.

### **Port Range Selection**
**Port range selection** `-p` specifies exactly which **ports** to scan.

**Example**: `nmap -p10-1000` Scan **ports 10 through 1000**.

## **Task 4 - Version Detection (Extract More Information)**

### **OS Detection**
**OS detection** `-O` attempts to identify the **operating system** running on a **target host** by analyzing multiple **network behavior indicators**.

#### **Main Takeaways**
- **Device type** → General classification of the system
- **Running** → Estimated **OS family** and version range
- **OS details** → More precise **OS version guess**
- **Network Distance** → Number of **hops** between scanner and target

### **Service and Version Detection**
**Service and version detection** `-sV` identifies which **services** are running on **open ports** and determines their **software versions**.

### **Combined OS and Version Detection**
The `-A` option enables **aggressive scanning**, combining multiple **advanced features** into one command.

#### **Includes:**
- **OS detection** `(-O)`
- **Service and version detection** `(-sV)`
- **Traceroute**
- **Additional discovery scripts**

### **Forcing a Scan**
The `-Pn` option skips **host discovery** and treats all **targets** as **online**.

#### **Why It’s Needed**
- Some **hosts** block **ICMP** and appear **offline**
- Ensures **port scanning** proceeds regardless of **discovery results**

### **Summary of Important Nmap Options**
|Option| Explanation|
| ---- | -----------|
| `-O` | **OS detection** |
| `-sV` | **Service and version detection** |
| `-A` | **OS detection, version detection, and additional features** |
| `-Pn` | Scan **hosts** that appear to be **down** |

## **Task 5 - Timing (How Fast is Fast)**
**Nmap** provides multiple options to control **scan speed**, **aggressiveness**, and **network load**, helping avoid detection by **IDS/IPS systems** and adapt to different **network conditions**.

### **Why It Matters**
- Fast scans may trigger **security alerts**
- Slow scans reduce **noise** but take more **time**
- Proper **timing** balances **stealth**, **accuracy**, and **speed**

### **Timing Templates**
**Timing templates** define how aggressively **Nmap** sends **probes** during a scan.

#### **Available Timing Levels**
|Template| Name| Description |
| ---- | -----------| ------ |
| `-T0` | **Paranoid** | Extremely slow, maximum stealth |
| `-T1` | **Sneaky** | Very slow, IDS evasion |
| `-T2` | **Polite** | Reduces bandwidth and load |
| `-T3` | **Normal** | Default behavior |
| `-T4` | **Aggressive** | Faster scans, higher noise |
| `-T5` | **Insane** | Extremely fast, high detection risk |

### **Effect of Timing on Scan Duration**
Using the same **SYN scan** on **100 common ports** (`-sS -F`), scan duration varies greatly based on **timing**.

#### **Example Results**
|Template| Duration |
| ---- | -----------|
| T0 (**Paranoid**) | ~9.8 hours |
| T1 (**Sneaky**) | ~27.5 minutes |
| T2 (**Polite**) | ~40.5 seconds |
| T3 (**Normal**) | ~0.15 seconds |
| T4 (**Aggressive**) | ~0.13 seconds | 
| T5 (**Insane**) | slightly faster than T4, but unreliable |

#### **Important Note about T5**
- **T5** is intentionally omitted in many labs because:
- It is too aggressive
- Results vary heavily by **network**
- **Packet loss** can cause missed **ports** or **false negatives**

## **Task 6 - Output (Controlling What You See)**
### **Verbosity (-v)**
Enables **real-time scan progress** and shows what **Nmap** is doing internally during different **scan phases** such as **host discovery**, **DNS resolution**, and **port scanning**.

### **Debugging (-d)**
Provides **debug-level output** for deep technical insight into how **Nmap** operates internally.

### **Saving Scan Reports**
**Nmap** allows saving **scan results** in different **formats** for **analysis**, **automation**, and **reporting**.

#### **Normal Output (-oN)**
**Human-readable output**, similar to what appears in the terminal.
```
-oN <filename>
```
#### XML Output (-oX)
Structured output suitable for **automation**, **parsing**, and **tools**.
```
-oX <filename>
```
#### Grepable Output (-oG)
Optimized for use with **grep**, **awk**, and **scripting**.
```
-oG <filename>
```
#### All Formats (-oA)
Saves results in all major formats at once using a single base name.
```
-oA <basename>
```
#### Summary
| Option | Description |
| ------ | ----------- |
| `-v` | Enable verbose output |
| `-d` | Enable debugging output |
| `-oN` | Normal output |
| `-oX` | XML output |
| `-oG` | Grepable output | 
| `-oA` | Save all output formats |

## **Task 7 - Conclusions**
**Nmap** is a powerful and flexible **network scanning tool** that helps identify **live hosts**, discover **open ports**, detect **services** and **versions**, and even guess the **operating system** of **target devices**. Its options for **verbosity**, **debugging**, and **output formats** make it suitable for both **real-time monitoring** and detailed **reporting**. Proper use of **timing templates**, **parallelism**, and **packet rates** allows you to balance **speed**, **stealth**, and **accuracy** during scans.

### **What I Learned**
- How to discover **live hosts** on a network
- How to identify **open ports** and running **services**
- How to understand the difference between **TCP** and **UDP communication**
- How **operating systems** can be fingerprinted through **network behavior**
- How **scan results** help in **security analysis** and **penetration testing**


