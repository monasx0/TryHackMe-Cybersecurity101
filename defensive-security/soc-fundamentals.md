# SOC Fundamentals
## Task 1 - Introduction to SOC
Modern organizations store "secrets" (confidential data) digitally. Because hackers constantly look for new **vulnerabilities**, traditional security is not enough. 

A **SOC (Security Operations Center)** is a dedicated facility with a specialized team that monitors an organization's network **24/7** to prevent damage.

---

## Task 2 - Purpose and Components
The core mission of a SOC is **Detection and Response**.

### 1. Detection
* **Vulnerabilities:** Finding weaknesses in software (like unpatched Windows computers).
* **Unauthorized Activity:** Detecting if an attacker stole an employee's password.
* **Policy Violations:** Spotting internal rules being broken (e.g., downloading pirated files).
* **Intrusions:** Identifying successful unauthorized access to the network.

### 2. Response
When an incident is found, the SOC minimizes the impact and performs a **Root Cause Analysis** to find out how it happened.

### The 3 Pillars of SOC
A mature SOC environment relies on three pillars: **People, Process, and Technology**.



---

## Task 3 - People
Human intervention is required to filter out "noise" (false alarms). The team follows a specific hierarchy:

* **SOC Analyst (Level 1):** The **first responders**. They do basic **alert triage** to see if a threat is real.
* **SOC Analyst (Level 2):** They perform deeper investigations and look at data from multiple sources.
* **SOC Analyst (Level 3):** Experienced pros who **proactively hunt** for threats and handle critical incidents.
* **Security Engineer:** They **deploy and configure** the security tools.
* **Detection Engineer:** They write the **custom rules** used to spot harmful activity.
* **SOC Manager:** They manage the team and report to the **CISO** (Chief Information Security Officer).

---

## Task 4 - Process
Processes ensure the team works efficiently.

### Alert Triage (The 5 Ws)
To analyze an alert, analysts must answer:
1.  **What?** (What happened? e.g., Malware detected).
2.  **When?** (The exact time and date).
3.  **Where?** (Which machine or directory?).
4.  **Who?** (Which user was involved?).
5.  **Why?** (The cause, e.g., user downloaded a bad file).

### Reporting & Forensics
Harmful alerts are escalated as **tickets**. If the event is critical, the team performs **Digital Forensics** to analyze "artifacts" (leftover clues) from the system.

---

## Task 5 - Technology
Technology automates detection so the team doesn't have to check every device manually.

* **SIEM (Security Information and Event Management):** Collects logs from everywhere. It uses **logic rules** to find suspicious matches.
* **EDR (Endpoint Detection and Response):** Provides real-time visibility into **laptops and servers**. It can block threats with one click.
* **Firewall:** A barrier between the **internal network** and the Internet. It filters unauthorized traffic.



---

## Task 6 - Conclusion


## The Strategic Balance
A **mature SOC** does not succeed through tools alone; it thrives on the seamless integration of **People, Process, and Technology**. This triad creates a resilient defense-in-depth posture capable of withstanding the complexities of the modern threat landscape.

### 1. Empowered People
The human element remains the most critical asset. Skilled **SOC Analysts** provide the intuition and analytical depth that automated systems lack. By maintaining a clear hierarchy—from the **Level 1 Triage** to the **Level 3 Threat Hunter**—the organization ensures that every alert is handled with the appropriate level of expertise.
### 2. Standardized Processes
Consistency is maintained through **strict processes** and **Standard Operating Procedures (SOPs)**. By utilizing the **5 Ws (Who, What, When, Where, Why)** and structured **Incident Response** frameworks, the SOC ensures that no detail is overlooked and that every response is measurable, repeatable, and effective.
### 3. Integrated Technology
**Advanced Technology** acts as the force multiplier for the team. Tools like **SIEM** provide the wide-angle "radar" view of the network, while **EDR** offers the microscopic "scalpel" needed to isolate threats on individual devices. When these technologies are properly tuned by **Security Engineers**, they filter out the noise and allow the team to focus on high-fidelity alerts.

