# **Cryptography Basics**

## **Task 1 - Introduction**
**Cryptography** is the science of securing **information**. It ensures that **messages** exchanged between parties cannot be read or altered by unauthorized third parties. **Cryptography** also helps verify the **identity** of the parties involved, ensuring that you are communicating with the intended **server** or **person**.

## **Task 2 - Importance of Cryptography**

### **Applications of Cryptography**
Even if you do not interact directly with **cryptography**, it underpins many **technologies** you use every day:
#### **Web Logins**
- Your **credentials** (e.g., **amazon login**) are **encrypted** when sent to the **server** to prevent **interception**.
#### **Secure Shell (SSH)**
- Establishes an **encrypted tunnel** between your **client** and **server** to prevent **eavesdropping**.
#### **Online Banking**
- **Browsers** verify **server certificates** to confirm you are communicating with your **bank** and not an **attacker**.
#### **File Integrity Verification**
- **Cryptographic hash functions** allow you to confirm that **downloaded files** are identical to the **original**.
### **Cryptography in Industry and Compliance**
#### 1. **Payment Card Industry**
- Companies handling **credit card data** must comply with the **Payment Card Industry Data Security Standard (PCI DSS)**.
- **Data** must be **encrypted**:
  - While **stored** on **servers**
  - While being **transmitted** over **networks**
 

#### 2. **Healthcare Data**
**Medical records** require compliance with various **legal standards**, which vary by **country**:
- USA: **HIPAA**, **HITECH**
- EU: **GDPR**
- UK: **Data Protection Act (DPA)**

These **regulations** highlight the importance of **cryptography** in protecting **sensitive personal information**.

## **Task 3 - Plaintext to Ciphertext**
In **cryptography**, we start with the **plaintext**, which is the readable **data** we want to protect. This can be anything from a simple **text message** or **image** to **credit card information** or **medical records**.

The **plaintext** is passed through an **encryption function** along with a **key**. The **encryption function** converts the **plaintext** into **ciphertext**, which is the **unreadable, scrambled** version of the **message**.
- **Cipher**: The **algorithm** or **method** used to convert **plaintext** into **ciphertext** and vice versa.
- **Key**: A **secret string of bits** used by the **cipher** to **encrypt** or **decrypt data**. The **cipher** itself is usually public knowledge, but the **key** must remain **secret**.


### **Main Takeaways**
- **Plaintext**: Original, readable **message** or **data** before **encryption**. Can include **documents**, **images**, **multimedia files**, or any **binary data**.
- **Ciphertext**: Scrambled, unreadable version of the **plaintext** after **encryption**. No meaningful **information** about the original **message** can be derived from it, except perhaps its approximate **size**.
- **Cipher**: **Algorithm** used to convert **plaintext** into **ciphertext** and back again, usually developed by **mathematicians**.
- **Key**: **Secret input** to the **cipher** that enables **encryption** and **decryption**.
- **Encryption**: Process of converting **plaintext** into **ciphertext** using a **cipher** and **key**. The **cipher** is public, but the **key** is **secret**.
- **Decryption**: Reverse process of **encryption**; converts **ciphertext** back into **plaintext** using the **cipher** and **key**. Without the correct **key**, recovering **plaintext** should be infeasible.

## **Task 4 - Historical Ciphers**
### **Caesar Cipher**
**Cryptography** has a long **history**, dating back to **ancient Egypt (1900 BCE)**. One of the simplest historical **ciphers** is the **Caesar Cipher** from the **first century BCE**.
#### **How It Works**
Each letter in the **plaintext** is shifted by a fixed number to create the **ciphertext**.
Example:
- **Plaintext**: TRYDODGEME
- **Key**: 3 (**right shift**)
- **Ciphertext**: WUBGRGJHPH
#### **Decryption**
To **decrypt**, shift letters in the opposite direction using the same **key**.

**Example**: Shift **left** by 3 to recover the original **plaintext**.
### **Security Issues**
- The **Caesar Cipher** is **insecure** by modern standards because there are only 25 possible **keys** (**English alphabet** has 26 letters).
- It is vulnerable to **brute-force attacks**, where all possible **keys** can be tried quickly.

### **Other Historical Ciphers**
- **Vigenère Cipher** (16th century)
- **Enigma Machine** (World War II)
- **One-Time Pad** (Cold War)

## **Task 5 - Types of Encryption**
### 1. **Symmetric Encryption**
**Symmetric Encryption**, also called **private key cryptography**, is a method of **encryption** where the same **key** is used for both **encrypting** and **decrypting data**. The **security** of **symmetric encryption** relies entirely on keeping the **key** **secret**. Anyone who obtains the **key** can read or alter the **data**, so sharing and protecting the **key** is critical.
#### **Main Points:**
- **Key** must be kept **secret**.
- Sharing the **key** securely with recipients can be challenging.
- **Fast** and **efficient**, but not practical for many recipients without a secure channel, because the **key** must be shared securely.
- #### **Examples**
- **DES (Data Encryption Standard)**
- **AES (Advanced Encryption Standard)**
### 2. **Asymmetric Encryption**
**Asymmetric encryption**, also called **public key cryptography**, is a method of **encryption** that uses a **pair of keys**: a **public key** for **encryption** and a **private key** for **decryption**. The **public key** can be shared openly, while the **private key** must remain **secret**. This approach allows **secure communication** without the need to exchange a **shared secret key** in advance.
#### **Main Points:**
- **Slower** than **symmetric encryption**.
- **Keys** are usually much larger (e.g., **RSA 2048-bit** minimum).
- **Security** relies on **mathematical problems** that are easy to compute one way, but extremely difficult to reverse.
- Enables **secure communication** without sharing a **secret key** beforehand.
#### **Examples**
- **RSA (Rivest–Shamir–Adleman)**
- **Diffie-Hellman**

## **Task 6 - Basic Math**

### **Mathematical Building Blocks of Cryptography**
### 1. **XOR (Exclusive OR) Operation**
**XOR** is a **binary logical operation** that returns 1 if the **bits** are different and 0 if they are the same.
#### **Truth Table**
| A | B | A⊕B |
| - | - | --- |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

#### **Properties**
- A ⊕ A = 0
- A ⊕ 0 = A
- **Commutative**: A ⊕ B = B ⊕ A
- **Associative**: (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C)
#### **Use in Cryptography**
Can serve as a simple example of **symmetric encryption algorithm**:
- **Ciphertext C = P ⊕ K** (P = **plaintext**, K = **key**)
- **Decryption**: P = C ⊕ K
### 2. **Modulo Operation**
**Modulo** (written as % or **mod**) gives the **remainder** after division of one number by another.
#### **Examples**
- 25 % 5 = 0
- 23 % 6 = 5
#### **Properties**
- Result is always **non-negative** and less than the **divisor**: 0 ≤ a % n < n
- Not **reversible**: Multiple values can satisfy the same **modulo equation**.
#### **Use in Cryptography**
- Fundamental in **algorithms** involving **large numbers**, e.g., **RSA**, **Diffie-Hellman**.
- **Programming languages** like **Python** handle **arbitrary-size integers** to support **cryptographic calculations**.

## **Task 7 - Conclusions**
In this lesson, we explored the **importance of cryptography** and the key **problems** it addresses. We also introduced the concepts of **symmetric** and **asymmetric encryption** and provided an overview of the fundamental **XOR** and **modulo operations** used in **cryptographic algorithms**.

### **What I Learned**
- **Importance of Cryptography**: Ensures **secure communication**, **data confidentiality**, **integrity**, and **authenticity**.
- **Symmetric Encryption**: Uses a single **secret key** for both **encryption** and **decryption**.
- **Asymmetric Encryption**: Uses a **public-private key pair** for **secure communication** without sharing a **secret key**.
- **Mathematical Operations**: **XOR** and **modulo** are fundamental **operations** used in **cryptographic algorithms**.
