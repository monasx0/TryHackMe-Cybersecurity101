# Digital Forensics Fundamentals

## Task 1 - Overview of Digital Forensics
**Forensics** refers to the scientific methods and procedures used to investigate and solve crimes. When these methods are applied to digital devices and cybercriminal activity, it is known as **Digital Forensics**. As our world becomes increasingly digital, almost every crime leaves a "digital footprint" on devices such as laptops, mobile phones, or cloud storage.

### Case Study: The Bank Robbery
To understand the impact of digital forensics, consider a law enforcement raid on a suspect's home. The following evidence was recovered from their devices:
* **Digital Maps:** Planning documents found on a laptop showing the bank's layout.
* **Security Intelligence:** A list of the bank's physical security controls and bypass plans found on a hard drive.
* **Communication Logs:** Illegal chat records and call logs on a mobile phone directly linking the suspect to the robbery.
* **Media Evidence:** Videos and photos of previous crimes stored as "trophies" on the laptop.

This evidence is vital for legal proceedings, but it must be collected and handled following strict scientific and legal procedures.



---

## Task 2 - Digital Forensics Methodology
The **NIST (National Institute of Standards and Technology)** defines a standard four-phase process to ensure that digital investigations are thorough and legally defensible.

### The Four Phases of Methodology:
1.  **Collection:** Identifying and securing all potential evidence sources (USBs, hard drives, cameras). It is critical to ensure the original data is **not tampered with** during this stage.
2.  **Examination:** Filtering the vast amount of collected data. This involves extracting specific information, such as files created on a certain date or data belonging to a specific user.
3.  **Analysis:** The core phase where investigators correlate different pieces of evidence to draw a chronological conclusion of the suspect's activities.
4.  **Reporting:** Preparing a detailed technical document for law enforcement and executive management. This must include an **Executive Summary** for non-technical readers.

### Specialized Fields of Forensics:
* **Computer Forensics:** Investigating desktops and laptops.
* **Mobile Forensics:** Extracting GPS data, SMS, and call logs from smartphones.
* **Network Forensics:** Analyzing network traffic logs to track movement across a network.
* **Cloud & Email Forensics:** Investigating remote infrastructure and phishing/fraudulent email campaigns.



---

## Task 3 - Evidence Acquisition
Acquiring evidence is a highly sensitive task. If the data is modified even slightly, it may be thrown out of court.

### Key Acquisition Standards:
* **Proper Authorization:** Investigators must have legal warrants or permission. Evidence collected without **authorization** is usually inadmissible in legal proceedings.
* **Chain of Custody:** A formal document that tracks every person who touched the evidence, the time of access, and where it was stored. This proves the **integrity** of the evidence.
* **Write Blockers:** Specialized hardware devices that allow an investigator to read data from a drive while **blocking any write commands**. This prevents the forensic workstation from accidentally changing file timestamps or metadata.



---

## Task 4 - Windows Forensics
Since Windows is the most common operating system used globally, it is frequently the target of forensic investigations. Analysts typically collect two types of "images" (copies) from a system.

### Types of Forensic Images:
1.  **Disk Image:** A bit-by-bit copy of the **non-volatile** storage (HDD/SSD). This contains saved files, browser history, and deleted items.
2.  **Memory Image:** A copy of the **RAM**. This is **volatile data** that is lost when the computer is turned off. It contains running processes, passwords in memory, and active network connections. **This must be collected first** before the system is shut down.

### Essential Forensic Tools:
| Tool | Function | Use Case |
| :--- | :--- | :--- |
| **FTK Imager** | Acquisition & Analysis | Creating bit-by-bit disk images via a GUI. |
| **Autopsy** | Analysis | Open-source platform for searching keywords and recovering deleted files. |
| **DumpIt** | Acquisition | A command-line utility for capturing memory images (RAM). |
| **Volatility** | Analysis | A powerful tool used specifically for analyzing memory images using plugins. |



---

## Task 5 - Conclusion
Digital forensics is a meticulous science that bridges the gap between technology and the law. By following the **NIST methodology**, maintaining a **Chain of Custody**, and using tools like **Autopsy** and **Volatility**, investigators can turn raw data into evidence that stands up in a court of law.
