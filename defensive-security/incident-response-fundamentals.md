# Incident Response Fundamentals

## Task 1 - Overview of Incident Response
In the physical world, we use CCTVs and security guards to protect our homes. In the **Digital Realm**, organizations face "Cyber Security Incidents" daily. **Incident Response (IR)** is the structured methodology used to handle a security breach from beginning to end, focusing on fighting the attack, minimizing damage, and restoring normal operations.



---

## Task 2 - Understanding Incidents and Events
Every process on a computer generates **Events**. Because there are millions of events, security solutions filter them into **Logs**. When a suspicious pattern is found, the system triggers an **Alert**.

### Alert Classification:
* **False Positive:** An alert that triggers on non-harmful activity (e.g., a large data backup mistaken for data theft).
* **True Positive:** An alert that correctly identifies a real threat (e.g., a phishing attempt). This is classified as an **Incident**.

### Severity Levels:
Incidents are prioritized by **Severity** (Low, Medium, High, Critical) based on their potential impact. **Critical** incidents are always handled first.

---

## Task 3 - Common Types of Incidents
Security incidents are categorized based on the nature of the attack:

* **Malware Infections:** Malicious programs (viruses, ransomware) designed to damage or exploit systems.
* **Security Breaches:** Unauthorized access to confidential data.
* **Data Leaks:** The exposure of sensitive information, often due to human error or misconfiguration.
* **Insider Attacks:** Attacks initiated by someone within the organization (e.g., a disgruntled employee).
* **Denial of Service (DoS):** Flooding a system with fake traffic to make it unavailable to legitimate users.



---

## Task 4 - Incident Response Frameworks
To handle incidents effectively, organizations follow structured frameworks. The two most prominent are **SANS** and **NIST**.

### SANS Framework (PICERL):
1.  **Preparation:** Building teams, plans, and tools before an attack happens.
2.  **Identification:** Detecting abnormal behavior and confirming the incident.
3.  **Containment:** Isolating systems to prevent the attack from spreading.
4.  **Eradication:** Removing the root cause of the threat (e.g., deleting malware).
5.  **Recovery:** Restoring systems from backups and returning to normal operations.
6.  **Lessons Learned:** Documenting the incident to improve future defenses.



### NIST Framework:
The **NIST** framework is similar but condenses the process into 4 phases: 
1. Preparation 
2. Detection & Analysis 
3. Containment, Eradication, & Recovery 
4. Post-Incident Activity.

The formal document governing these actions is the **Incident Response Plan**, which outlines roles, communication paths, and methodologies.

---

## Task 5 - Incident Response Techniques & Tools
Automated technology is essential for modern incident detection and response:

* **SIEM:** Centralizes and correlates logs to find incidents across the whole network.
* **EDR:** Protects individual devices (endpoints) and can automatically isolate them if a threat is found.
* **AV (Antivirus):** Scans for known malicious signatures.



### Playbooks and Runbooks:
* **Playbooks:** High-level guidelines providing step-by-step instructions for specific incident types (e.g., a Phishing Playbook).
* **Runbooks:** Highly detailed, technical execution steps tailored to specific organizational tools.

---

## Task 6 - Conclusion
Incident Response is a critical defensive discipline. By combining **skilled people**, **structured frameworks (SANS/NIST)**, and **advanced tools**, organizations can transform from being vulnerable targets into resilient entities capable of weathering any cyber storm.
