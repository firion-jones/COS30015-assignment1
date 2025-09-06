# Tool Comparison

<!-- Write something here introducing the concept of this section of the report -->

## Overview of Attacker Tools

<!-- Briefly discuss the tools that will be used and a dot point that summarises each tool -->

## Comparison Table

## Hashcat

Hashcat is a specialized tool for password-based attacks, focusing on scenarios where the attacker has access to known hash or encrypted data and aims to recover the original password or passphrase. It employs brute force, dictionary, and hybrid attack methods to achieve this goal. Hashcat excels at cracking password hashes across more than 450 supported algorithms[@hashcat], recovering passwords for encrypted file formats, and deciphering offline authentication tokens.

Hashcat is limited to offline password recovery and cannot break mathematically sound encryption without access to passwords, attack live network services, or exploit flaws in cryptographic implementations. Its strengths lie in unmatched password recovery capabilities, broad algorithm support, and GPU-accelerated performance, making it a specialized tool for cracking password hashes and encrypted files rather than attacking network protocols or cryptographic weaknesses.

Rather than replacing network-based tools such as Hydra. Hashcat focuses on offline attacks against captured password hashes or encrypted files, while Hydra targets live authentication services by attempting to guess credentials in real time. Hashcat operates independently of network access, working in the dark to recover passwords from stored data. Once successful, the recovered credentials can be used to access systems without further brute force attempts.

### Strengths and Weaknesses

  **Strengths:**

  - Unmatched password recovery capabilities
  - Supports 450+ password hash algorithms
  - GPU-accelerated performance for rapid attacks
  - Effective for encrypted file formats and offline authentication tokens

  **Limitations:**

  - Requires access to password-protected material (hashes, encrypted files)
  - Cannot break mathematically sound encryption without passwords
  - Not suitable for attacking live network services
  - Does not exploit cryptographic implementation flaws

### Use Cases

- Cracking password hashes extracted from sources such as Windows "Ntds.dit" or "SAM" files, Linux "/etc/shadow", or other stored hash values supported by Hashcat's extensive algorithm coverage.
- Recovering lost passwords for encrypted files or authentication tokens


<!-- -------------------------------------------------------------------------------------------- -->

### Hydra

#### Description
Primary Function: Network-based password brute force and spraying tool
Attack Type: Live authentication attacks against network services
Approach: Online credential testing (vs Hashcat's offline hash cracking)
Core Capabilities
Protocol Support (50+ protocols):

Web Services: HTTP(S), HTTP-POST, HTTP-GET forms
Remote Access: SSH, Telnet, RDP, VNC
File Services: FTP, SFTP, SMB/CIFS
Database: MySQL, PostgreSQL, MSSQL, Oracle
Email: IMAP, POP3, SMTP
Network: SNMP, LDAP, Cisco protocols
And many more...

Attack Modes:

Single password against multiple users
Multiple passwords against single user
Password spraying (low and slow)
Credential stuffing with username:password lists
Custom username/password combinations

#### Strengths and Weaknesses

  **Strengths:**

Tests live authentication systems directly
Works against any network service
No hash extraction required
Immediate feedback on successful credentials
Can test multiple services simultaneously

Personalized Attack Integration:

Custom wordlist support perfect for your synthetic profiles
Flexible username/password combination testing
Can incorporate personal data patterns effectively
Rate limiting allows realistic password spraying

Versatility:

50+ protocol support covers most authentication scenarios
HTTP form attacks for modern web applications
Database and network service testing
Proxy and anonymization support

  **Limitations:**

Detection and Blocking:

Generates network traffic (easily logged/detected)
Account lockout policies can halt attacks
Rate limiting required to avoid detection
Firewall/IPS systems may block repeated attempts

Performance Constraints:

Network latency affects speed
Server response time limitations
Connection limits from target systems
Account lockout policies force slow attacks

Technical Limitations:

Cannot bypass multi-factor authentication
Limited against modern authentication (OAuth, SAML)
Requires network connectivity to target
May trigger security alerts/responses

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
