# Public Key Cryptography Basics

## Task 1 - Introduction
In everyday life, we naturally ensure that our conversations are **private**, **authentic**, and **untampered**. We confirm who we are talking to, verify the source of information, and ensure no one can alter it. In the digital world, similar challenges exist when exchanging information online. **Public key cryptography** (**asymmetric cryptography**) provides **authentication**, **authenticity**, **integrity**, and **confidentiality**, enabling secure communication across networks and ensuring information reaches the intended recipients safely.

## Task 2 - Common Use of Asymmetric Encryption
Exchanging keys for **symmetric encryption** is a common use of **asymmetric cryptography**. Since **asymmetric encryption** is relatively slow compared to **symmetric encryption**, it is mainly used to negotiate and agree on **symmetric encryption ciphers** and **keys**.

### Analogy (Lock and Secret Code)
Imagine you have a **secret code** for communicating and instructions for using it. How can you send these instructions to a friend without anyone else reading them? The solution is simple: ask your friend for a **lock**. Only your friend has the **key** for this **lock**, and you have an indestructible box to secure it.

If you send the instructions in the locked box, your friend can unlock it and read them. After that, you can communicate using the **secret code** without the risk of eavesdropping.

| Analogy | Cryptographic System |
| ------- | -------------------- |
| Secret Code | **Symmetric Encryption Cipher and Key** |
| Lock | **Public Key** |
| Lock’s Key | **Private Key** |

## Task 3 - RSA (Rivest–Shamir–Adleman)
### RSA (Public-Key Encryption)
**RSA** is a **public-key encryption algorithm** that enables secure **data transmission** over insecure channels, where adversaries may attempt to eavesdrop.
#### The Math Behind RSA Security
**RSA**’s security relies on the difficulty of factoring large **numbers**. While multiplying two large **prime numbers** is straightforward, finding their factors is computationally hard.
#### Example
- Multiplying small **primes**: 113 × 127 = 14351
- For larger **primes**: 982451653031 × 169743212279 = 166764499494295486767649

It is easy to multiply two huge **primes**, but very hard to factor their product, especially when **primes** are hundreds of digits long. Modern computers can factor small **numbers** like 166764499494295486767649, but **numbers** with 600+ digits are practically impossible to factor.
### RSA Encryption and Decryption
In **asymmetric encryption**, the **public key** is shared with everyone and used for **encryption**, while the **private key** is kept **secret** and used for **decryption**.

#### Example
- Alice wants to send a **message** to Bob.
- Alice encrypts the **message** with Bob’s **public key**, and Bob decrypts it using his **private key**.

### RSA Example

1. Bob chooses two **prime numbers**: p = 17 and q = 11 → multiplies them to get n = 187.
2. Bob calculates a number related to p and q (φ) = 160.
3. Bob picks a small number e = 7 for the **public key**.
4. Bob calculates d = 23 for the **private key**.
#### Encryption
- Alice wants to send x = 13.
- She uses Bob’s **public key** to transform the **message** into y = 62.
#### Decryption
- Bob uses his **private key** to transform y = 62 back into the original **message** x = 13.

The **message** is securely transmitted, and no one else can read it.

## Task 4 - Diffie-Hellman Key Exchange
One challenge of **symmetric encryption** is sharing the **secret key** securely. **Diffie-Hellman** allows two parties to establish a shared **secret key** over an insecure channel without anyone else being able to discover it. This shared **key** can then be used for **symmetric encryption**.
### Conceptually
- Alice and Bob each pick a **private number** (A and B).
- They combine their **private numbers** with some **public shared material** (C) and exchange the results.
- By combining the received value with their own **secret**, both end up with the same shared **key**.

### Real-World Example
1. **Public values**: prime number p = 29, generator g = 3.
2. **Private keys**: Alice a = 13, Bob b = 15.
3. **Public keys**: Alice: A = g^a mod p = 19, Bob: B = g^b mod p = 26
4. Exchange **public keys**: Alice receives B = 26, Bob receives A = 19.
5. Compute shared **secret**: Alice: B^a mod p = 10, Bob: A^b mod p = 10

## Task 5 - SSH
### Authenticating the Server
When connecting to a server using **SSH** for the first time, the client asks you to verify the server’s **public key fingerprint**. This step ensures that you are connecting to the real server and not a malicious one performing a **man-in-the-middle attack**. Once accepted, the server’s **public key** is stored and automatically trusted in future connections unless it changes.
### Authenticating the Client
After verifying the server, the server must authenticate you. While **SSH** can use passwords, this is discouraged due to security risks. A more secure method is **SSH key-based authentication**, which uses a **public–private key pair** to prove your **identity** without sending passwords over the network.

### SSH Key Pairs
**SSH keys** consist of:
- A **private key** (kept secret on your machine)
- A **public key** (copied to the server)

### Protecting Private Keys
**Private SSH keys** must be treated like passwords:
- Never share them
- Use a strong **passphrase**
- Set strict file **permissions** (readable only by the owner)

## Task 6 - Digital Signatures and Certificates
In the analogue world, we sign papers to confirm **identity**, approve transactions, or acknowledge documents. In the digital world, signatures are replaced by **digital signatures**, which verify the **authenticity** and **integrity** of a **message** or **document**.
### Certificates
**Certificates** are a key application of **public key cryptography** and are widely used in **HTTPS**. They confirm a website’s **authenticity** through a **chain of trust**, starting from trusted root **CAs**.
### Obtaining Certificates
**Certificates** can be acquired from **certificate authorities** or free services like **Let’s Encrypt** to enable **secure HTTPS connections** on your website.

## Task 7 - PGP and GPG
**PGP** (Pretty Good Privacy) is software for **encrypting files**, performing **digital signing**, and more. **GnuPG (GPG)** is an open-source implementation of the OpenPGP standard.
### Uses of GPG
- **Encrypt emails** to protect **confidentiality**.
- **Sign emails** to verify **authenticity** and **integrity**.

### Generating a GPG Key
Use the following command:
```
gpg --full-gen-key
```
### Practical Usage
- Share your **public key** with contacts to allow **encrypted communication**.
- **Private key** is used to **decrypt messages**.
- Protect the **private key** with a **passphrase**, similar to **SSH keys**.

## Task 8 - Conclusions
**Public key cryptography** secures communication using **asymmetric key pairs**, solving **key exchange** problems and ensuring **authentication, integrity, and confidentiality**. **RSA**, **Diffie-Hellman**, and **SSH keys** enable secure data exchange, while **digital signatures, certificates, and PGP/GPG** verify **identity** and protect **messages**.  

### What I Learned
- **Asymmetric encryption** uses **public-private keys** for secure communication.  
- **RSA** relies on factoring large numbers for security.  
- **Diffie-Hellman** enables shared secrets over insecure channels.  
- **SSH keys, digital signatures, and certificates** verify **identity** and **integrity**.  
- **PGP/GPG** encrypts and signs **messages** securely.
