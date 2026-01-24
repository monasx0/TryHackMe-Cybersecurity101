# REMnux

## Task 1 - Introduction
REMnux is a specialized Linux distribution designed for malware analysis and reverse engineering. It provides a pre-configured environment with essential tools such as Volatility, YARA, Wireshark, and oledump, allowing for safe dissection of malicious artifacts.

## Task 2 - Static Analysis of OLE2 Files
Analysis was conducted on `agenttesla.xlsm` to identify embedded malicious macros.

### Data Stream Identification
Running `oledump.py agenttesla.xlsm` revealed multiple data streams.
* **Stream A3/A4:** Indicators of VBA Macros (marked with 'm' or 'M').
* **Specific Target:** `A4: M 688 'VBA/ThisWorkbook'` was selected for decompression.

### Macro Deobfuscation
Using the `--vbadecompress` flag, the macro logic was exposed. The script utilized character replacement (`*` and `^`) to hide a PowerShell command.


**Decoded Command Breakdown:**
* **-WindowStyle hidden:** Executes without a visible terminal.
* **-executionpolicy bypass:** Bypasses local security restrictions.
* **Invoke-WebRequest:** Downloads `Doc-3737122pdf.exe` from `http://193.203.203.67/rt/`.
* **Start-Process:** Executes the downloaded payload from the temporary directory.

---

## Task 3 - Network Simulation
To observe malware behavior without internet access, **INetSim** was used to simulate common services (DNS, HTTP, SMTP).

### Configuration Steps
1.  **Identify IP:** Locate the REMnux IP address via `ifconfig`.
2.  **Edit Config:** Modify `/etc/inetsim/inetsim.conf`.
3.  **Set DNS:** Update `dns_default_ip` to the REMnux IP to redirect all traffic to the local simulator.
4.  **Launch:** Execute `sudo inetsim` to begin the simulation.

---

## Task 4 - Memory Forensics
Memory analysis was performed on `wcry.mem` (WannaCry) to extract forensic artifacts.

### Key Volatility Plugins
| Plugin | Purpose |
| :--- | :--- |
| **windows.pstree.PsTree** | Visualizes process parent-child relationships. |
| **windows.cmdline.CmdLine** | Identifies command-line arguments used by processes. |
| **windows.malfind.Malfind** | Locates potential injected code in memory ranges. |
| **windows.filescan.FileScan** | Scans for file objects residing in memory. |

### Bulk Preprocessing (Automated Loop)
To expedite analysis, a bash loop was used to run all plugins and save results to text files:
`for plugin in [list_of_plugins]; do vol3 -q -f wcry.mem $plugin > wcry.$plugin.txt; done`



### String Extraction
Printable strings were extracted in multiple encodings to capture hidden metadata:
* **ASCII:** Standard printable text.
* **Little-Endian (-e l):** 16-bit strings typical of Windows environments.
* **Big-Endian (-e b):** 16-bit strings for specific architectures.



## Task 5 - Conclusion
This workflow demonstrates the power of REMnux in handling an end-to-end investigation: from initial document analysis and deobfuscation to network simulation and automated memory evidence preprocessing.
