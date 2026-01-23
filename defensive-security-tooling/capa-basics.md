# CAPA Basics

## Task 1 - Introduction to CAPA
CAPA (Common Analysis Platform for Artifacts) is a static analysis tool developed by Mandiant for identifying capabilities in executable files (PE, ELF, .NET, etc.). It automates the extraction of reverse engineering knowledge by matching file characteristics against a comprehensive library of behavioral rules.

## Task 2 - Technical File Overview
The analysis was performed on `cryptbot.bin`. Initial static metadata includes:
* **Hashes:** * MD5: `3b9d26d2e7433749f2c32edb13a2b0a2`
    * SHA256: `ae7bc6b6f6ecb206a7b957e4bb86e0d11845c5b2d9f7a00a482bef63b567ce4c`
* **Architecture:** i386 (Windows PE format)
* **Analysis Type:** Static

## Task 3 - Behavioral Framework Mapping
CAPA maps identified capabilities to three primary industry standards:

### MITRE ATT&CK
Provides a playbook for adversary tactics and techniques.
* **Defense Evasion:** Obfuscated Information [T1027], Sandbox Evasion [T1497.001].
* **Persistence:** Scheduled Tasks via `at` [T1053.002] and `schtasks` [T1053.005].
* **Execution:** PowerShell [T1059.001] and Shared Modules [T1129].

### MAEC (Malware Attribute Enumeration and Characterization)
Categorizes the high-level nature of the binary.
* **Launcher:** Exhibits behaviors that trigger specific malicious actions (dropping payloads, persistence).
* **Downloader:** (Potential) Capabilities for fetching secondary stage resources.

### Malware Behavior Catalogue (MBC)
A granular catalog focused on malware-specific objectives.
| Objective | Behavior | Method/Identifier |
| :--- | :--- | :--- |
| **Data** | Encode Data | Base64 [C0026.001], XOR [C0026.002] |
| **Process** | Create Process | [C0017] |
| **Anti-Static** | Code Obfuscation | Stack Strings [B0032.017] |

---

## Task 4 - Capability and Namespace Hierarchy
CAPA organizes its findings using a hierarchical Namespace system.

### Top-Level Namespaces (TLN)
* **anti-analysis:** Evasion, packing, and anti-debugging.
* **communication:** Network interaction (HTTP, User-Agents).
* **data-manipulation:** Transformation logic (Encryption/Encoding).
* **host-interaction:** File system and process manipulation.
* **nursery:** A staging area for unpolished or experimental rules (e.g., cryptocurrency strings).

### Case Study: Persistence
The capability `schedule task via schtasks` is found under the `persistence/scheduled-tasks` namespace. This indicates the binary uses the Windows Task Scheduler to ensure it runs repeatedly on the host.

## Task 5 - Advanced Analysis: CAPA Web Explorer
For deep-dive investigations, CAPA supports verbose and very verbose outputs (`-v` or `-vv`).
* **JSON Export:** Generated using `capa.exe -j -vv .\file.bin > output.json`.
* **Visualization:** The `.json` file can be uploaded to the **CAPA Web Explorer** to see exactly which strings or API calls triggered a rule.
* **Example Trigger:** The `anti-VM` rule was triggered by the regex string `/VMWare/i`, identifying that the malware checks for virtualized environments to avoid being analyzed.

## Task 6 - Conclusion
CAPA serves as a bridge between raw code and actionable intelligence. By automating the identification of tactics like persistence, evasion, and data encoding, it allows security professionals to rapidly assess the risk profile of a binary without performing exhaustive manual reverse engineering.
