# CyberChef Basics

## Task 1 - Introduction to CyberChef
CyberChef is an intuitive, web-based "Swiss Army knife" for data. It allows users to perform complex operations—ranging from simple encoding like **Base64** to advanced **AES encryption**—all within a browser. It uses a "Recipe" concept where multiple operations are linked together to process data.



---

## Task 2 - Accessing the Tool
* **Online:** Accessible via any modern web browser with an internet connection.
* **Offline:** Can be run locally by downloading the latest stable release from GitHub, ensuring privacy and availability without internet access.

---

## Task 3 - Navigating the Interface
The interface is divided into four primary functional areas:

1.  **Operations:** A searchable library of all available tools (filters, encodings, etc.).
2.  **Recipe:** The "heart" of the tool where you drag and drop operations to build a processing chain.
3.  **Input:** The area where you paste or upload the data you wish to transform.
4.  **Output:** The visual space where the results of the "Bake" are displayed.

### Common Operations:
* **To Base64:** Encodes raw data into ASCII format.
* **ROT13:** A Caesar cipher that rotates letters by 13 positions.
* **URL Encode/Decode:** Converts special characters into percent-encoding for web compatibility.

---

## Task 4 - The CyberChef Thought Process
To use CyberChef effectively, follow these four steps:
1.  **Set an Objective:** Determine what you want to achieve (e.g., "Decode this gibberish").
2.  **Input Data:** Paste the suspicious string or file into the Input pane.
3.  **Build a Recipe:** Search for and select operations (e.g., **From Base64**, **Extract IPs**).
4.  **Analyze Output:** Check if the result is readable or meets your goal.



### Specialized Extractors
CyberChef can automatically pull specific data types from large blocks of text:
* **Extract IP addresses:** Finds IPv4 and IPv6 addresses.
* **Extract URLs:** Finds web addresses (requires protocols like http/ftp).
* **Extract email addresses:** Finds strings in the `user@domain.com` format.

---

## Task 5 - Data Formats and Base64 Logic
Understanding how data is transformed is key to digital forensics. **Base64** is one of the most common encoding formats encountered in security operations.

### Simplified Base64 Encoding (Example: "THM")
1.  **Binary Conversion:** Characters are converted to 8-bit binary (T=01010100, H=01001000, M=01001101).
2.  **Bit Splitting:** The continuous string of bits is divided into 6-bit chunks.
3.  **Decimal Mapping:** Each 6-bit chunk is converted to a decimal number.
4.  **Index Lookup:** The decimal number is matched against the Base64 Index Table (0-63).

**Result:** "THM" becomes **VEhN**.

---

## Task 6 - Conclusion
CyberChef simplifies the often-tedious task of data transformation through a visual, drag-and-drop interface. By mastering the use of **Extractors**, **Base Encodings**, and **Timestamp** conversions, analysts can rapidly decode obfuscated data and identify indicators of compromise. While CyberChef is ideal for quick browser-based tasks, it remains a foundational tool in the security practitioner’s arsenal for everyday data manipulation.
