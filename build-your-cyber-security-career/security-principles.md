# Security Principles

## Task 1 - The Core of Security: The CIA Triad
The foundation of any security posture is built upon three pillars known as the CIA Triad. Security is not a binary state but a balance of these three functions:

* **Confidentiality:** Ensuring data is accessible only to authorized recipients.
* **Integrity:** Ensuring data remains accurate and unaltered; providing mechanisms to detect unauthorized changes.
* **Availability:** Ensuring systems and data are accessible when required by users.



### Beyond the Triad
Modern security requires additional layers to ensure trust:
* **Authenticity:** Verifying that data or a document originates from the claimed source.
* **Nonrepudiation:** Ensuring an entity cannot deny an action or the authorship of a document (critical for banking and legal systems).

---

## Task 2 - The Adversarial Flipside: The DAD Triad
Every security goal has a corresponding threat. The **DAD Triad** represents the opposite of CIA and defines the primary goals of an attacker:
1.  **Disclosure:** The unauthorized release of data (Opposite of Confidentiality).
2.  **Alteration:** The unauthorized modification of data (Opposite of Integrity).
3.  **Destruction/Denial:** Rendering a system or data unusable (Opposite of Availability).



---

## Task 3 - Foundational Security Models
Security models provide a mathematical or logical framework to enforce CIA properties.

| Model | Primary Goal | Core Logic |
| :--- | :--- | :--- |
| **Bell-LaPadula** | Confidentiality | **No Read Up / No Write Down.** Prevents sensitive info from leaking to lower levels. |
| **Biba** | Integrity | **No Read Down / No Write Up.** Prevents high-integrity systems from being corrupted by low-integrity data. |
| **Clark-Wilson** | Integrity | Uses **Transformation Procedures (TPs)** and **Integrity Verification (IVPs)** to ensure data remains consistent. |

---

## 4. Security Principles and Standards (ISO/IEC 19249)
The International Organization for Standardization provides specific principles for building secure products.

### Architectural Principles
* **Domain Separation:** Grouping related components (e.g., OS Kernel in Ring 0 vs. Apps in Ring 3).
* **Layering:** Implementing security at multiple abstract levels (Defense-in-Depth).
* **Encapsulation:** Hiding low-level implementations to prevent direct data manipulation (common in OOP).
* **Redundancy:** Ensuring availability through backup hardware or RAID configurations.
* **Virtualization:** Using sandboxing and hardware sharing to improve security boundaries.

### Design Principles
1.  **Least Privilege:** Providing the absolute minimum permissions needed for a task.
2.  **Attack Surface Minimization:** Disabling unnecessary services to reduce entry points.
3.  **Centralized Parameter Validation:** Validating all user inputs through a single, trusted library.
4.  **Centralized General Security Services:** Using a single server/system for authentication and security tasks.
5.  **Fail Safe/Error Handling:** Ensuring systems fail into a secure state (e.g., a firewall blocking traffic upon a crash).

---

## Task 5 - Trust Frameworks: Zero Trust vs. Trust but Verify
Trust is treated differently depending on the organization's risk tolerance:

* **Trust but Verify:** Assumes entities are trustworthy but requires logging and auditing to confirm behavior.
* **Zero Trust:** Treats "trust" as a vulnerability. It follows the mantra **"Never trust, always verify."** It removes location-based trust (internal vs. external) and relies on microsegmentation.

---

## Task 6 - Defining the Risk Landscape
Understanding the difference between these three terms is critical for risk management:
* **Vulnerability:** A weakness in the system (e.g., a glass door).
* **Threat:** A potential danger that could exploit a weakness (e.g., a burglar with a hammer).
* **Risk:** The likelihood of the threat occurring combined with the business impact (e.g., the cost of losing the inventory).

## Task 7 - Conclusion
Security is a continuous process of balancing protection and accessibility. By implementing frameworks like the **Parkerian Hexad** (which adds Utility and Possession to CIA) and utilizing the **Shared Responsibility Model** in cloud environments, organizations can build a resilient security posture.
