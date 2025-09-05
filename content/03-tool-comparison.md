# Tool Comparison

<!-- Write something here introducing the concept of this section of the report -->

## Overview of Attacker Tools

<!-- Briefly discuss the tools that will be used and a dot point that summarises each tool -->

## Comparison Table

### Hashcat

#### Description

Hashcat is specifically designed for password-based attacks where:

Input: Known hash/encrypted data
Goal: Recover the password/passphrase
Method: Brute force, dictionary, or hybrid attacks

**Hashcat excels at:**

Password hash cracking (300+ algorithms)
Encrypted file format cracking (where password-protected)
Offline authentication token cracking

**Hashcat cannot do:**

Break mathematically sound encryption without passwords
Attack live network services
Exploit implementation flaws in cryptographic code

Research Implications for Your Assignment
This positioning shows hashcat's specific niche in cybersecurity:
Strengths:

Unmatched password recovery capabilities
Massive algorithm support for password-based schemes
GPU-accelerated performance

**Limitations:**

Requires pre-existing password-protected material
Cannot break properly implemented encryption
Offline-only attack tool

For your tool comparison, this means hashcat complements rather than replaces network-based tools like Hydra. While Hydra attacks live authentication services, hashcat attacks captured password hashes or encrypted files offline.

#### Strengths and Weaknesses

**Strengths:**
- Unmatched password recovery capabilities
- Massive algorithm support for password-based schemes
- GPU-accelerated performance

**Limitations:**
- Requires pre-existing password-protected material
- Cannot break properly implemented encryption
- Offline-only attack tool
- Public Key Cryptanalysis
  - RSA
  - Discrete logarithm
  - elliptic curve
- Symmetric encryption
- Post quantum
- blockchain


#### Use Cases

- Password hashes can be cloned from using a shadow copy of the "Ntds.dit" file. https://blog.netwrix.com/2021/11/30/extracting-password-hashes-from-the-ntds-dit-file/ OR C:\Windows\System32\config\SAM for local users https://www.lsoft.net/posts/what-is-a-sam-file/ OR `/etc/shadow` on linux systems OR any other stored hash values. 
- Regaining lost passwords

<!-- -------------------------------------------------------------------------------------------- -->

### Hydra

#### Description

#### Strengths and Weaknesses

#### Use Cases

<!-- -------------------------------------------------------------------------------------------- -->

### John the Ripper

#### Description

#### Strengths and Weaknesses

#### Use Cases

<!-- -------------------------------------------------------------------------------------------- -->

### Medusa

#### Description

#### Strengths and Weaknesses

#### Use Cases

<!-- -------------------------------------------------------------------------------------------- -->

### Ncrack

#### Description

#### Strengths and Weaknesses

#### Use Cases

<!-- -------------------------------------------------------------------------------------------- -->
