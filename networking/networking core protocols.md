# Networking Core Protocols

## Task 1 - Introduction
Networking core protocols are the fundamental rules that allow devices to communicate with each other across local and global networks. These protocols define how data is addressed, transmitted, routed, and received to ensure reliable and efficient communication. From automatically assigning IP addresses to resolving hardware identities and troubleshooting connectivity issues, core networking protocols work together to keep modern networks stable, scalable, and functional in both home and enterprise environments.

## Task 2 - Domain Name System (DNS)

### Domain Name System
The Domain Name System (DNS) allows users to access websites using easy-to-remember domain names instead of numerical IP addresses. It acts as a directory that maps domain names to their corresponding IP addresses, making Internet navigation simple and efficient.

### DNS Record Types
DNS uses different record types to define how domain names are resolved and how services are handled:
- **A Record** maps a domain name to an IPv4 address.
- **AAAA Record** maps a domain name to an IPv6 address.
- **CNAME Record** maps one domain name to another domain name.
- **MX Record** specifies the mail server responsible for handling emails for a domain.

## Task - 3 WHOIS
### Domain Ownership
When someone registers a domain name, they gain full authority to manage its DNS records, such as A, AAAA, and MX records. This means the domain owner decides how the domain behaves and where it points on the Internet.

### WHOIS Records
WHOIS is a public database that stores information about domain registrations. It contains details such as the registrant’s name, phone number, email address, physical address, registration date, and last update date.

## Task 4 - HTTP(S)
### HTTP and HTTPS 
Web browsers primarily use the HTTP and HTTPS protocols to communicate with web servers. HTTP stands for Hypertext Transfer Protocol, while HTTPS is the secure version that encrypts data. Both protocols rely on TCP to ensure reliable communication between the client and the server.
#### Common HTTP Methods
- **GET** – Retrieves data from the server, such as web pages or images.
- **POST** – Sends data to the server, commonly used for form submissions and file uploads.
- **PUT** – Creates or updates a resource on the server, overwriting existing data if necessary.
- **DELETE** – Removes a specified resource from the server

### Traffic Analysis with Wireshark
Using tools like Wireshark, we can inspect HTTP traffic in detail. It allows us to see the exact requests sent by the browser and the responses returned by the server, revealing hidden headers and metadata not visible in the browser.

## Task 5 - FTP: Transferring Files

### File Transfer Protocol (FTP) 
FTP (File Transfer Protocol) is specifically designed for transferring files between a client and a server. Because of this specialization, FTP can be more efficient and faster than HTTP when transferring files under similar network conditions.FTP uses TCP port 21 for control commands and Port 20 for data transfer in active mode.

#### Common FTP Commands
FTP defines specific commands for interacting with the server:
- **USER** – Sends the username to the server.
- **PASS** – Sends the password for authentication.
- **RETR** – Downloads a file from the server to the client.
- **STOR** – Uploads a file from the client to the server.
- **LIST** – Requests a directory listing (triggered by `ls` on the client).


### FTP Transfer Modes
- **ASCII** mode is used for text files.
- **Binary** mode is used for non-text files (images, executables).
- **Choosing** the wrong mode can cause file corruption or warnings during transfer.


### FTP Traffic Analysis with Wireshark
- Client commands appear separately from server responses.
- Commands typed by the user (e.g., `ls`) are translated into FTP protocol commands (e.g., `LIST`).
- Directory listings and file transfers occur over separate data connections, not the main control channel.

## Task 6 - SMTP: Sending Email

### Simple Mail Transfer Protocol (SMTP)
Just like web browsing and file transfers require specific protocols, email communication relies on its own protocol called SMTP (Simple Mail Transfer Protocol). SMTP defines how a mail client communicates with a mail server and how mail servers communicate with each other to deliver emails.SMTP servers listen on TCP port 25 by default.

### Sending Email Using Telnet
Using telnet, it is possible to manually send an email by directly typing SMTP commands:
- The client connects to the SMTP server on port 25.
- Commands are entered one by one to define sender, recipient, and message content.
- Once the email content is complete, a single dot (.) ends the message.
- The session is closed using the QUIT command.

## Task 7 - POP3: Receiving Email

### Post Office Protocol Version 3 (POP3) 
#### Common POP3 Commands
During a POP3 session, the client uses several commands:
- **USER** `<username>` – Identifies the user.
- **PASS** `<password>` – Authenticates the user.
- **STAT** – Displays the number of messages and their total size.
- **LIST** – Lists all available messages and their sizes.
- **RETR** `<message_number>` – Retrieves a specific email.
- **DELE** `<message_number>` – Marks a message for deletion.
- **QUIT** – Ends the session and applies changes such as deletions.

### POP3 Session Using Telnet
Using telnet, a client can manually connect to a POP3 server:
- The client connects to the server on port 110.
- Authentication is performed using USER and PASS.
- Commands like STAT, LIST, and RETR allow the client to view and download emails.
- The session ends with QUIT, applying any requested deletions.

## Task 8 - IMAP: Synchronizing Email
### Internet Message Access Protocol (IMAP)
IMAP (Internet Message Access Protocol) is designed for users who access their email from multiple devices, such as a desktop, laptop, and smartphone. Unlike POP3, which downloads and removes emails from the server, IMAP keeps emails on the server and synchronizes them across all connected clients. IMAP listens on TCP port 143 by default.
#### Common IMAP Commands
IMAP commands are more advanced than POP3 commands:
- **LOGIN** `<username> <password>` – Authenticates the user
- **SELECT** `<mailbox>` – Selects a mailbox folder (e.g., inbox)
- **FETCH** `<mail_number> <data_item>` – Retrieves a message or part of it
- **MOVE** `<sequence_set> <mailbox>` – Moves messages to another folder
- **COPY** `<sequence_set> <mailbox>` – Copies messages to another folder
- **LOGOUT** – Ends the IMAP session

## Task 9 - Conclusion

In this lesson, we explored the core networking protocols that make modern communication possible. We saw how HTTP/HTTPS allows web browsing, FTP enables efficient file transfers, and SMTP handles sending emails. For retrieving emails, POP3 provides simple download functionality for a single device, while IMAP allows mailbox synchronization across multiple devices. We also discussed how DNS maps domain names to IP addresses and how WHOIS provides registration information for domains. Together, these protocols form the foundation for how devices communicate reliably over networks and the Internet.
#### What I Learned
- How HTTP/HTTPS defines communication between web browsers and web servers using commands like GET, POST, PUT, and DELETE.
- How FTP is used for uploading and downloading files efficiently, and the purpose of commands like USER, PASS, RETR, and STOR.
- How SMTP handles sending emails and the role of commands like HELO, MAIL FROM, RCPT TO, and DATA.
- How POP3 allows downloading emails to a single device, while IMAP enables synchronization across multiple devices.
- How DNS maps domain names to IP addresses and how WHOIS provides public domain registration information.


