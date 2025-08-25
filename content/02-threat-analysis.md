# Threat Analysis

## Authentication
According to the "Annual Cyber Threat Report 2023-2024", the most frequently reported threat in Australia were Authentication attacks in the form of "compromised accounts or credentials"[@acsc2024annual], accounting for nearly one-third of all cybercrime incidents nationwide. This prevalence underscores the critical importance of understanding and mitigating authentication-related threats in the current cybersecurity landscape.

Authentication breaches encompass a wide array of attack categories, each exploiting different weaknesses in user and system behavior. The most prominent include **phishing**, which leverages psychological manipulation to trick users into divulging credentials, and **brute force attacks**, where adversaries systematically guess passwords using automated tools. **Password spraying** represents a "low and slow" approach, targeting many accounts with common passwords to evade detection. **Credential stuffing** utilizes previously breached username-password pairs, often sourced from large-scale data leaks, to gain unauthorized access through automation. These categories highlight the multifaceted nature of authentication threats, demonstrating why password-based attacks remain a critical focus for security research and organizational defense.

## **Section 2: Authentication Threats Case Study** (~300 words)
**Purpose:** Deep analysis of the threat landscape  
**Subsections:**

### **2.1 Current Threat Landscape Background** (~100 words)
**Content:**
In July 2025, Qantas confirmed that 5.7 million customers were impacted in a cyberattack, demonstrating the ongoing threat to Australian organizations [@abc2025qantas_cyber].

- 2024-2025 statistics on authentication attacks
- Prevalence in recent breach reports
- Evolution of attack sophistication
- Industry sectors most affected

**Key Stats to Include:**
- 99% of identity attacks are password attacks (Microsoft)
- 88% of breaches involve stolen credentials (Verizon)
- Password reuse statistics

### **2.2 Typical Adversary Tradecraft** (~150 words)

**Purpose:** Technical analysis of attack methods

**Content:**

- **Brute Force:** Traditional systematic guessing, tools, detectability
- **Password Spraying:** "Low and slow" methodology, evasion techniques, recent examples
- **Credential Stuffing:** Leveraging breach data, automation, success factors
- **Attack Infrastructure:** Tools, botnets, scaling methods

**Technical Details:**

- Specific tools used (Hydra, Hashcat, etc.)
- Attack timing and patterns
- Evasion techniques

### **2.3 Organizational Impact** (~50 words)
**Content:**

The organizational impact of authentication breaches is starkly illustrated by the 2022 Optus incident, which exposed sensitive data of nearly 10 million Australians and triggered widespread concerns over identity theft and fraud [@abc2022optus_breach]. More recently, the Qantas breach in July 2025 affected 5.7 million customers, with varying degrees of personal information compromised [@abc2025qantas_cyber]. Both cases highlight the persistent threat posed by credential stuffing, where attackers leverage previously leaked credentials to infiltrate systems at scale. The consequences include substantial financial losses, operational disruption, and enduring reputational harm, emphasizing the critical need for organizations to strengthen authentication controls and proactively address credential-based threats.
  
- Financial costs (cite specific figures)
- Operational disruption
- Detection and containment timelines
- Reputation and compliance implications

**Rubric Alignment:** Addresses "typical adversary trade craft, the potential impact for an organisation"

---

## **Section 3: Threat Choice Justification** (~150 words)

**Purpose:** Argumentative section explaining selection rationale

**Structure:**

### **3.1 Prevalence and Relevance** (~50 words)

- Current threat statistics
- Real-world case studies from 2024
- Universal applicability across organizations

### **3.2 Technical Analysis Opportunities** (~50 words)

- Multiple attack vectors to examine
- Rich tool ecosystem for analysis
- Clear success/failure metrics
- Laboratory feasibility

### **3.3 Framework Integration Potential** (~50 words)

- Strong MITRE ATT&CK mapping (T1110 family)
- Essential 8 mitigation alignment
- Comprehensive defensive strategies available

**Rubric Alignment:** Addresses "Justify your threat choice" and demonstrates "consultation of the landscape and relatedness to modern challenges"

---

## **Section 4: Research Foundation** (~50 words)
**Purpose:** Bridge to tool selection phase
**Content:**
- Summary of research methodology
- Key sources consulted
- Transition statement to tool comparison phase

**Rubric Alignment:** Shows "consultation of the landscape" through reference quality

---

## **Structural Notes:**

### **Writing Style Requirements:**
- Academic tone with IEEE citations
- Avoid bullet points (use prose paragraphs)
- Bold key statistics for scannability
- Logical flow between sections

### **Citation Strategy:**
- **15-20 sources minimum** (IEEE format)
- **Primary sources preferred:** Verizon DBIR, Microsoft reports, IBM studies
- **Current data:** 2024-2025 reports and statistics
- **Mix of:** Industry reports, academic sources, case studies

### **Connection Points:**
- **Forward Links:** Sets up tool selection criteria
- **Backward Links:** References assignment objectives
- **Framework Prep:** Establishes MITRE/Essential 8 foundation

### **Assessment Criteria Focus:**
This structure targets **Criteria 1: Planning and Justification** specifically:
- Case study provided
- Justification with examples  
- Landscape consultation through reference
- Modern challenges and relevance addressed
- Foundation for TTPs and metrics

---

## **Quality Checkpoints:**

### **Before Writing:**
- [ ] All sections have clear purpose
- [ ] Word count targets realistic
- [ ] Rubric requirements mapped
- [ ] Citation sources identified

### **During Writing:**
- [ ] Each paragraph advances the argument
- [ ] Statistics properly cited
- [ ] Technical depth appropriate
- [ ] Flow between sections logical

### **After Writing:**
- [ ] Word count within target (~500)
- [ ] All citations in IEEE format
- [ ] No bullet points or lists used
- [ ] Sets up tool selection phase effectively