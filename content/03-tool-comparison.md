<!-- Write something here introducing the concept of this section of the report -->

# Overview of Attacker Tools

This section examines four prominent authentication attack tools to understand their capabilities, limitations, and practical applications in cybersecurity research. The analysis evaluates both offline password recovery tools (Hashcat, John the Ripper) and online network-based attack tools (Hydra, NetExec), providing a comprehensive overview of the current authentication threat landscape. By comparing these tools across different attack methodologies—from hash cracking to live network authentication testing—this research establishes the foundation for selecting the most appropriate tool for subsequent defensive analysis and laboratoryd

## Comparison Table

```{=latex}
\input{content/tables/attack-tools-comparison.tex}
```

## Hashcat

Hashcat is a specialized tool for password-based attacks, focusing on scenarios where the attacker has access to known hash or encrypted data and aims to recover the original password or passphrase. It employs brute force, dictionary, and hybrid attack methods to achieve this goal. Hashcat excels at cracking password hashes across more than 450 supported algorithms[@hashcat], recovering passwords for encrypted file formats, and deciphering offline authentication tokens.

Hashcat is limited to offline password recovery and cannot break mathematically sound encryption without access to passwords, attack live network services, or exploit flaws in cryptographic implementations. Its strengths lie in unmatched password recovery capabilities, broad algorithm support, and GPU-accelerated performance, making it a specialized tool for cracking password hashes and encrypted files rather than attacking network protocols or cryptographic weaknesses.

Rather than replacing network-based tools such as Hydra. Hashcat focuses on offline attacks against captured password hashes or encrypted files, while Hydra targets live authentication services by attempting to guess credentials in real time. Hashcat operates independently of network access, working in the dark to recover passwords from stored data. Once successful, the recovered credentials can be used to access systems without further brute force attempts.

<!-- ### Strengths and Weaknesses

  **Strengths:**

  - Unmatched password recovery capabilities
  - Supports 450+ password hash algorithms
  - GPU-accelerated performance for rapid attacks
  - Effective for encrypted file formats and offline authentication tokens

  **Limitations:**

  - Requires access to password-protected material (hashes, encrypted files)
  - Cannot break mathematically sound encryption without passwords
  - Not suitable for attacking live network services
  - Does not exploit cryptographic implementation flaws -->

### Use Cases

- Cracking password hashes extracted from sources such as Windows "Ntds.dit" or "SAM" files, Linux "/etc/shadow", or other stored hash values supported by Hashcat's extensive algorithm coverage.
- Recovering lost passwords for encrypted files or authentication tokens

<!-- -------------------------------------------------------------------------------------------- -->

## Hydra

Hydra is a versatile tool for conducting password-based attacks against live network services. Unlike Hashcat, which focuses on offline password recovery from hashes or encrypted files, Hydra targets active authentication endpoints by systematically testing username and password combinations in real time. It supports more than 50 protocols, including web services (HTTP, HTTPS), remote access (SSH, Telnet, RDP), file sharing (FTP, SMB), databases (MySQL, PostgreSQL), and email (IMAP, SMTP)[@hydra]. Hydra is commonly used for brute force, password spraying, and credential stuffing attacks, providing immediate feedback on successful logins.

For this research, Hydra was chosen over Medusa[@medusa] due to Medusa's lack of recent git commits and lower comparative popularity on GitHub, indicating less active development and community support. Medusa offers functionality comparable to Hydra, with a modular architecture that enables consistent command usage across various protocols. However, its lower popularity and less active development made it a secondary choice for this research.

<!-- ### Strengths and Weaknesses

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
- Requires network connectivity to the target -->

### Use Cases

- Testing the strength of passwords for web applications, remote access, and file sharing services
- Simulating password spraying attacks to evaluate organizational defenses
- Assessing exposure to credential stuffing

<!-- -------------------------------------------------------------------------------------------- -->

## John the Ripper

John the Ripper is a foundational password cracking and security auditing tool that established many baseline techniques in the field. As the "original" password cracker[@johntheripper], it operates primarily through offline hash cracking similar to Hashcat, while also offering limited online attack capabilities. John the Ripper exists in two main variants: the classic mode with traditional password cracking algorithms, and the community-enhanced "Jumbo" version that supports over 200 hash formats including Unix/Linux systems, Windows environments, applications, databases, and cryptocurrency wallets[@keychainx2021bitcoin].

John the Ripper distinguishes itself through its sophisticated rule engine for password transformations and unique "single mode" that leverages account information to generate targeted password candidates. While it shares offline hash cracking capabilities with Hashcat, John the Ripper's historical significance and educational value make it valuable for understanding classical password cracking techniques, though it operates at significantly slower speeds on modern GPU hardware.

<!-- ### Strengths and Weaknesses

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
- Limited online attack capabilities compared to dedicated network tools -->

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

<!-- ### Strengths and Weaknesses

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
- Dependent on network connectivity and target system availability -->

### Use Cases

- Enterprise Active Directory assessment for automating credential validation and security posture evaluation across large Windows networks
- Post-compromise lateral movement through advanced credential attacks including pass-the-hash and Kerberos abuse
- Comprehensive domain security validation including delegation detection and Certificate Services enumeration
- Automated BloodHound data collection for attack path visualization and privilege escalation planning

---

## Attack Tool Selection and Summary

After evaluating the four authentication attack tools, **Hydra** emerged as the most suitable choice for this research assignment. This selection was critical to establish before proceeding to defensive tool analysis, as it provides the foundation for understanding what threats need to be mitigated.

**Hydra** offers the ideal balance of capabilities for this assignment's scope. Its support for over 50 network protocols, real-time authentication testing, and immediate feedback mechanisms make it particularly valuable for understanding live network attack scenarios. The tool's ability to perform brute force, password spraying, and credential stuffing attacks directly aligns with the authentication threat landscape identified in the threat analysis section.

<!-- **NetExec** presented fascinating capabilities, particularly its comprehensive Active Directory assessment features and BloodHound integration. However, its scope proved too extensive for this assignment's constraints, encompassing post-exploitation lateral movement and enterprise-wide network reconnaissance that extends beyond focused authentication testing. While an extremely powerful tool for real-world penetration testing, its complexity would have diluted the research focus.

**Hashcat** demonstrated impressive technical capabilities with its 450+ algorithm support and GPU acceleration. Despite being a foundational tool in password recovery, it lacked the network-based attack vectors I sought to explore in this assignment. Its offline nature, while valuable for hash cracking scenarios, doesn't provide the interactive network authentication testing central to this research.

**John the Ripper**, while historically significant as the original password cracker, unfortunately appeared outdated compared to modern alternatives like Hashcat. Though it retains educational value and offers unique features like its sophisticated rule engine, its slower performance and less active development made it a secondary choice for contemporary security research.

This tool selection process ensured that the subsequent defensive analysis would address the most relevant and practical authentication threats -->

# Overview of Defender Tools

## Comparison Table

```{=latex}
\input{content/tables/defender-tools-comparison.tex}
```

<!-- -------------------------------------------------------------------------------------------- -->

\newpage
## Fail2ban

Fail2ban is a UNIX based system (sorry windows), that operates by scanning log files and systemd journals using specified regular expressions (filter-rules) to detect authentication failures and other suspicious activities[@fail2ban_wiki_howitworks]. When failures exceed configured thresholds, fail2ban executes actions to ban the offending sources, typically by updating system firewall rules to reject new connections from those IP addresses for a configurable duration. The system operates through "jails" - configuration units that define which log files to monitor, what patterns constitute failures, and how many attempts within a specified time window trigger bans.

Fail2ban comes pre-configured to monitor standard log files for services like SSH and Apache, but can be easily customized to read any log file and detect any error pattern. 


<!-- ### Strengths and Weaknesses

**Strengths:**

- Automated real-time response eliminates manual monitoring requirements
- Lightweight operation with minimal system resource consumption
- Cross-protocol support covering Hydra's entire attack surface
- Highly configurable detection thresholds and response parameters
- Built-in integration with standard system logs and firewall mechanisms
- Open source, with good community documentation.
- Persistent ban tracking across service restarts and system reboots

**Limitations:**

- Reactive defense model requires attacks to begin before protection activates
- Vulnerable to distributed attacks using multiple source IP addresses
- Risk of legitimate user lockouts through misconfigured thresholds or false positives
- Log-dependent detection misses network-level attack indicators
- Ineffective against slow, low-threshold attacks designed to evade detection
- Limited threat intelligence integration for proactive source blocking
- Potential for bypass through IP rotation or proxy-based attacks
- Does not have native Windows support -->

### Hydra Defense

Fail2ban could effectively counter Hydra's authentication attacks by monitoring system logs for failed login patterns and automatically blocking source IP addresses after exceeding configured thresholds. When Hydra conducts brute force or password spraying attacks against SSH, HTTP forms, FTP, or other services, fail2ban detects the repeated authentication failures and implements immediate firewall blocks that terminate the attack session. 
<!-- -------------------------------------------------------------------------------------------- -->


## Wazuh

Wazuh is a free and open-source platform that unifies XDR (Extended Detection and Response) and SIEM (Security Information and Event Management) capabilities for protecting workloads across on-premises, virtualized, containerized, and cloud-based environments[@wazuh]. 

Wazuh's centralized architecture enables enterprise-wide correlation of security events, detecting coordinated attacks that may be missed by isolated systems. By integrating MITRE ATT&CK mapping and threat intelligence, Wazuh identifies complex attack patterns through behavioral analysis and cross-system event relationships. Detected threats trigger automated responses such as firewall updates, security alerts, compliance reporting and other various sets of functionality.

<!-- ### Strengths and Weaknesses

**Strengths**

- Unified XDR and SIEM capabilities with no licensing costs
- Centralized monitoring and correlation across distributed environments
- Comprehensive security coverage including threat detection, compliance, and incident response
- Open-source platform with active community development
- Scalable architecture supporting enterprise-level deployments
- Integration capabilities with cloud platforms and security tools
- Behavioral analysis and threat intelligence integration

**Limitations**

- Complex deployment and configuration requirements
- Significant resource consumption for central processing infrastructure
- Steep learning curve for effective implementation and tuning (They sell 3 day tutorial sessions for $1800)
- Potential for alert overload without proper configuration
- Dependency on network connectivity and agent deployment
- Performance considerations with large-scale log processing
- Limited real-time blocking compared to dedicated prevention tools -->


### Hydra Defense
Wazuh can help defend against Hydra’s authentication attacks by monitoring security events from many systems at once. This means it can spot brute force attacks that use multiple computers to avoid detection. Wazuh looks for patterns like repeated failed logins or attempts to guess passwords quickly. When it finds suspicious activity, it can automatically alert security staff, block the attacker’s access, or record the incident for review.
<!-- -------------------------------------------------------------------------------------------- -->


## pfSense
pfSense is a FreeBSD-based open-source firewall and router platform designed for network perimeter security[@pfsense]. Acting as a gateway, it proactively filters traffic and blocks threats before they reach internal systems. With integrated threat intelligence, geographic IP filtering, and reputation databases, pfSense can preemptively block known malicious sources. Its connection rate limiting and automated rule enforcement help prevent brute force and high-volume attacks at the network boundary, providing organization-wide protection through real-time traffic analysis.

<!-- ### Strengths and Weaknesses

**Strengths**

- Open-source platform with no licensing costs and active community development
- Network perimeter positioning providing organization-wide protection before attacks reach internal systems
- Geographic and reputation-based IP blocking through threat intelligence integration
- Comprehensive network services combining firewall, VPN, routing, and monitoring capabilities
- Real-time traffic analysis and logging for forensic investigation and compliance reporting

**Limitations**

- Network perimeter focus limits visibility into internal threats and application-layer authentication details
- Requires dedicated hardware or virtual machine resources, increasing infrastructure costs
- Advanced configuration and management demand significant networking expertise
- Geographic IP blocking may inadvertently affect legitimate users using VPNs or traveling
- Performance bottlenecks can occur on lower-spec hardware when handling high traffic volumes -->

### Hydra Defense

pfSense can help protect against Hydra attacks by blocking traffic from suspicious locations and known bad IP addresses before it reaches your network. Its ability to limit the number of connection attempts and automatically block sources that try to log in too quickly makes it effective at stopping brute force attacks.

<!-- -------------------------------------------------------------------------------------------- -->


## Suricata

Suricata is a network security tool that inspects data packets in real time to detect threats and suspicious activity. It uses predefined rules and signatures to spot attacks, unusual protocol behavior, and malicious content as traffic passes through the network. Suricata can work passively to monitor and log network activity for later analysis, or actively block threats when deployed inline. Its focus on analyzing network traffic at the packet level allows for quick detection and detailed investigation of attacks that may not show up in standard system logs.

<!-- ### Strengths and Weaknesses

**Strengths**

- Deep packet inspection for detailed network protocol and content analysis
- Supports both passive IDS monitoring and active IPS prevention
- High-performance processing for multi-gigabit traffic loads
- Real-time threat detection with rapid response to network attacks
- Integration with SIEM platforms and threat intelligence feeds

**Limitations**

- Requires specialized expertise for deployment and rule tuning
- High resource usage for deep packet inspection can impact performance
- Needs frequent rule updates to stay effective against new threats
- Limited visibility into encrypted traffic
- Potential for false positives without careful configuration -->

### Hydra Defense

Suricata could potentially detect Hydra attacks through deep packet inspection that identifies rapid TCP connection sequences and systematic authentication patterns characteristic of automated credential testing tools. When deployed in IPS mode, the platform might actively block detected attack traffic in real-time, though effectiveness could be limited against encrypted authentication protocols and distributed attacks that blend with legitimate network traffic.


## Defender Tool Selection and Summary

**Fail2ban** was selected as the defensive tool for this assignment because it provides simple, automated protection against brute force authentication attacks like those performed by Hydra. It is lightweight, easy to configure, and works directly with standard Linux logs, making it ideal for small business or single-server environments. Unlike more complex or resource-intensive solutions, Fail2ban offers effective real-time blocking without requiring advanced expertise or additional hardware.

\newpage