# Threat Analysis

## Authentication

According to the Annual Cyber Threat Report(ACTR) 2023-2024, the most frequently reported threat in Australia were Authentication attacks in the form of "compromised accounts or credentials"[@acsc2024annual], accounting for nearly one-third of all cybercrime incidents nationwide. This prevalence underscores the critical importance of understanding and mitigating authentication-related threats in the current cybersecurity landscape.

Authentication breaches encompass a wide array of attack categories, each exploiting different weaknesses in user and system behavior. The most prominent include **phishing**, which leverages psychological manipulation to trick users into divulging credentials, and **brute force attacks**, where adversaries systematically guess passwords using automated tools. **Password spraying** represents a "low and slow" approach, targeting many accounts with common passwords to evade detection. **Credential stuffing** utilizes previously breached username-password pairs, often sourced from large-scale data leaks, to gain unauthorized access through automation. These categories highlight the multifaceted nature of authentication threats, demonstrating why password-based attacks remain a critical focus for security research and organizational defense.

## Threats in the Authentication Landscape

### Current Threat Landscape

Authentication threats represent a critical challenge in today’s cybersecurity landscape, both in Australia and globally. The Albanese Government’s commitment of $15–$20 billion through 2033–34 to strengthen cyber domain capabilities underscores the national urgency to address these issues[@acsc2024annual]. In the 2023–24 financial year, the Australian Signals Directorate received over 36,700 calls to its Cyber Security Hotline 12% increase from the previous year, reflecting the growing prevalence of cyber incidents[@acsc2024annual]. Notably, compromised accounts or credentials accounted for **32% of all cybercrime**, making it the leading contributor to reported incidents. On a global scale, Microsoft Entra data reveals that of more than **600 million identity attacks per day**, over **99% are password-based**[@microsoft2024digital]. These statistics highlight the widespread and persistent nature of authentication-related threats, demonstrating why robust authentication mechanisms are essential for organizational and national security.

### Typical Adversary Types

Authentication attacks are executed through several distinct methods, each exploiting specific vulnerabilities in user behavior and system design.

- **Phishing** is a psychological manipulation technique where adversaries impersonate trusted entities, often via email or messaging platforms, to deceive users into revealing their credentials. This method remains highly effective due to its reliance on social engineering rather than technical flaws.

- **Brute force attacks** involve systematically generating and attempting password combinations until a valid login is achieved. Attackers leverage automated tools to accelerate this process, targeting accounts with weak or commonly used passwords.

- **Password spraying** refines brute force tactics by distributing login attempts across many accounts using a shortlist of popular passwords, thereby evading detection mechanisms that monitor for rapid, repeated failures. A notable example is the 2024 Midnight Blizzard incident, where attackers employed password spraying against Microsoft’s infrastructure, prompting significant defensive actions[@microsoft2024midnight_blizzard_blog].

- **Credential stuffing** utilizes credentials harvested from previous data breaches, exploiting the widespread practice of password reuse across multiple services. The 2022 Optus breach illustrated the impact of this technique, as compromised credentials were repurposed to target other organizations[@abc2022optus_breach]. These methods collectively demonstrate the evolving sophistication and persistence of authentication threats in the modern cyber landscape.

### Impact

This section starts with how phishing and credential stuffing can be used as good starts

<!-- Breifly discuss the impact phishing attacks can have on a personal and organisation level. -->

The organizational impact of authentication breaches is starkly illustrated by the 2022 Optus incident, which exposed sensitive data of nearly 10 million Australians and triggered widespread concerns over identity theft and fraud [@abc2022optus_breach]. More recently, the Qantas breach in July 2025 affected 5.7 million customers, with varying degrees of personal information compromised [@abc2025qantas_cyber]. Both cases highlight the persistent threat posed by credential stuffing, where attackers leverage previously leaked credentials to infiltrate systems at scale. The consequences include substantial financial losses, operational disruption, and enduring reputational harm, emphasizing the critical need for organizations to strengthen authentication controls and proactively address credential-based threats.

---


## Threat Choice Justification

The selection of authentication attacks as the focal threat for this analysis is driven by their overwhelming prevalence and critical impact on both Australian and global organizations. Recent reports indicate that compromised credentials account for nearly one-third of all cybercrime incidents in Australia, with high-profile breaches such as Optus and Qantas underscoring the real-world consequences of these attacks[@acsc2024annual;@abc2022optus_breach;@abc2025qantas_cyber]. The universal reliance on password-based authentication across industries makes this threat highly relevant and widely applicable. From a technical perspective, authentication attacks such as brute force, password spraying, and credential stuffing offer a rich landscape for analysis, enabling clear success and failure metrics and supporting laboratory-based experimentation. 

While phishing remains a significant aspect of authentication security due to its effectiveness and prevalence, it is not easily testable in a controlled lab environment and will not be the focus of practical testing in this assignment. Nevertheless, its role in the broader authentication threat landscape will be acknowledged. Furthermore, the threat aligns strongly with established frameworks like MITRE ATT&CK (T1110 family) and Essential 8 mitigations, providing a robust foundation for evaluating defensive strategies and mapping adversary techniques. 

This combination of prevalence, technical depth, and framework integration makes authentication attacks an ideal subject for comprehensive security analysis. It will also be interesting to see how easy it is to break into hypothetical systems and gain a practical understanding of how secure my own personal passwords really are.
