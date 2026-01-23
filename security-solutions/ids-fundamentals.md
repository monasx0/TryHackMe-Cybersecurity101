# Intrusion Detection Systems (IDS) Fundamentals

## Task 1 - Introduction to IDS
While firewalls act as gatekeepers at the network boundary, an **Intrusion Detection System (IDS)** serves as the internal surveillance system. If an attacker bypasses the perimeter using a legitimate-looking connection, the IDS is responsible for identifying subsequent malicious behavior. 

Unlike a firewall, which proactively blocks traffic, an IDS is primarily a **monitoring solution**. It observes network traffic for known attack patterns or deviations from normal behavior and notifies security administrators via alerts, allowing for a swift manual response.



---

## Task 2 - Deployment and Detection Modes
The effectiveness of an IDS depends on how it is deployed and how it identifies threats.

### Deployment Modes
* **Host IDS (HIDS):** Installed on individual devices to monitor internal system calls, log files, and software activity.
* **Network IDS (NIDS):** Deployed at strategic points in the network to monitor traffic for all connected hosts, providing a centralized security view.



### Detection Modes
* **Signature-Based:** Matches traffic against a database of known attack patterns (signatures). While highly efficient for known threats, it cannot detect "Zero-Day" attacks.
* **Anomaly-Based:** Establishes a "baseline" of normal network behavior and triggers alerts when activity deviates from that norm. This is effective for new threats but can result in **False Positives**.
* **Hybrid IDS:** Integrates both signature and anomaly-based methods to provide comprehensive coverage.

---

## Task 3 - Snort - The Open Source Standard
**Snort** is a premier open-source IDS that utilizes both signature and anomaly-based detection. It operates in three distinct modes:
1.  **Packet Sniffer:** Displays real-time network traffic on the console for basic monitoring.
2.  **Packet Logger:** Records traffic into **PCAP** files for later forensic analysis.
3.  **NIDS Mode:** The primary defensive mode that applies rules to live traffic and generates alerts upon threat detection.

---

## Task 4 - Snort Configuration and Rule Analysis
Snort’s intelligence is driven by its configuration file (`snort.conf`) and its rule sets. Rules follow a strict syntax to ensure precise detection.

### Anatomy of a Snort Rule
A typical rule consists of a **Rule Header** (Action, Protocol, IPs, Ports) and **Rule Options** (Metadata).

**Sample Rule Syntax:**
```bash
alert icmp any any -> $HOME_NET any (msg:"Ping Detected"; sid:10001; rev:1;)
```
### Laboratory Execution
To detect a loopback ping, we can append a custom rule to `/etc/snort/rules/local.rules`:
```bash
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)
```
**Running Snort in NIDS Mode:**
```bash
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf
```
**Analyzing Historical PCAP Files:**
```bash
sudo snort -q -l /var/log/snort -r Task.pcap -A console -c /etc/snort/snort.conf
```
---

## Task 5 - Conclusion
The implementation of an Intrusion Detection System is essential for achieving deep visibility and identifying post-perimeter threats within a robust security architecture. By leveraging the granular rule-based logic of tools like Snort, organizations can effectively transition from basic traffic filtering to sophisticated, real-time threat monitoring. Ultimately, the synergy between signature-based precision and anomaly-based flexibility ensures a proactive defense against both established and emerging cyber-attacks.
