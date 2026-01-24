# FlareVM

## Task 1 - Introduction to FlareVM (Forensics, Logic Analysis, and Reverse Engineering)
FlareVM is a specialized Windows-based distribution curated by the FLARE Team at Mandiant. It is designed specifically for malware analysts, incident responders, and forensic investigators. It functions as a comprehensive ecosystem that consolidates complex toolsets into a single, hardened environment for unraveling digital mysteries and gain insight into malicious executable behavior.

## Task 2 - Comprehensive Tool Arsenal
FlareVM categorizes its tools to cover every stage of the investigative lifecycle.

### A. Reverse Engineering & Debugging
These tools allow analysts to solve the "puzzle backward," identifying code logic and correcting errors at the assembly level.
* **Ghidra:** Open-source suite developed by the NSA for deep reverse engineering.
* **x64dbg:** Modern, open-source debugger for x64 and x32 binaries.
* **OllyDbg:** A classic debugger for assembly-level analysis.
* **Radare2:** A powerful command-line framework for reverse engineering.
* **Binary Ninja:** High-performance disassembler and decompiler.
* **PEiD:** Specialized in detecting packers, cryptors, and compilers.

### B. Disassemblers & Decompilers
Essential for breaking machine code into a human-readable format to understand control flow.
* **CFF Explorer:** A PE editor for analyzing and modifying Portable Executable headers.
* **Hopper Disassembler:** A combined debugger/disassembler for various architectures.
* **RetDec:** A machine-code-to-C decompiler.

### C. Static & Dynamic Analysis
* **Process Hacker:** An advanced process watcher and memory editor.
* **PEview:** A lightweight viewer for internal PE file structures.
* **Dependency Walker:** Visualizes the DLL dependencies of an executable.
* **DIE (Detect It Easy):** Quickly identifies compilers and protection layers.

### D. Forensics & Incident Response
* **Volatility:** The industry-standard framework for RAM dump forensics.
* **Rekall:** Specialized memory forensic framework for incident response.
* **FTK Imager:** Used for disk image acquisition and evidence preservation.

### E. Network Analysis
* **Wireshark:** Captures and inspects network protocol traffic in real-time.
* **Nmap:** Performs vulnerability scanning and network mapping.
* **Netcat:** The "Swiss Army Knife" of networking for reading/writing data across connections.

### F. File Analysis & Hex Editing
* **FileInsight:** Hex editor for deep inspection and binary editing.
* **Hex Fiend & HxD:** High-performance hex editors for viewing raw byte data.

### G. Sysinternals Suite
Advanced utilities for Windows system diagnosis.
* **Autoruns:** Identifies programs configured to launch during boot-up.
* **Process Explorer:** Detailed view of active processes and parent-child relationships.
* **Process Monitor (Procmon):** Logs real-time file system, registry, and thread activity.

---

## Task 3 - Detailed Investigative Tool Overview

| Tool | Capability | Forensic Value |
| :--- | :--- | :--- |
| **Procmon** | Real-time logging | Tracks if processes like `lsass.exe` are being targeted for credential dumping. |
| **Process Explorer** | Process Tree | Validates Process IDs (PIDs) and tracks spawned child processes (e.g., from Word docs or ISOs). |
| **HxD** | Byte Inspection | Identifies file types via headers (e.g., `4D 5A` for executables) and checks for corruption. |
| **CFF Explorer** | Integrity Checks | Generates MD5/SHA-1 hashes to verify if system files have been altered by malware. |
| **Wireshark** | Traffic Triage | Identifies C2 communication via protocols like TLSv1.2 or suspicious TCP connections. |
| **PEStudio** | Risk Assessment | Performs static triage to find blacklisted APIs and suspicious metadata. |
| **FLOSS** | String De-obfuscation | Automatically extracts hidden strings (URLs, IPs, file paths) that `strings.exe` would miss. |

---

## Task 4 - Dissection of Malicious File: `windows.exe`

### Initial Static Triage (PEStudio)
The file `windows.exe` was flagged as a potential threat. Static analysis provided the following indicators:
* **Hashes:** * MD5: `9FDD4767DE5AEC8E577C1916ECC3E1D6`
    * SHA-1: `A1BC55A7931BFCD24651357829C460FD3DC4828F`
* **Masquerading:** The file description claims to be the "Registry Editor" (REGEDIT), but it was located in a user download folder rather than `C:\Windows\System32`.
* **Metadata Anomalies:** Metadata contains Russian text (`Редактор реестра`), which is highly suspicious for English-speaking environments.
* **Obfuscation Indicators:** The absence of a "Rich Header" suggests the file is packed or intentionally obfuscated to evade static detection.

### Import Address Table (IAT) Analysis
Blacklisted API calls were identified:
* **set_UseShellExecute:** Allows the malware to spawn additional processes via the OS shell.
* **CryptoStream / RijndaelManaged:** Confirms the binary uses AES encryption, likely for encrypting C2 traffic or ransom activities.

### Advanced String Extraction (FLOSS)
Running `FLOSS.exe .\windows.exe > windows.txt` yielded significant results:
* Even though FLOSS noted limited support for .NET de-obfuscation, it successfully extracted static strings that mirrored the suspicious blacklisted APIs found in PEStudio, confirming the cryptographic and process-spawning capabilities of the binary.

---

## Task 5 - Dynamic Analysis Case Study: `cobaltstrike.exe`

### Process Observation (Process Explorer)
* **Goal:** Determine if the binary connects to a C2 (Command and Control) server.
* **Process Tree:** Verified that `Explorer.exe` spawned `cobaltstrike.exe` (PID: 4756).
* **Network Check:** Under the **TCP/IP tab** in Properties, a connection attempt was observed, providing a live look at the destination IP.

### Behavior Confirmation (Procmon)
To verify the findings of Process Explorer, Procmon was utilized with a filter:
1.  **Filter:** `Process Name` contains `cobalt`.
2.  **Observation:** Procmon logged granular activity, confirming a steady network connection to an external, unknown IP address.
* **Confirmed C2 IP:** `47.120.46.210`

---

## Task 6 - Conclusion
FlareVM provides a streamlined, professional-grade environment for end-to-end malware analysis. By combining static analysis (PEStudio, FLOSS) with dynamic behavioral monitoring (Procmon, Process Explorer), analysts can move from initial suspicion to a confirmed list of Indicators of Compromise (IOCs), such as malicious IPs, cryptographic functions, and process masquerading.
