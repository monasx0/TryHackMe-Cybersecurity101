# Firewall Fundamentals

## Task 1 - Purpose of a Firewall
In the physical world, security guards stand at the entrances of banks and buildings to verify every person entering or leaving. In the digital realm, a **Firewall** performs the exact same function. It acts as a barrier between a trusted internal network and an untrusted external network (like the Internet).

A firewall inspects every data packet that attempts to cross its boundary. Based on a set of **pre-defined rules**, the firewall either **allows** legitimate traffic to pass or **blocks** unauthorized visitors from gaining access to the system.



---

## Task 2 - Types of Firewalls
Firewalls have evolved significantly, moving across different layers of the **OSI Model** to provide more granular protection.

### 1. Stateless Firewall (Layers 3 & 4)
This is the most basic type. It filters packets based on individual rules (Source IP, Port) but **does not remember** previous connections. Because it treats every packet as a new event, it is very fast but lacks the context needed for complex security policies.

### 2. Stateful Firewall (Layers 3 & 4)
Unlike stateless systems, a stateful firewall maintains a **State Table**. It keeps track of established connections. If a connection was previously approved, future packets for that same session are automatically allowed, providing better security with less manual rule-matching.

### 3. Proxy Firewall (Layer 7)
Also known as an **Application-Level Gateway**, it acts as an intermediary. It prevents direct contact between the network and the internet by masking internal IP addresses. Most importantly, it can **inspect the content** of the data (e.g., blocking specific URLs or file types).

### 4. Next-Generation Firewall (NGFW) (Layers 3–7)
The most advanced protection available. NGFWs combine traditional firewalling with **Intrusion Prevention Systems (IPS)**, **SSL/TLS Decryption**, and **Heuristic Analysis** to identify and block patterns of attack in real-time.



---

## Task 3 - Firewall Rule Logic
Firewalls are instructed through **Access Control Lists (ACLs)**. Every rule consists of specific components that define how traffic is handled.

### Anatomy of a Rule:
* **Source/Destination:** The IP addresses involved in the communication.
* **Port & Protocol:** The specific service (e.g., **TCP 80** for HTTP or **TCP 22** for SSH).
* **Action:** What the firewall does with the packet (**Allow**, **Deny**, or **Forward**).
* **Direction:** Whether the rule applies to **Inbound** (incoming) or **Outbound** (outgoing) traffic.

### Directionality Examples:
* **Inbound:** Allowing external customers to reach your web server.
* **Outbound:** Preventing internal employees from accessing malicious websites.
* **Forward:** Redirecting traffic from the gateway to a specific internal server.

---

## Task 4 - Linux Firewalls and UFW
Linux security is built upon the **Netfilter** framework. While there are advanced tools like **iptables** and **nftables**, many users prefer **UFW (Uncomplicated Firewall)** for its simple syntax.

### Basic UFW Management
To interact with the firewall, use the following commands:

**Check Firewall Status:**
```bash
sudo ufw status
```
**Enable the Firewall:**
```bash
sudo ufw enable
```
**Set Default Outbound Policy:**
```bash
sudo ufw default allow outgoing
```
**Block a Specific Service (e.g., SSH):**
```bash
sudo ufw deny 22/tcp
```
**List Rules with Numbers (for deletion):**
```bash
sudo ufw status numbered
```
**Delete a Specific Rule (e.g., Rule #2):**
```bash
sudo ufw delete 2
```
---

## Task 5 - Conclusion
A **Firewall** is the cornerstone of defensive security. Whether you are using a basic **Stateless** filter or a sophisticated **Next-Generation** system, the goal remains the same: ensuring that only authorized and safe traffic enters your network. By mastering **UFW** and understanding **Stateful inspection**, you can significantly reduce the attack surface of any system.
