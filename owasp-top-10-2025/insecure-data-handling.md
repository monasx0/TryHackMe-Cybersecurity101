# OWASP Top 10 2025: Insecure Data Handling

## Task 1 - Introduction
This report provides a professional breakdown of three specific categories from the **OWASP Top 10 (2025)**. These categories focus on how applications process user-provided data and how they behave when managing sensitive information. 

By understanding these flaws, developers and security professionals can implement better defenses against modern web exploits. The focus areas for this report are:
* **A04: Cryptographic Failures**
* **A05: Injection**
* **A08: Software or Data Integrity Failures**

---

## Task 2 - A04: Cryptographic Failures
**Cryptographic Failures** occur when an application fails to protect sensitive data at rest (stored on a disk) or in transit (moving across a network). This is often the result of "cutting corners" in security implementation.

### Understanding the Risk
Security is only as strong as its weakest link. Common mistakes include:
* **Weak Hashing:** Storing user passwords using outdated methods like MD5 or SHA1, which can be cracked in seconds using modern hardware.
* **Hard-coded Secrets:** Embedding API keys or database passwords directly into the source code where they can be discovered by anyone with access to the repository.
* **"Rolling Your Own Crypto":** Attempting to invent a custom encryption algorithm rather than using industry-standard, battle-tested methods.

### Prevention Strategies
To defend against these failures, organizations must adopt modern standards:
* **Use Robust Hashing:** Implement "slow" hashing functions like **bcrypt**, **scrypt**, or **Argon2** for passwords. These are designed to resist brute-force attacks.
* **Secret Management:** Store credentials in dedicated environments like **AWS Secrets Manager** or **HashiCorp Vault** instead of configuration files.
* **Standard Libraries:** Always use verified cryptographic libraries (such as OpenSSL or BoringSSL) rather than custom-built scripts.



---

## Task 3 - A05: Injection
**Injection** remains one of the most dangerous and common web vulnerabilities. It occurs when "untrusted" user input is sent to an interpreter as part of a command or query.

### The Core Problem
The application confuses **data** provided by a user with **code** that the system should execute. This allows an attacker to "inject" their own commands into the application's logic.

**Common Types of Injection:**
* **SQL Injection (SQLi):** Inserting database queries into input fields to steal or delete data.
* **Command Injection:** Tricking the server into executing OS-level commands (e.g., `ls`, `whoami`, or `rm -rf`).
* **Server-Side Template Injection (SSTI):** Exploiting web templates to execute malicious code on the server.
* **AI Prompt Injection:** Manipulating Large Language Models (LLMs) to ignore safety guardrails.

### Prevention Strategies
The golden rule is: **Never trust user input.**
* **Parameterized Queries:** Use "Prepared Statements" for all database interactions. This ensures the database treats input strictly as data, not executable code.
* **Input Validation:** Enforce strict allow-lists. For example, if a field asks for a "Zip Code," the application should reject any input that contains letters or special characters.
* **Safe APIs:** Avoid using functions that call the system shell directly. Use built-in programming language APIs that handle arguments safely.



---

## Task 4 - A08: Software or Data Integrity Failures
**Software or Data Integrity Failures** occur when an application assumes that code or data is safe without verifying where it came from or if it has been changed.

### Understanding the Risk
In modern development, applications are rarely built from scratch. They rely on "Supply Chains"—plugins, libraries, and automated updates. If an attacker compromises a library that your app uses, your app becomes a vehicle for their attack.

**Common Patterns:**
* **Unverified Updates:** An application downloads a "patch" from the internet and installs it without checking a digital signature.
* **Insecure Deserialization:** Taking complex data (like a Python object or JSON) and turning it back into live code without checking if the data has been modified to include a "payload."

### Prevention Strategies
* **Digital Signatures:** Only allow software updates that are cryptographically signed by a trusted source.
* **Checksum Verification:** Use hashes (like SHA-256) to verify that a file has not been altered during download.
* **Vetted Sources:** Ensure that all third-party libraries used in the CI/CD (Continuous Integration/Continuous Deployment) pipeline are from reputable, maintained repositories.



---

## Task 5 - Conclusion
The 2025 OWASP Top 10 highlights that while web technologies evolve, fundamental mistakes regarding user input and data handling persist. By focusing on the **IAAA** (Identity, Authentication, Authorization, and Accountability) framework and ensuring that every piece of data crossing a trust boundary is validated and verified, developers can significantly reduce the attack surface of their applications.
