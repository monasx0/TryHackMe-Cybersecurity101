# OWASP Top 10 2025 (IAAA Failures)
## Task 1 - Introduction
This report focuses on three critical categories from the **OWASP Top 10** that deal specifically with failures in how applications handle identity and access. Understanding these vulnerabilities is vital because they represent the "keys to the kingdom"—if these systems fail, an attacker can steal data or take over an entire system.

The categories covered in this detailed analysis include:
* **A01: Broken Access Control**
* **A07: Authentication Failures**
* **A09: Logging & Alerting Failures**

---

## Task 2 - What is IAAA?
Before diving into the vulnerabilities, we must understand the framework used to verify users. **IAAA** stands for Identity, Authentication, Authorisation, and Accountability. These steps must happen in a specific order; you cannot skip a level.

* **Identity:** This is who you claim to be (e.g., your username or email address).
* **Authentication:** This is proving you are who you claim to be (e.g., providing the correct password or an OTP).
* **Authorisation:** This defines what you are allowed to do once you are inside (e.g., a regular user cannot delete other users).
* **Accountability:** This is the "paper trail." It records who performed what action, when, and from where.



Failures in any of these areas allow attackers to bypass security boundaries, leading to the vulnerabilities discussed in the following tasks.

---

## Task 3 - A01: Broken Access Control
**Broken Access Control** occurs when an application does not check the "Authorisation" step properly on the server side. Even if you are logged in, the server must verify that you have permission to access the specific data you are requesting.

### Insecure Direct Object Reference (IDOR)
A common example of this is **IDOR**. This happens when a web application uses a simple identifier (like a number) to point to data. If an attacker can change that number in the URL to see someone else's data, the access control is broken.

**Example Scenario:**
* You log in and see your profile at: `https://bank.com/profile?id=105`
* You change the URL manually to: `https://bank.com/profile?id=104`
* If the page loads the profile of user 104, you have successfully performed **Horizontal Privilege Escalation**.

**Key Takeaway:** The application must never trust the "ID" sent by the user's browser. It must always check if the currently logged-in user actually owns that ID.

---

## Task 4 - A07: Authentication Failures
**Authentication Failures** happen when the "Authentication" step is weak or can be fooled. If an attacker can guess a password, bypass a login screen, or trick the system into thinking they are the Admin, the system has failed to bind the identity to the user correctly.

### Case Study: Username Normalization Flaws
Attackers often try to fool databases by using different "casing" or hidden characters. For example, if a system has an account named `admin`, an attacker might try to register an account named `aDmiN`. 

If the application doesn't properly "normalize" (convert everything to lowercase) before checking if the user exists, it might create a duplicate entry or overwrite the permissions of the original account.



**Common Authentication Issues:**
* **Weak Passwords:** Allowing users to set "password123" without any lockout for failed attempts.
* **Username Enumeration:** When the login page says "User not found" vs "Wrong password," it tells an attacker exactly which usernames exist.
* **Session Issues:** Not giving a user a new "Session ID" after they log in, allowing an attacker to steal their old one.

---

## Task 5 - A09: Logging & Alerting Failures
This category focuses on the "Accountability" part of IAAA. **Logging** is the act of recording events, and **Alerting** is the act of notifying a human when something goes wrong. If an attacker spends three hours trying to guess a password and no one is notified, that is a failure.

**Why Logging Matters:**
Without logs, a security team is "blind." They cannot prove how a breach happened, what data was stolen, or who did it. 

**Examples of Logging Failures:**
* **Missing Events:** Not logging when someone fails to log in.
* **Vague Logs:** A log that says "Error occurred" but doesn't say which user caused it or what IP address it came from.
* **Tampering:** Storing logs on the same server as the application. If an attacker takes over the server, they can simply delete the logs to hide their tracks.

---

## Task 6 - Conclusion
Identity, Authentication, Authorisation, and Accountability (IAAA) are the pillars of web security. To prevent the vulnerabilities discussed, developers must follow these "Big Ideas":

1.  **Enforce Server-Side Checks:** Never trust the client's browser to tell the truth about permissions.
2.  **Use Unique Indexes:** Ensure that "admin" and "ADMIN" are treated as the same identity to prevent registration tricks.
3.  **Implement Rate Limiting:** Lock accounts or slow down requests if too many failed logins occur.
4.  **Centralize Logs:** Store logs on a separate, secure server so they cannot be deleted by an attacker who compromises the website.
