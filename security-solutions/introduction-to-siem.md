# Security Information and Event Management (SIEM)

## Task 1 - Introduction to SIEM
In a modern Security Operations Center (SOC), the **SIEM** (Security Information and Event Management) system acts as the centralized "brain." It is the core solution used by analysts to collect, normalize, and correlate logs from every device in the network to identify and respond to threats.

---

## Task 2 - The Challenge of Isolated Logs
In a standard network, devices continuously generate a "trail" of activity. Without a centralized system, these logs remain scattered and "silent."

### Log Source Categories:
1.  **Host-Centric Logs:** Captured within the endpoint itself (Windows, Linux, Servers). Examples include **Process Execution**, **Registry changes**, and **Authentication attempts**.
2.  **Network-Centric Logs:** Generated during communication between hosts or the internet (Firewalls, Routers, IDS/IPS). Examples include **SSH connections**, **VPN access**, and **Web traffic**.

### The Problem:
Without SIEM, security teams face massive hurdles:
* **No Centralization:** Analysts must manually connect to each machine via SSH or RDP.
* **Limited Context:** A single log might look harmless, but it doesn't show the "big picture" of an attack (e.g., **Lateral Movement**).
* **Format Issues:** Windows logs look different from Linux or Firewall logs, making manual comparison nearly impossible.

---

## Task 3 - The Power of SIEM Features
A SIEM solution transforms raw, scattered data into **Actionable Intelligence**.

### Core Features:
* **Centralized Collection:** Pulls logs from all sources into one location using **Agents** or **APIs**.
* **Normalization & Parsing:** Standardizes different log formats into a consistent structure, so a "Login" event looks the same regardless of the source.
* **Correlation:** Connects dots between different events. For example, it can link a **VPN login** from a new IP to a **PowerShell script execution**, signaling a compromised account.
* **Real-time Alerting:** Triggers notifications the moment a specific **Detection Rule** is matched.
* **Dashboards:** Provides visual summaries of network health, top failed logins, and triggered rules.



---

### Task 4: Log Sources and Ingestion
#### Primary Log Sources
Every interaction within a network generates a data point. To maintain total visibility, a SIEM must ingest logs from a variety of operating systems and services.

* **Windows Ecosystem:** Windows utilizes the **Event Viewer** to record activities. Each event is categorized by a unique **Event ID**, which the SIEM uses to track specific behaviors across thousands of endpoints.
* **Linux Ecosystem:** Linux systems store critical logs in plaintext files within the **`/var/log`** directory. Key files include:
    * **`/var/log/auth.log`**: Captures all authentication and authorization events.
    * **`/var/log/cron`**: Records the execution of scheduled background tasks.
    * **`/var/log/kern`**: Stores kernel-level messages and errors.
* **Web Services:** Apache and Nginx servers record every HTTP request. These are usually found in **`/var/log/apache2`** or **`/var/log/httpd`**, providing data on source IPs, status codes, and requested URLs.



#### Technical Ingestion Methods
Bringing this data into the SIEM requires specific transport mechanisms:

1.  **Agents and Forwarders:** A lightweight software package (e.g., **Splunk Universal Forwarder**) is installed on the host. It "watches" the log files and pushes new data to the SIEM in real-time.
2.  **Syslog Protocol:** A standard networking protocol used by routers, switches, and firewalls to stream logs to a centralized collector.
3.  **Manual Ingestion:** Analysts can manually upload files (such as `.csv`, `.json`, or `.log`) for "one-off" forensic investigations or historical analysis.
4.  **API Integration:** Used for cloud services (like AWS or Azure) where logs are pulled directly from the provider's management interface.

---

## Task 5 - Alerting Process and Analysis
SIEMs use **Logic-based Detection Rules** to catch adversaries.

### How Rules Work:
* **Case 1 (Log Clearing):** If an attacker tries to hide their tracks, Windows generates **Event ID 104**. A SIEM rule can be set to alert immediately when this ID appears.
* **Case 2 (Command Execution):** If a user runs the `whoami` command (often used after an exploit), the SIEM looks for **Event ID 4688** combined with the process name "whoami."

### The Analyst's Workflow:
Once an alert triggers, the analyst must determine if it is a **True Positive** (Real Threat) or a **False Positive** (Mistake). Actions include:
* **Tuning:** Adjusting the rule to stop future false alarms.
* **Isolation:** Disconnecting a confirmed infected host from the network.
* **Blocking:** Blacklisting suspicious IPs at the firewall level.

---

## Task 6 - Strategic Conclusion - The SIEM Ecosystem
The implementation of a **SIEM solution** represents the transition from a reactive security posture to a proactive, intelligence-driven operation. By solving the fundamental problems of **data fragmentation** and **lack of context**, the SIEM serves as the primary force multiplier for a security team. 

A high-functioning SIEM does not simply store data; it provides the **visibility** required to detect the most subtle indicators of compromise. When **skilled analysts** leverage **refined detection logic** and **centralized log correlation**, the organization gains the ability to neutralize threats with surgical precision before they can escalate into catastrophic breaches.
