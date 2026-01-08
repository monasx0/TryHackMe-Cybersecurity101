# **Hashing Basics**

## Task 1 - **Introduction**
**Hashing** is a method used to verify the **integrity** of files by generating a unique **hash value** for each file. A **hash function** takes any input and produces a **fixed-size output**, known as the **hash**. Comparing **hash values** allows us to determine, with high certainty, whether two files are **identical**. **Hashing** is widely used in **file verification**, **security**, and **data integrity**. 

## Task 2 - **Hash Functions**
A **hash function** converts input data of any size into a **fixed-size hash value** (**digest**). It is **one-way**, meaning the original data cannot be derived from the **hash**. Even a small change in input produces a completely different **hash**.

### **Example**
- **File1**: `T` → **MD5**: `b9ece18c950afbfa6b0fdbfa4ff731d3`.
- **File2**: `U` → **MD5**: `4c614360da93c0a041b22e537de151eb`.
- Only one-bit difference, **hashes** are completely different.

### **Types of Hashes**
- **MD5** – fast, not secure for sensitive data.  
- **SHA1** – better than **MD5**, but now weak.  
- **SHA256** – secure, widely used today.  

## Task 3 - **Insecure Password Storage for Authentication**
**Hashing** is widely used for **password storage** and **data integrity**. For **authentication**, systems only need to verify that a user knows the **password**, not store it in **cleartext**. This differs from **password managers**, which must retrieve **passwords** in **plain text**.

### **Insecure Password Storage**
- **Plaintext storage** – e.g., **RockYou** breach exposed 14 million **passwords**.  
- **Deprecated encryption** – e.g., **Adobe** stored **passwords** in old encryption with hints.  
- **Weak hash functions** – e.g., **LinkedIn** used **SHA-1** without **salting**.  

## Task 4 - **Using Hashing for Secure Password Storage**

### **Hashing Passwords**
Instead of storing **passwords** directly, systems store their **hash values** using a **secure hashing function**. This way, even if the **database** is leaked, an attacker must **crack** each **hash** individually. Without protection, identical **passwords** produce the same **hash**, which can be exploited.  

### **Rainbow Tables**
A **Rainbow Table** is a precomputed lookup table mapping **hashes** to **plaintext passwords**. It allows attackers to quickly recover **passwords** from **hashes**. Popular tools like **CrackStation** use **rainbow tables** for fast **password cracking**.  

### **Salt**
A **salt** is a random value added to a **password** before **hashing** to make each **hash** unique. Even if two users have the same **password**, their **hashes** will be different because of the **salt**. This prevents attackers from using **rainbow tables** to quickly reverse **hashes**. **Salts** do not need to be secret and are stored alongside the **hash**. Modern algorithms like **Bcrypt** and **Scrypt** handle **salting** automatically.  

## Task 5 - **Recognising Password Hashes**

### **Linux Password Hashes**
On **Linux** systems, **password hashes** are stored in `/etc/shadow`, which is only readable by **root**. Each line contains fields separated by colons, with the hashed **password** field following the format: `$prefix$options$salt$hash`. The **prefix** identifies the **hashing algorithm**, allowing recognition of **Unix-style password hashes**. Common **prefixes** include `$y$` for **yescrypt**, `$2b$`/`$2y$` for **bcrypt**, `$6$` for **SHA-512**, and `$1$` or `$md5$` for **MD5-based hashes**.  

### **Windows Password Hashes**
Windows password hashes are stored in the **SAM** (**Security Accounts Manager**) database and use **NTLM**, a variant of **MD4**. **NTLM hashes** visually resemble **MD4** and **MD5**, so context is critical for correct identification. These **hashes** are separated into **NT hashes** and **LM hashes**, and tools such as **mimikatz** can extract them.  

### **Identifying Hash Types**
**Hash type recognition** often relies on **prefixes**, **length**, and **encoding**, as well as understanding the **application** that generated the **hash**. Reference guides, like the **Hashcat Example Hashes** page, provide standard formats and **password prefixes**, which help in both **offensive testing** and **security research**.  

## Task 6 - **Password Cracking**

### **Cracking Salted Password Hashes**
**Password hashes** cannot be decrypted because they are not encrypted. When a **salt** is used, attackers must recreate the **hashing process** by hashing many possible **passwords**, appending the **salt** where required, and comparing the result to the target **hash**. Tools such as **Hashcat** and **John the Ripper** are commonly used for this purpose, often alongside **wordlists** like **rockyou.txt**.  

### **GPU‑Based Hash Cracking**
Modern **GPUs** contain thousands of cores optimized for parallel calculations, making them extremely effective for cracking many **hash types**. **Hashing algorithms** like **MD5** and **SHA-1** can be cracked significantly faster using **GPUs**. Algorithms like **Bcrypt** are designed to reduce GPU speed advantages, making brute-force attacks less effective.  

### **Practical Hash Cracking**
In practice, hashes are provided for identification and cracking using appropriate **tools**. While online services and **rainbow tables** may work for unsalted **hashes**, relying on them limits learning. Using **Hashcat** or **John the Ripper** with **wordlists** provides hands-on experience and a deeper understanding of real-world **password security**.  

## Task 7 - **Hashing for Integrity Checking**

### **Integrity Checking**
**Hashing** can verify that files have not been altered. Because the same input always produces the same **hash**, even a single-bit change results in a completely different output. This property allows checking downloaded files against official **hashes** to ensure authenticity. **Hashes** also help identify duplicate files efficiently.  

### **HMAC (Keyed-Hash Message Authentication Code)**
An **HMAC** combines a **cryptographic hash function** with a **secret key** to provide both **authenticity** and **integrity**. It proves that a message comes from a trusted source and has not been altered. **HMACs** are widely used in secure **communications** and **API authentication**.

#### **How HMAC Works**
1. The **secret key** is padded to match the **hash function**’s block size.  
2. The padded **key** is XORed with a constant (**opad/ipad**).  
3. The **message** is hashed using the **hash function** with the XORed **key**.  
4. The result is hashed again using the **key** with the other constant.  
5. The final output is the **HMAC value**, a fixed-size string.  

## Task 8 - **Conclusions**
**Hashing** is a fundamental concept in **cybersecurity**, providing **data integrity**, **password security**, and **authentication verification**. By converting input data into **fixed-size hash values**, even small changes are easily detectable. **Hashes** cannot be reversed, making them ideal for storing **passwords** securely, especially when combined with **salts** to prevent **rainbow table attacks**. **HMAC** extends hashing to verify both **authenticity** and **integrity**.  

### **What I Learned**
- **Hash functions** produce **fixed-size**, **one-way outputs** sensitive to input changes.  
- Proper **password storage** requires **secure hashing algorithms** and unique **salts**.  
- **Rainbow tables** exploit unsalted **hashes**; **salting** mitigates this risk.  
- **Linux** and **Windows** store **hashed passwords** differently, with specific formats and algorithms.  
- **Hash cracking** can be performed using **tools** like **Hashcat** and **John the Ripper**, often leveraging **GPUs** for speed.  
- **Hashing** is essential for **file integrity checks**, **duplicate detection**, and secure **communications** through **HMAC**.
