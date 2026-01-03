# Windows Fundamentals Par 03
## Task 1 - Introduction
This room will provide an overview of the security features within the Windows operating system.

## Task 2 - Windows Updates
#### Windows Update
Windows Update is a Microsoft service that delivers security patches, feature enhancements, and updates for the Windows operating system and other Microsoft products, such as Microsoft Defender.

Updates are typically released on the second Tuesday of each month, known as Patch Tuesday. Critical updates, however, may be pushed outside this schedule if necessary.

You can access Windows Update via **Settings** or, alternatively, through the **Run dialog** or **Command Prompt** using the command:`control /name Microsoft.WindowsUpdate`

## Task 3 - Windows Security
#### Windows Security
Per Microsoft, “Windows Security is your home to manage the tools that protect your device and your data”. Windows Security can be accessed via Settings or by opening the Windows Security app directly.
#### Protection Areas
- Virus & threat protection
- Firewall & network protection
- App & browser control
- Device security

#### Status Icons
- **Green** – Device is  protected; no recommended actions.
- **Yellow** – Safety recommendation requires review.
- **Red** – Immediate attention needed.

## Task 4 - Virus and Threat Protection
Windows Security divides Virus & Threat Protection into two main sections:
1. Current Threats
2. Virus and threat protection settings

### Current Threats
#### Scan Options
- **Quick Scan** – Checks common folders where threats are usually found.
- **Full Scan** – Scans all files and running programs; may take over an hour.
- **Custom Scan** – Scan specific files or folders you choose.

#### Threat History
- **Last Scan** – Shows results of the most recent automatic scan.
- **Quarantined Threats** – Isolated items that cannot harm the device.
- **Allowed Threats** – Files you chose to allow.

### Virus and Threat Protection Settings
- **Real-time Protection** – Detects and blocks malware immediately.
- **Cloud-delivered Protection** – Uses cloud data to improve threat detection.
- **Automatic Sample Submission** – Sends samples to Microsoft to improve protection.
- **Controlled Folder Access** – Protects important folders from untrusted apps.
- **Exclusions** – Specify files or folders to skip during scans.
- **Notifications** – Alerts you to important security events.

### Updates and Ransomware Protection
- **Check for Updates** – Update antivirus definitions manually.
- **Ransomware Protection** – Requires Real-time Protection and Controlled Folder Access to be enabled.

## Task 5 - Firewall and Network Protection

### Firewall & Network Protection
A firewall controls what network traffic is allowed to enter or leave your device. Think of it as a security guard checking everything that tries to pass through your system's ports.
#### Firewall Profiles
- **Domain** – Used on networks where the system can authenticate to a domain controller.
- **Private** – Assigned by the user for home or trusted networks.
- **Public** – Default profile for public networks like coffee shops or airports.

#### Advance Settings
Configuring firewall rules is intended for advanced users. To open advanced settings, use the Run dialog **Win + R** and type`wf.msc`.

## Task 6 - App and Browser Control
### App and Browser Control
**Microsoft Defender SmartScreen** helps protect your device from phishing sites, malware, and potentially harmful downloads. You can configure SmartScreen to:
- **Warn** – Notify you about suspicious apps or files
- **Block** – Prevent access to risky apps or files
- **Off** – Disable protection

SmartScreen checks apps and files downloaded from the web, helping prevent unrecognized or potentially malicious software from running.

## Task 7 - Device Security
### Core Isolation & Security Processor
**Core Isolation** provides additional system security by isolating critical processes from the rest of the operating system.
- Memory Integrity – Prevents attacks from injecting malicious code into high-security processes.

#### Security Processor
Windows devices with a **Trusted Platform Module** (**TPM**) offer hardware-based security functions. TPM is a secure cryptographic processor that performs cryptographic operations and protects against tampering, helping safeguard sensitive information.

## Task 8 - BitLocker

### BitLocker
**BitLocker** is a Windows feature that encrypts drives to protect data from theft or unauthorized access, especially on devices with a Trusted Platform Module (TPM).

## Task 9 - Volume Shadow Copy Service
### Volume Shadow Copy Service (VSS)
Volume Shadow Copy Service creates consistent snapshots of data for backup purposes. These copies are stored in the **System Volume Information** folder on drives with protection enabled.
When VSS is turned on, you can:
- Create a restore point
- Perform a system restore
- Configure restore settings

## Task 9 - Conclusion
In this room, I covered several built-in Windows security tools that help keep the device protected.

### What I Learned
- How to manage **Windows Update**
- Navigate **Windows Security** and its protection areas
- Configure **Virus and Threat Protection** and understand scanning options
- Manage **Firewall and Network Protection** and app access through firewall profiles
- Understand **SmartScreen**
- Learn about **Core Isolation** and **Memory Integrity** to prevent attacks
- Understand **Trusted Platform Module** (**TPM**) and **BitLocker** for data encryption
- Use Volume **Shadow Copy Service** (**VSS**) for system restore and data protection





