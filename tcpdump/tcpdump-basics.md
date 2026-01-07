# **Tcpdump Basics**

## Task 1 - **Introduction**
**Tcpdump** is a **command-line** **packet capture** tool built on the **libpcap library**, developed in **C/C++** for **Unix-like systems** in the late 1980s/1990s. It is **stable**, **fast**, and forms the **foundation** for many modern **networking tools**. It has also been ported to **Windows** as **WinPcap**.

## Task 2 - **Basic Packet Capture**
### **Capture Packets on an Interface**

```
tcpdump -i INTERface
```
Captures **packets** on a specified **network interface** (e.g., -i eth0 for **Ethernet** or -i any for **all interfaces**).

### **Save Captures to a File**

```
tcpdump -w FILE
```
Saves captured **packets** to a **file** (usually .pcap) for later **analysis**.

### **Read Captured Files**
```
tcpdump -r FILE
```
Reads and displays **packets** from a previously saved **PCAP file**.

### **Limit Number of Packets**
```
tcpdump -c COUNT
```
Captures only a specific number of **packets**, then stops automatically.

### **Disable Name Resolution**
```
tcpdump -n / -nn
```
Avoids resolving **IP addresses** and **ports** to **domain names** or **protocol names**, making the **output** faster and easier to **read**.

## Task 3 - **Filtering Expressions**
**Tcpdump** allows **filtering captured packets** based on **hosts**, **ports**, **protocols**, or **logical conditions**. This helps **analysts** focus on **relevant traffic** and reduce **noise** in large **captures**.

### **Host Filtering**
```
tcpdump host HOSTNAME
```
Captures **packets** involving a specific **host**. Use `src host HOST` or `dst host HOST` to filter **source** or **destination traffic**.

### **Port Filtering**
```
tcpdump port PORT_NUMBER
```
Captures **packets** on a specific **port**. Use `src port` or `dst port` for finer **filtering**.

### **Protocol Filtering**
```
tcpdump PROTOCOL
```
Filters **packets** by **protocol**, such as **tcp**, **udp**, **icmp**, etc.

### **Logical Operators**
**Tcpdump** supports **logical operators** to combine **filter conditions**:

- **and** – captures **packets** matching **both conditions**.
```
tcpdump host 1.1.1.1 and tcp
```
- **or** – captures **packets** matching **either condition**.
```
tcpdump udp or icmp
```
- **not** – captures **packets** excluding a **condition**.
```
tcpdump not tcp
```

### **Reading Captured Files**
To filter **packets** from a saved **file**, use:
```
tcpdump -r FILE -c COUNT -n
```

## Task 4 - **Advanced Filtering**
**Tcpdump** supports **advanced filtering** using **packet lengths**, **binary operations**, and **header bytes** to capture **specific traffic patterns**. This is useful for **network troubleshooting** and **security analysis**.

### **Packet Length Filtering**
```
tcpdump greater LENGTH
tcpdump less LENGTH
```
Capture **packets** above or below a specific **length** and allows **analysts** to focus on **unusually large** or **small packets**.

### **Binary Operations**
Filters can use **binary operators** (`&`, `|`, `!`) on **protocol headers** to match specific **bits** in **packet fields**.

#### **Common Binary Operators**
- **&** (**AND**) – returns 1 if **both bits** are 1.
- **|** (**OR**) – returns 1 if **either bit** is 1.
- **!** (**NOT**) – inverts the **bit** (1 → 0, 0 → 1).

**Example**:
```
tcp[tcpflags] == tcp-syn
```

### **Header Byte Filtering**
**Tcpdump** allows **filtering packets** based on the contents of **header bytes** using the syntax:
```
proto[expr:size]
```

### **TCP Flags Filtering**
**TCP flags** can be filtered using:
```
tcp[tcpflags]
```

#### **Available TCP Flags**
- **tcp-syn** – Synchronize
- **tcp-ack** – Acknowledge
- **tcp-fin** – Finish
- **tcp-rst** – Reset
- **tcp-push** – Push

## Task 5 - **Displaying Packets**
**Tcpdump** allows you to **customize** the **display** of captured **packets** to make **analysis easier** and more **readable**.

### **Common Display Options**
- `-q` (**Quick output**) – Shows brief **information** about each **packet**.
- `-e` (**MAC addresses**) – Displays **source** and **destination MAC addresses**.
- `-A` (**ASCII**) – Shows **packet contents** in **ASCII format**, useful for **reading text protocols**.
- `-xx` (**Hexadecimal**) – Displays **packet data** in **hexadecimal format**.
- `-X` (**Hex + ASCII**) – Shows both **hexadecimal** and **ASCII representations** of **packet data**.

Using **ASCII** or **Hex** + **ASCII** options helps **analysts** inspect **payload data** for **protocols** like **HTTP**, **FTP**, or **SMTP**.

**Example**:
```
sudo tcpdump -i eth0 -c 5 -q
```
This command shows a brief **summary** of each **packet captured**.

## Task 6 - **Conclusions**
**Tcpdump** is a **lightweight** and **powerful command-line tool** for capturing and analyzing **network packets**. It allows **filtering traffic** by **host**, **port**, **protocol**, or **TCP flags** and supports **reading/writing PCAP files** for later **analysis**. **Custom display options** like -q, -e, -A, -xx, -X make **packet data easier** to understand. Using **Tcpdump** helps **visualize network behavior** and **troubleshoot issues** efficiently.

### **What I Learned**
- How to **capture packets** on **specific interfaces** and **limit the number of packets**.
- How to **filter traffic** using **hosts**, **ports**, **protocols**, and **logical conditions**.
- How to **read/write PCAP files** for **analysis**.
- How to **customize packet display** and **interpret packet headers** for **network troubleshooting**.
