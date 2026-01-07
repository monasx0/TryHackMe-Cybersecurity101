# Networking Secure Protocols

## Task 1 - Introduction
In the **Networking Core Protocols** section, we saw how data is transmitted over the network, but these protocols do not protect **confidentiality**, **integrity**, or **authenticity**. Sensitive information like **passwords**, **emails**, or **payments** can be intercepted or altered. To secure communication, **Transport Layer Security (TLS)** is added to existing protocols, creating **HTTPS**, **POP3S**, **SMTPS**, and **IMAPS**, while **SSH** provides a secure way to access remote systems, replacing insecure protocols like **TELNET**.

## Task 2 - TLS (Transport Layer Security)
### TLS (Transport Layer Security)
**TLS** is a **cryptographic protocol** that secures communication over networks by providing **confidentiality** and **integrity**. It operates at the **Transport Layer** of the **OSI model**. **TLS** is an evolution of **SSL (Secure Sockets Layer)**, with **TLS 1.3** being the latest version, introduced in 2018.

#### Main Takeaways
- **TLS** secures data at the **Transport Layer** of the **OSI model**.
- It **encrypts all data** exchanged between a **client** and a **server**, ensuring **confidentiality** and **integrity**.

### Certificates in TLS
Before secure communication begins, a **server** (or **client**) needs a signed **TLS certificate** to verify its **identity**. This certificate is issued by a **Certificate Authority (CA)** after the server submits a **Certificate Signing Request (CSR)**.

#### Main Takeaways
- **Trusted Certificates**: Certificates from trusted **CAs** are automatically recognized by web browsers.
- **Self-Signed Certificates**: Not recommended for verifying **authenticity**, as they are not validated by a **third party**.

## Task 3 - HTTP (Hyper Text Transfer Protocol)
### HTTP
As we studied in the **Networking Core Protocols** room, **HTTP** relies on **TCP** and uses **port 80** by default. All **HTTP traffic** is sent in **cleartext**, which means anyone intercepting the packets can read the exchanged data, such as **usernames**, **passwords**, or other sensitive information.

#### HTTP Over TLS (HTTPS)
**HTTPS** stands for **Hypertext Transfer Protocol Secure**. It is essentially **HTTP over TLS**, which **encrypts all traffic** to ensure **confidentiality** and **integrity**. After resolving the **domain name**, the steps to request a page over **HTTPS** are:
- Establish a **TCP three-way handshake** with the target **server**.
- Establish a **TLS session**.
- Communicate using the **HTTP protocol**, e.g., sending **HTTP requests** like `GET / HTTP/1.1`.

### Getting the Encryption Key
Accessing the **encryption key** allows decryption of the **HTTPS traffic**. Without the key, the content remains **secure**. When the key is provided to tools like **Wireshark**, the previously hidden **HTTP traffic** can be decrypted and inspected.

## Task 4 - SMTPS, POP3S, and IMAPS
### Email Over TLS
Adding **TLS** to email protocols like **SMTP**, **POP3**, and **IMAP** secures communication by **encrypting the data** as it travels across the network. These secure versions are called:
- **SMTPS** – Secure Mail Transfer Protocol over **TLS**
- **POP3S** – Secure Post Office Protocol over **TLS**
- **IMAPS** – Secure Internet Message Access Protocol over **TLS**

## Task 5 - SSH (Secure Shell)
**SSH** is a protocol used to securely log in to remote systems. It provides **encrypted communication**, protecting the **confidentiality** and **integrity** of the connection. **SSH** replaced older, insecure methods like **Telnet**, where all data—including **passwords**—was sent in **cleartext**.

#### Key Advantages of SSH:
- **Secure authentication**: Supports **password**, **public key**, and **two-factor authentication**.
- **Confidentiality**: **End-to-end encryption** protects against **eavesdropping** and alerts you to new **server keys** to prevent **man-in-the-middle attacks**.
- **Integrity**: **Cryptography** ensures data is not tampered with during **transmission**.
- **Tunneling**: **SSH** can create a **secure tunnel** for other protocols, similar to a **VPN**.
- **X11 Forwarding**: Allows **graphical applications** from remote **Unix-like systems** to display locally over the network.

## Task 6 - SFTP and FTPS
### Secure File Transfer (SFTP and FTPS)
**SFTP (SSH File Transfer Protocol)** and **FTPS (File Transfer Protocol Secure)** both provide **secure methods** for transferring files, but they rely on **different underlying technologies**. **SFTP** is part of the **SSH protocol suite** and operates on **port 22**, while **FTPS** uses **TLS** for security, similar to **HTTPS**, and typically operates on **port 990**.

**Example (SFTP command)**:  
```bash
sftp user@hostname
```

This establishes a **secure file transfer session**, ensuring that all **file uploads** and **downloads** are **encrypted** and **protected from eavesdropping**.

## Task 7 - VPN (Virtual Private Network)
A **VPN (Virtual Private Network)** creates a **secure tunnel** between a **client** and a **VPN server**, allowing users to access **remote networks** as if they were **directly connected**. VPNs are commonly used by companies to enable **employees** to securely access **internal resources** from remote locations.

#### Main Takeaways:
- **Encryption**: All traffic between the **client** and **server** is **encrypted**.
- **Anonymity**: VPN users appear to be coming from the **VPN server’s IP address** rather than their actual location.

## Task 8 - Conclusions
In this lesson, we explored **secure networking protocols** that protect **confidentiality**, **integrity**, and **authenticity** of **data**. Protocols like **HTTPS**, **SMTPS**, **POP3S**, and **IMAPS** secure **web browsing** and **email communication** using **TLS**, while **SSH**, **SFTP**, and **FTPS** provide **secure remote access** and **file transfers**. **VPNs** create **encrypted tunnels** to protect all traffic and ensure **privacy** when accessing **remote networks**. Together, these protocols allow **safe** and **trusted communication** over the **Internet**.

### What I Learned
- **TLS** encrypts data to secure protocols like **HTTP**, **SMTP**, **POP3**, and **IMAP**.
- **SSH** replaces insecure remote access protocols like **Telnet** and provides **authentication**, **encryption**, and **tunneling**.
- **SFTP** and **FTPS** allow **secure file transfers** using **SSH** and **TLS**, respectively.
- **VPNs** encrypt all traffic between a **client** and **server**, ensuring **privacy**, **anonymity**, and access to **remote networks**.
- Implementing **secure protocols** prevents **eavesdropping**, **data tampering**, and **impersonation attacks**.
