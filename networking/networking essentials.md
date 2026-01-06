# Networking Essentials
## Task 1 - Introduction
This lesson introduces the core concepts that make modern networks function seamlessly behind the scenes. It focuses on how devices automatically obtain network configurations, how data travels across multiple networks and countries, and how multiple devices can share a single public **IP address** to access the Internet.

Throughout this lesson, we will explore essential networking services and mechanisms that enable dynamic configuration, efficient packet delivery, and Internet connectivity in home and enterprise environments.

## Task 2 - **DHCP**
### Dynamic Network Configuration
Modern devices can automatically configure their network settings when they connect to a new network, allowing users to get online without manual setup.
### **DHCP** (Dynamic Host Configuration Protocol)
**DHCP** is a protocol that automatically assigns **IP addresses** and other network settings to devices, making network access quick and easy.
### **DHCP** Process (DORA)
**DHCP** assigns an **IP address** using four steps:
- **Discover** – The client looks for a **DHCP** server.
- **Offer** – The server offers an available **IP address**.
- **Request** – The client accepts the offered address.
- **Acknowledge** – The server confirms the assignment.

After the process is complete, the device receives an **IP address**, a gateway, and a **DNS server**, allowing it to access the network and the Internet.

## Task 3 - **ARP** (Address Resolution Protocol)

### **MAC Address**
A **MAC address** is a unique 48-bit hardware address assigned to a network interface. It is used for communication between devices on the same local network.

### **IP** and **MAC** Relationship
Devices communicate using **IP addresses**, but data is delivered on the local network using **MAC addresses**. To send data, a device must know both.

### **ARP** (Address Resolution Protocol)
**ARP** is a protocol that maps an **IP address** to its corresponding **MAC address** on a local network.

#### How **ARP** Works
- The sender broadcasts an **ARP Request** asking for the **MAC address** of an **IP**
- The target device replies with an **ARP Reply** containing its **MAC address**
- Communication can then begin using **Ethernet frames**

## Task 4 -  **ICMP** (Internet Control Message Protocol)

### **Internet Control Message Protocol (ICMP)**
**ICMP** is a network-layer protocol used for error reporting and network diagnostics. It helps devices understand whether data can reach a destination and what happens when it cannot.
### **Ping**
The **ping** command checks whether a target system is reachable on the network.
#### How **Ping** Works
- Sends an **ICMP Echo Request** (Type 8) to the target
- The target replies with an **ICMP Echo Reply** (Type 0) 
- Measures round-trip time (RTT) between sender and receiver

### **Traceroute**
The **traceroute** command shows the path packets take from your system to a target.

#### How **Traceroute** Works
- **Traceroute** sends a packet to the target with a limited hop count (**TTL**).
- The first router reduces **TTL** to 0, drops the packet, and sends back a message to tell you it’s there.
- **Traceroute** increases **TTL** by 1 and repeats, discovering the next router along the path.
- This continues until the packet reaches the target.
- If a router doesn’t respond, **traceroute** shows * for that hop.

## Task 5 - Routing
Routing is how networks decide the path packets take from a source to a destination. Even a small network needs a way to figure out which router to send packets through. On the Internet, with millions of routers and billions of devices, routing protocols help routers choose the best paths automatically.
### Common Routing Protocols
#### **OSPF** (Open Shortest Path First)
- Routers share information about the network’s topology.
- Each router calculates the most efficient path to every destination.
#### **EIGRP** (Enhanced Interior Gateway Routing Protocol)
- Cisco’s proprietary protocol combining different routing methods.
- Considers network reachability and costs (like bandwidth or delay) to pick paths.
#### **BGP** (Border Gateway Protocol)
- The main protocol for the Internet.
- Lets different networks (**ISPs**) exchange routing info.
- Ensures packets are sent efficiently across multiple networks.
#### **RIP** (Routing Information Protocol)
- Simple protocol for small networks.
- Chooses routes with the fewest hops to reach a destination.

## Task 6 - **NAT**
### Network Address Translation (NAT)
**NAT** is a technique used to allow many devices on a private network to share a single public **IP address** when accessing the Internet. This solves the problem of IPv4 address depletion.
#### How **NAT** Works
- Devices on a private network use private **IP addresses**.
- The **NAT**-enabled router translates these private addresses into a public **IP address** and assigns unique port numbers.
- When a device initiates a connection, the router keeps a translation table to map internal **IP addresses** and ports to the external **IP** and port.

## Task 7 - Conclusions
In this task, we explored how devices connect and communicate across networks. We learned how routing protocols help routers determine the best path for sending packets, how **DHCP** automatically assigns **IP addresses**, how **ARP** translates **IP addresses** to **MAC addresses**, and how **NAT** allows multiple devices to share a single public **IP**. We also saw how **ICMP** tools like **ping** and **traceroute** help troubleshoot networks and understand packet paths.
### What I Learned
- How **DHCP** assigns **IP addresses**, gateways, and **DNS servers** automatically.
- How **ARP** maps **IP addresses** to **MAC addresses** for devices on the same network.
- How routing protocols (**OSPF**, **EIGRP**, **BGP**, **RIP**) determine the best path for packets.
- How **ICMP** commands like **ping** and **traceroute** help test connectivity and discover routes.
- How **NAT** allows multiple devices to access the Internet using a single public **IP address**.
