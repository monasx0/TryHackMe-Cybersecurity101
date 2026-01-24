# OWASP Top 10 2025 (Application Design Flaws)
# OWASP Top 10 Analysis Report: Architecture and System Design Failures

## Task 1 - Introduction
This report focuses on four categories from the **OWASP Top 10 2025** that center on failures in architecture and system design. Unlike code-level bugs, these vulnerabilities often stem from how a system is structured, configured, or integrated with external components.

The following categories are analyzed in this report:
* **AS02: Security Misconfigurations**
* **AS03: Software Supply Chain Failures**
* **AS04: Cryptographic Failures**
* **AS06: Insecure Design**

---

## Task 2 - AS02: Security Misconfigurations
**Security Misconfigurations** occur when a system is deployed with unsafe settings. These are not typically "coding errors" but rather mistakes in setup, such as leaving a door unlocked rather than the lock being broken.

### Why It Matters
Modern apps use complex "stacks" (cloud storage, APIs, servers). If a single part of this stack uses a default password or exposes an admin panel, the entire system is at risk.

**Common Patterns:**
* **Default Credentials:** Leaving passwords as `admin` or `password123`.
* **Verbose Error Messages:** Showing "Stack Traces" (detailed technical errors) to users, which tells attackers exactly how the server is built.
* **Exposed Storage:** Leaving cloud buckets (like AWS S3) open to the public without a login requirement.

**Prevention:**
* Harden configurations by removing unused features.
* Hide technical details from error messages.
* Use automated tools to check for open "buckets" or exposed services.



---

## Task 3 - AS03: Software Supply Chain Failures
**Software Supply Chain Failures** happen when the "ingredients" used to build an app (libraries, third-party packages, or AI models) are compromised. You might write perfect code, but if a tool you downloaded contains a "backdoor," your app is vulnerable.

### The SolarWinds Example
In 2021, attackers didn't hack a company directly; they hacked the software update process. When thousands of organizations downloaded a "trusted" update, they were actually installing a virus.

**Common Patterns:**
* Automatically installing updates without checking them first.
* Using unverified AI models that might have hidden malicious behaviors.
* Using "outdated" libraries that have known, public vulnerabilities.

**Prevention:**
* Verify and "sign" all third-party components before use.
* Monitor dependencies for new vulnerabilities constantly.
* Treat third-party AI models as untrusted until audited.

---

## Task 4 - AS04: Cryptographic Failures
**Cryptographic Failures** occur when encryption is missing, weak, or implemented incorrectly. Cryptography is what keeps passwords and credit card numbers private; when it fails, that sensitive data is exposed in "plain text."

### Common Failures
* **Weak Algorithms:** Using old methods like **MD5** or **SHA-1**, which modern computers can "crack" in seconds.
* **Hard-coded Keys:** Putting the "secret key" directly inside the source code where any developer (or attacker) can see it.
* **Lack of Encryption in Transit:** Sending data over the internet without HTTPS/TLS, allowing "Man-in-the-Middle" attacks.



**Prevention:**
* Use modern, strong encryption like **AES-GCM**.
* Use a "Vault" service (like AWS KMS or HashiCorp Vault) to store keys instead of keeping them in code.
* Ensure all web traffic is forced over **TLS 1.3**.

---

## Task 5 - AS06: Insecure Design
**Insecure Design** is a "foundational" flaw. This means the actual logic of the app is dangerous, even if the code is written perfectly. You cannot "patch" a design flaw; you usually have to rebuild the feature.

### Insecure Design in the AI Era
With AI assistants, developers often trust model outputs blindly. **Prompt Injection** is a major design risk where a user can "trick" an AI into ignoring its rules or leaking private data by giving it specific instructions.

**Example Case (Clubhouse):**
The app's design assumed users would only use the mobile app. However, because the backend API had no authentication, anyone could bypass the app and query private conversation data directly from the server.

**How to Design Securely:**
* **Threat Modeling:** Think like an attacker during the drawing board phase.
* **Least Privilege:** Ensure users and AI agents only have access to what they absolutely need.
* **Human-in-the-loop:** Require a human to review high-risk actions taken by an AI.

---

## Task 6 - Conclusion
Architecture and design security cannot be an afterthought. Strong systems are built on "Secure by Design" principles, where every dependency is vetted, encryption is standard, and configurations are hardened before the first user ever logs in.
