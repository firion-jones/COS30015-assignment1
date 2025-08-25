# Authentication Attack Scenario Design - Dot Point Plan

## **Testing Scenario Overview**
**Objective:** Evaluate effectiveness of password spraying attacks using personalized password generation against various defensive measures

## **Environment Setup**
### **Virtual Lab Infrastructure**
- **Target System:** Ubuntu server with SSH and web application login
- **Attack Platform:** Kali Linux VM with custom tools
- **Network:** Host-only networking (isolated environment)
- **Monitoring:** Centralized logging server for detection analysis

### **Target Applications**
- **Primary:** Custom web application with login form
- **Secondary:** SSH service with username/password authentication
- **Database:** MySQL backend storing user credentials (hashed)

## **Phase 1: Synthetic Data Generation**
### **User Profile Database Creation**
- Generate **500 realistic user profiles** using Python Faker library
- **Data points per user:**
  - Full name (first, last)
  - Email address
  - Birth year/date
  - Pet names (1-2 per user)
  - Hobbies/interests
  - Favorite foods
  - Location/city
  - Company/job title
  - Previously gained password

### **Password Generation Algorithm**
- **Pattern-based password creation** using personal data
- **Common password patterns to implement:**
  - `{FirstName}{BirthYear}!` (e.g., Sarah1990!)
  - `{Pet}{Number}@` (e.g., Fluffy123@)
  - `{Hobby}{Year}` (e.g., Photography2024)
  - `{Location}{BirthYear}!` (e.g., Sydney1985!)
  - `{Company}@{Year}` (e.g., Microsoft@2024)
  - `{PreviousPassword}` (If available, used once, attributes can also be dissected and rearranged, (e.g., Candy*2000 could be dissected into `[Candy,$,2000]`))
- **Ensure compliance with password policy:** minimum 8 chars, uppercase, lowercase, number, special character

## **Phase 2: Attack Implementation (Offensive Tool)**
### **Custom Password Spraying Tool**
- **Language:** Python with requests/paramiko libraries
- **Features:**
  - Multi-protocol support (HTTP/SSH)
  - Configurable timing delays (avoid detection)
  - User-agent rotation and IP spoofing simulation
  - Success/failure logging with timestamps
  - Pattern effectiveness tracking

### **Attack Methodology**
- **Stage 1:** Username enumeration (if required)
- **Stage 2:** Single password against all users (classic spraying)
- **Stage 3:** Personalized passwords against specific users
- **Timing:** 1 attempt per user per 30 minutes (avoid lockouts)
- **Duration:** 48-hour attack simulation

## **Phase 3: Defensive Implementation**
### **Baseline Testing (No Defenses)**
- Document attack success rate without protection
- Establish baseline metrics for comparison

### **Defense Tool 1: fail2ban**
- **Configuration:**
  - SSH protection: 3 failures = 10 minute ban
  - HTTP protection: 5 failures = 15 minute ban
  - Custom rules for web application
- **Monitoring:** Ban events, IP addresses, timing

### **Defense Tool 2: Account Lockout Policies**
- **Application-level:** 5 failed attempts = 30 minute lockout
- **System-level:** PAM modules for SSH protection
- **Progressive delays:** Increasing wait times per failed attempt

### **Defense Tool 3: Enhanced Monitoring**
- **Log analysis:** Automated pattern detection
- **Alerting:** Real-time notifications for spray patterns
- **SIEM simulation:** Correlation rules for attack identification

## **Success Metrics Definition**

### **Attack Success Metrics (Offensive)**
- **Primary:** Successful authentication rate (logins/total attempts)
- **Secondary:** Time to first successful login
- **Pattern effectiveness:** Which personal data patterns yield highest success
- **Evasion rate:** Attacks completed without triggering defenses

### **Defense Success Metrics (Defensive)**
- **Primary:** Attack detection rate (alerts/actual attacks)
- **Secondary:** Time to detection (minutes from attack start)
- **False positive rate:** Legitimate users blocked
- **Containment effectiveness:** Attacks stopped vs completed

### **Overall Effectiveness Metrics**
- **Business impact:** Percentage of accounts compromised
- **Operational impact:** Legitimate user disruption
- **Detection accuracy:** True positives vs false positives

## **MITRE ATT&CK Framework Mapping**

### **Primary Techniques**
- **T1110.003 - Brute Force: Password Spraying**
  - Main attack vector implementation
- **T1589.001 - Gather Victim Identity Information: Credentials**
  - Personal data collection and analysis
- **T1078.004 - Valid Accounts: Cloud Accounts**
  - Successful authentication usage

### **Supporting Techniques**
- **T1201 - Password Policy Discovery**
  - Understanding target password requirements
- **T1087 - Account Discovery** 
  - Username enumeration activities
- **T1133 - External Remote Services**
  - SSH/web service targeting

## **Testing Timeline**
### **Week 1:** Environment setup and data generation
### **Week 2:** Attack tool development and testing
### **Week 3:** Baseline attack execution (no defenses)
### **Week 4:** Defense implementation and protected testing
### **Week 5:** Analysis, comparison, and documentation

## **Expected Outcomes**
### **Attack Tool Analysis**
- Personalized passwords significantly more effective than generic wordlists
- Lower detection rates with slow, targeted approach
- Pattern effectiveness varies by demographic correlation

### **Defense Tool Analysis**
- fail2ban effective against rapid attacks, less effective against slow spraying
- Account lockouts protect individual accounts but may cause DoS
- Combined defenses provide layered protection with acceptable false positive rates

### **Scenario Winner Determination**
- **Attacker wins:** >10% successful authentication rate
- **Defender wins:** <2% successful authentication rate + >90% detection rate
- **Balanced outcome:** 2-10% success rate with high detection