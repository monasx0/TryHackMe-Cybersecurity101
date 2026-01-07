# Wireshark Basics

## Task 1 - Introduction
**Wireshark** is a **powerful**, **open-source**, and **cross-platform** network **packet analyzer**. It allows you to **capture**, **inspect**, and **analyze network traffic** in real time or through previously saved **packet capture (PCAP) files**. Recognized as one of the best tools for **packet analysis**, Wireshark is widely used by **network administrators**, **cybersecurity professionals**, and **enthusiasts** to **understand network behavior** and **troubleshoot issues**.

## Task 2 - Tool Overview
#### Use Cases
Wireshark is used to **detect network problems**, identify **security anomalies**, and **investigate protocol details**. It allows **analysts** to examine **packets in depth** but does not **modify them** or act as an **IDS**.

#### GUI and Data
The **Wireshark interface** provides an **all-in-one workspace** with sections for **toolbar**, **display filter**, **recent files**, **capture interfaces**, and **status information**, making **packet analysis** efficient.

#### Loading PCAP Files
Wireshark allows you to **open** and **analyze packet capture (PCAP) files** using **menus**, **drag-and-drop**, or **double-click**, showing **detailed packet information** for investigation.

#### Packet Panes
- **Packet List Pane** – **summary** of each packet.  
- **Packet Details Pane** – **detailed protocol breakdown**.  
- **Packet Bytes Pane** – **raw hex** and **ASCII representation**.  

#### Colouring Packets
Packets can be **color-coded** based on **protocol** or **custom rules**, helping **analysts** quickly spot **anomalies** or **events of interest**. **Colouring rules** can be **temporary** or **permanent**.

#### Traffic Sniffing
Wireshark can **capture live network traffic** using the **capture interface**, with buttons to **start**, **stop**, and **restart sniffing**.

#### Merge PCAP Files
Wireshark allows **combining multiple PCAP files** into one for **consolidated analysis**, which can then be **saved as a new file**.

#### View File Details
You can view **capture file properties**, including **hash**, **capture time**, **comments**, **interface**, and **statistics**, which helps **classify** and **manage multiple PCAP files**.

## Task 3 - Packet Dissection
**Packet dissection**, also called **protocol dissection**, is the process of **decoding packet details** by analyzing **protocols** and their **fields**. Wireshark supports a wide range of **protocols** and allows **custom dissection scripts**. This process uses **OSI layers** to break down packets for **detailed analysis**.

### Layers of a Packet
#### The Frame (Layer 1)
Shows the **physical frame** or **packet details** from the **Physical layer**.

#### Source [MAC] (Layer 2)
Displays **source** and **destination MAC addresses** from the **Data Link layer**.

#### Source [IP] (Layer 3)
Shows **source** and **destination IPv4 addresses** from the **Network layer**.

#### Protocol (Layer 4)
Details the **Transport layer protocol (TCP/UDP)** including **source** and **destination ports**.

#### Protocol Errors
Highlights **TCP segment issues** that need **reassembly**; an extension of **Layer 4**.

#### Application Protocol (Layer 5)
Displays information specific to the **application protocol** used (e.g., **HTTP**, **FTP**, **SMB**).

#### Application Data
Shows **application-specific data**, extending the details of **Layer 5**.

## Task 4 - Packet Navigation

### Packet Numbers
Wireshark assigns a **unique number** to each captured packet, making it easier to **track events** and **navigate large captures**.

### Go to Packet
This feature allows **analysts** to **jump to specific packets** in the capture using the **“Go” menu** or **toolbar**. It helps **follow conversations** or **locate key events**.

### Find Packets
Wireshark can **search for packets by content**, using **Display Filter**, **Hex**, **String**, or **Regex inputs**. Searches can be performed in the **Packet List**, **Packet Details**, or **Packet Bytes panes**.

### Mark Packets
**Analysts** can **mark packets** for further investigation or **export**. **Marked packets** are **highlighted** and help identify **events of interest**, but markings are **temporary per session**.

### Packet Comments
Wireshark allows **adding comments** to specific packets. **Comments** are saved with the **capture file** and can help **analysts** note **suspicious** or **important events**.

### Export Packets
Specific **packets** can be **exported** from a **capture file** to **reduce noise** and **focus analysis** on **suspicious activity**.

### Export Objects (Files)
Wireshark can **extract files transferred over the network** from certain **protocols** (e.g., **HTTP**, **SMB**, **TFTP**) for further investigation.

### Time Display Format
The default **time display** is **seconds since capture start**. **Analysts** can change it (e.g., to **UTC format**) for easier **interpretation of events**.

## Task 5 - Packet Filtering
Wireshark provides a **powerful filtering engine** to help **analysts** focus on **specific traffic** or **events**. There are **two types of filters**:  
- **Capture Filters** – filter packets while **capturing**.  
- **Display Filters** – filter packets after capture for **viewing** and **analysis**.

### Apply as Filter
A basic filtering method where you **click on a field** and **apply a filter** to view only packets matching that **value**. The **query** is automatically **generated and applied**.

### Conversation Filter
Filters all packets **linked by IP addresses and port numbers** to view a **full conversation**, hiding **unrelated packets**.

### Colourise Conversation
Highlights **linked packets** without hiding others, using **coloring rules** to visually **track related packets**.

### Apply as Column
Adds a **specific field** as a **new column** in the **packet list pane**, helping to **track values across packets**.

### Follow Stream
Reconstructs **application-level streams (TCP/UDP/HTTP)** to view the **full conversation**, including **unencrypted data** like **usernames** and **passwords**. Automatically applies a **filter** for the stream being followed.

## Task 6 - Conclusions
**Wireshark** is a **powerful** and **versatile network analysis tool** that allows **analysts** to **capture**, **inspect**, **filter**, and **dissect network traffic**. By exploring its **GUI**, **packet panes**, **filtering options**, and **advanced features** like **stream following** and **expert info**, I gained a clear understanding of how to **investigate network behavior** and **troubleshoot issues effectively**.

### What I Learned
- How to **capture** and **load PCAP files** for analysis.  
- The **structure of a packet** and **OSI layer dissection**.  
- How **packet numbers**, **marking**, and **comments** help **track events**.  
- Techniques for **filtering traffic**, including **display** and **conversation filters**.  
- How to **follow streams** to **reconstruct application-level communication**.  
- Using **coloring rules**, **exporting packets**, and **objects** to **organize** and **share relevant data**.  
- The importance of **time display formats** and **expert info** for **spotting anomalies**.
