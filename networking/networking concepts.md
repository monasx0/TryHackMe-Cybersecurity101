# Network Concepts

## Task 1 - Introduction
This lesson marks the beginning of a four-part journey designed to introduce viewers to essential networking concepts and the most widely used networking **protocols**. Throughout this series, we will explore the fundamental building blocks of modern digital communication, uncover how devices connect and interact across networks, and provide practical insights into the protocols that keep our interconnected world running smoothly.

## Task 2 - OSI Model
The **OSI** (**Open Systems Interconnection**) model is a conceptual framework created by the **International Organization for Standardization** (**ISO**) to describe how network communications occur. It divides networking into seven layers, each with a specific role, making it easier to understand, design, and troubleshoot networks.

#### Layer 1: Physical Layer
Deals with the actual physical connection between devices, such as cables, WiFi signals, or antennas, and defines how binary data (0s and 1s) is transmitted.

#### Layer 2: Data Link Layer
Ensures reliable data transfer between devices on the same network segment. It uses **MAC addresses** to identify devices and manages protocols like **Ethernet** and **WiFi**.

#### Layer 3: Network Layer
Handles communication between different networks. It’s responsible for logical addressing and routing data through the best paths, using protocols such as **IP** and **ICMP**.

#### Layer 4: Transport Layer
Provides end-to-end communication between applications on different hosts. It manages data flow, segmentation, and error correction, with protocols like **TCP** and **UDP**.

#### Layer 5: Session Layer
Manages sessions between applications, ensuring data is sent in the correct order and can recover from failures.

#### Layer 6: Presentation Layer
Prepares data for the **application layer**, handling encoding, compression, and **encryption**.

#### Layer 7: Application Layer
Provides services directly to user applications. This is where protocols like **HTTP**, **FTP**, **DNS**, **SMTP**, and **IMAP** operate, allowing programs like web browsers and email clients to communicate over the network.

## Task 3 - TCP/IP Model
**TCP/IP** stands for **Transmission Control Protocol/Internet Protocol** and was created in the 1970s by the **U.S. Department of Defense**. One of its strengths is that the network can keep working even if parts of it go down, thanks to smart routing that adapts to changes.

The **TCP/IP model** has four layers, which we can look at from top to bottom:
#### Layer 1: Application Layer
Combines the **OSI model’s** **application**, **presentation**, and **session layers**. It provides services directly to programs, like web browsing, email, and file transfers.
#### Layer 2: Transport Layer
Ensures that data moves reliably between applications on different devices. Protocols like **TCP** and **UDP** work here.
#### Layer 3: Internet Layer
Handles sending data across networks, like **OSI’s network layer**. It uses addresses and routing to get packets to the right place, using protocols like **IP**.
#### Layer 4: Network Access Layer
Combines **OSI’s physical** and **data link layers**. It handles the actual transmission of data over **cables**, **WiFi**, or other media and uses **MAC addresses** to identify devices on the same network.

## Task 4 - IP Addresses and Subnets
### IP Address
An **IP address** is a unique numerical label assigned to every device on a network. It allows devices to identify and communicate with each other. Examples include IPv4 `192.168.1.1` and IPv6 `2001:0db8:85a3::8a2e:0370:7334`.
### Subnet
A **subnet** (**subnetwork**) is a smaller, organized segment of a larger network. Subnets improve network efficiency, security, and management. They are defined using a **subnet mask**, `255.255.255.0` or **CIDR notation**, `/24`.
### Private Address
A **private IP address** is reserved for use within internal networks and cannot be accessed directly from the Internet. **Private addresses** allow safe communication within a local network. Common ranges include:
- `10.0.0.0` – `10.255.255.255`
- `172.16.0.0` – `172.31.255.255`
- `192.168.0.0` – `192.168.255.255`

## Task 5 - UDP and TCP
### TCP (Transmission Control Protocol)
**TCP** is a connection-oriented protocol that ensures reliable communication between devices. It guarantees that data is delivered in order, without errors, and without duplication. **TCP** is used by applications like web browsing (**HTTP/HTTPS**), email (**SMTP, IMAP**), and file transfers (**FTP**).
#### How TCP communicates
- **SYN** – The sender requests a connection.
- **SYN-ACK** – The receiver acknowledges the request and agrees to connect.
- **ACK** – The sender confirms, and the connection is established.
### UDP (User Datagram Protocol)
**UDP** is a connectionless protocol that sends data without establishing a connection. It is faster but does not guarantee delivery, order, or error checking. **UDP** is commonly used for live streaming, online gaming, and DNS queries where speed is more important than reliability.
#### How UDP communicates
- Data is sent as datagrams without handshakes.
- There is no acknowledgment from the receiver, so packets may arrive out of order or get lost.

## Task 6 - Encapsulation
**Encapsulation** is the process in networking where data from a higher layer is wrapped with protocol-specific information (headers and sometimes trailers) by each lower layer before transmission. This ensures that each layer can perform its specific function, such as addressing, routing, or error checking, without worrying about the details of other layers.
#### Steps of Encapsulation
##### 1. Application Layer
The user’s data (like an email, message, or file) is created and formatted according to the application protocol.
##### 2. Transport Layer
A **header** is added containing information like source and destination ports, sequencing, and error-checking details, forming a segment (**TCP**) or datagram (**UDP**).
##### 3. Network Layer
An **IP header** is added for logical addressing and routing, creating a packet.
##### 4. Data Link Layer
A **header** and **trailer** are added for physical addressing and error detection, forming a frame, which is ready to be transmitted over the physical medium.

## Task 7 - Telnet
Telnet is a network protocol used to access and manage remote devices over a TCP/IP network. It allows a user to log in to a remote computer and execute commands as if they were physically present. Telnet works on port 23 and transmits data, including passwords, in plain text, which makes it insecure for sensitive communications.

## Task 8 - Conclusion
In this lesson, we explored the foundational concepts of computer networking, including the **OSI** and **TCP/IP** models, **IP addressing**, **subnets**, **encapsulation**, and basic protocols like **TCP**, **UDP**, and **Telnet**. Understanding these concepts helps us see how devices communicate reliably, securely, and efficiently across networks.

#### What I Learned
- The **OSI model** layers and their roles in organizing network communication.
- How the **TCP/IP** model works and how it differs from the **OSI** model.
- **IP addresses**, **subnets**, and **private addresses** and how they help devices communicate efficiently.
- The differences between **TCP** and **UDP**, including how reliable and fast data transmission is handled.
- The concept of **encapsulation** and how each **network layer** wraps data with **headers** and **trailers** for proper delivery.

