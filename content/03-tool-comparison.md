# Tool Comparison

<!-- Write something here introducing the concept of this section of the report -->

## Overview of Attacker Tools

This section examines four prominent authentication attack tools to understand their capabilities, limitations, and practical applications in cybersecurity research. The analysis evaluates both offline password recovery tools (Hashcat, John the Ripper) and online network-based attack tools (Hydra, NetExec), providing a comprehensive overview of the current authentication threat landscape. By comparing these tools across different attack methodologies—from hash cracking to live network authentication testing—this research establishes the foundation for selecting the most appropriate tool for subsequent defensive analysis and laboratoryd

## Comparison Table

```{=latex}
\input{content/tables/attack-tools-comparison.tex}
```

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

## Hydra

Hydra is a versatile tool for conducting password-based attacks against live network services. Unlike Hashcat, which focuses on offline password recovery from hashes or encrypted files, Hydra targets active authentication endpoints by systematically testing username and password combinations in real time. It supports more than 50 protocols, including web services (HTTP, HTTPS), remote access (SSH, Telnet, RDP), file sharing (FTP, SMB), databases (MySQL, PostgreSQL), and email (IMAP, SMTP)[@hydra]. Hydra is commonly used for brute force, password spraying, and credential stuffing attacks, providing immediate feedback on successful logins.

For this research, Hydra was chosen over Medusa[@medusa] due to Medusa's lack of recent git commits and lower comparative popularity on GitHub, indicating less active development and community support. Medusa offers functionality comparable to Hydra, with a modular architecture that enables consistent command usage across various protocols. However, its lower popularity and less active development made it a secondary choice for this research.

### Strengths and Weaknesses

**Strengths:**

- Directly tests live authentication systems
- Supports a wide range of network protocols
- No need for hash extraction
- Immediate identification of valid credentials
- Flexible attack modes (brute force, spraying, credential stuffing)
- Custom wordlist and username/password combinations

**Limitations:**

- Generates network traffic that can be detected and logged
- May trigger account lockout or security alerts
- Network speed and server response time can affect performance
- Cannot bypass multi-factor authentication or modern protocols (OAuth, SAML)
- Requires network connectivity to the target

### Use Cases

- Testing the strength of passwords for web applications, remote access, and file sharing services
- Simulating password spraying attacks to evaluate organizational defenses
- Assessing exposure to credential stuffing

<!-- -------------------------------------------------------------------------------------------- -->

## John the Ripper

John the Ripper is a foundational password cracking and security auditing tool that established many baseline techniques in the field. As the "original" password cracker[@johntheripper], it operates primarily through offline hash cracking similar to Hashcat, while also offering limited online attack capabilities. John the Ripper exists in two main variants: the classic mode with traditional password cracking algorithms, and the community-enhanced "Jumbo" version that supports over 200 hash formats including Unix/Linux systems, Windows environments, applications, databases, and cryptocurrency wallets[@keychainx2021bitcoin].

John the Ripper distinguishes itself through its sophisticated rule engine for password transformations and unique "single mode" that leverages account information to generate targeted password candidates. While it shares offline hash cracking capabilities with Hashcat, John the Ripper's historical significance and educational value make it valuable for understanding classical password cracking techniques, though it operates at significantly slower speeds on modern GPU hardware.

### Strengths and Weaknesses

**Strengths:**

- Historical significance with established algorithms and techniques
- Sophisticated rule engine for password transformation
- Unique single mode using account information for targeted attacks
- Broad compatibility with older and limited hardware
- Educational value with well-documented classical algorithms
- Dual architecture supporting both classic and enhanced modes

**Limitations:**

- Significantly slower GPU performance compared to Hashcat
- Slower development pace and update cycle
- More complex configuration than modern tools
- Less optimized memory efficiency for large-scale attacks
- Limited online attack capabilities compared to dedicated network tools

### Use Cases

- Educational environments for learning password cracking fundamentals
- Legacy system auditing where modern tools may not be compatible
- Specialized rule-based attacks leveraging account information
- Cryptocurrency wallet password recovery for older formats
- Cross-platform password auditing on resource-constrained systems

<!-- -------------------------------------------------------------------------------------------- -->

## NetExec

NetExec is a network penetration testing tool designed to identify security vulnerabilities within enterprise networks by systematically testing credentials across multiple services and protocols. Operating under the philosophy that "you're only as strong as your weakest point," NetExec performs comprehensive credential validation across network infrastructure to locate authentication weaknesses[@netexec]. The tool primarily targets Windows-specific protocols commonly used in enterprise environments, making it particularly effective for Active Directory assessments and post-exploitation activities.

NetExec distinguishes itself from single-protocol tools like Hydra through its multi-protocol approach and specialized Windows/Active Directory focus. While Hydra targets individual services, NetExec provides a comprehensive network-wide assessment capability, automatically testing credentials against discovered services and integrating with tools like BloodHound for attack path visualization[@bloodhound]. This makes it valuable for both initial network reconnaissance and post-compromise lateral movement scenarios.

### Strengths and Weaknesses

**Strengths:**

- Supports multiple protocols (SMB, LDAP, WINRM, MSSQL, SSH, FTP, RDP, WMI, NFS)
- Integrated BloodHound support for network mapping and attack path visualization
- Automated credential validation across entire network infrastructure
- Specialized Windows/Active Directory enumeration capabilities
- Post-exploitation lateral movement through advanced credential attacks
- Support for pass-the-hash, Kerberos abuse, and LAPS integration

**Limitations:**

- Primarily Windows/Active Directory focused, limiting applicability to Linux-only environments
- Requires existing network access for post-exploitation activities
- May trigger security alerts due to multiple authentication attempts
- Cannot bypass multi-factor authentication or modern OAuth/SAML protocols
- Dependent on network connectivity and target system availability

### Use Cases

- Enterprise Active Directory assessment for automating credential validation and security posture evaluation across large Windows networks
- Post-compromise lateral movement through advanced credential attacks including pass-the-hash and Kerberos abuse
- Comprehensive domain security validation including delegation detection and Certificate Services enumeration
- Automated BloodHound data collection for attack path visualization and privilege escalation planning

## Attack Tool Selection and Summary

After evaluating the four authentication attack tools, **Hydra** emerged as the most suitable choice for this research assignment. This selection was critical to establish before proceeding to defensive tool analysis, as it provides the foundation for understanding what threats need to be mitigated.

**Hydra** offers the ideal balance of capabilities for this assignment's scope. Its support for over 50 network protocols, real-time authentication testing, and immediate feedback mechanisms make it particularly valuable for understanding live network attack scenarios. The tool's ability to perform brute force, password spraying, and credential stuffing attacks directly aligns with the authentication threat landscape identified in the threat analysis section.

**NetExec** presented fascinating capabilities, particularly its comprehensive Active Directory assessment features and BloodHound integration. However, its scope proved too extensive for this assignment's constraints, encompassing post-exploitation lateral movement and enterprise-wide network reconnaissance that extends beyond focused authentication testing. While an extremely powerful tool for real-world penetration testing, its complexity would have diluted the research focus.

**Hashcat** demonstrated impressive technical capabilities with its 450+ algorithm support and GPU acceleration. Despite being a foundational tool in password recovery, it lacked the network-based attack vectors I sought to explore in this assignment. Its offline nature, while valuable for hash cracking scenarios, doesn't provide the interactive network authentication testing central to this research.

**John the Ripper**, while historically significant as the original password cracker, unfortunately appeared outdated compared to modern alternatives like Hashcat. Though it retains educational value and offers unique features like its sophisticated rule engine, its slower performance and less active development made it a secondary choice for contemporary security research.

This tool selection process ensured that the subsequent defensive analysis would address the most relevant and practical authentication threats