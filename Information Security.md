> Information Security (InfoSec) is the practice of protecting information and information systems from unauthorized access, use, disclosure, modification, destruction, or disruption.

## 1. Introduction to Information Security

Information is one of the most valuable assets of an individual or organization.

Examples include:

- Personal information
    
- Financial records
    
- Medical records
    
- Business documents
    
- Customer databases
    
- Login credentials
    
- Intellectual property
    

Information Security protects information regardless of whether it is stored digitally, printed on paper, or communicated verbally.

Its purpose is to ensure that information remains protected throughout its lifecycle.

## 2. Goals of Information Security

Information Security is commonly based on the CIA Triad.

### 2.1 Confidentiality

Confidentiality ensures that information is accessible only to authorized individuals.

Examples:

- Password-protecting confidential documents.
    
- Encrypting sensitive files.
    
- Restricting access to employee records.
    

### 2.2 Integrity

Integrity ensures that information remains accurate, complete, and protected from unauthorized modification.

Examples:

- Using file hashes to detect unexpected changes.
    
- Restricting database modification permissions.
    
- Maintaining audit logs.
    

### 2.3 Availability

Availability ensures that information and services remain accessible when required.

Examples:

- Maintaining backups.
    
- Using redundant systems.
    
- Protecting servers against denial-of-service attacks.
    

Related note: [[CIA Triad]]

## 3. Types of Information

### 3.1 Personal Information

Information that identifies or relates to an individual.

Examples:

- Name
    
- Email address
    
- Phone number
    
- Residential address
    

### 3.2 Sensitive Personal Information

Information requiring additional protection because unauthorized disclosure could cause significant harm.

Examples may include:

- Financial account details
    
- Medical records
    
- Authentication credentials
    
- Biometric information
    

The exact legal classification depends on applicable laws and regulations.

### 3.3 Business Information

Information used by organizations for their operations.

Examples:

- Business plans
    
- Employee records
    
- Financial reports
    
- Internal communications
    
- Customer information
    

### 3.4 Intellectual Property

Intellectual Property includes creations and information protected through applicable intellectual property rights.

Examples:

- Software source code
    
- Patents
    
- Copyrighted material
    
- Trade secrets
    
- Proprietary designs
    

## 4. Information Classification

Information classification means organizing information according to its sensitivity and the level of protection it requires.

A common classification model is:

|Classification|Description|Example|
|---|---|---|
|Public|Information intended for public access|Public website content|
|Internal|Information intended for organizational use|Internal announcements|
|Confidential|Information requiring restricted access|Customer records|
|Restricted|Highly sensitive information with strict access controls|Critical credentials or sensitive financial records|

Organizations may use different classification names and policies.

### Why Classification Matters

It helps organizations:

- Decide who can access information.
    
- Select appropriate security controls.
    
- Apply encryption where necessary.
    
- Determine storage and sharing requirements.
    
- Reduce accidental information exposure.
    

## 5. Information Security Threats

### 5.1 Unauthorized Access

Occurs when someone accesses information without permission.

Example: An attacker obtains an employee's credentials and accesses confidential records.

### 5.2 Data Leakage

Data leakage occurs when sensitive information is exposed to unauthorized parties.

It may happen through:

- Misconfigured cloud storage.
    
- Incorrect email recipients.
    
- Lost devices.
    
- Insecure file sharing.
    
- Improper disposal of documents.
    

### 5.3 Data Theft

Data theft involves intentionally obtaining information without authorization.

Examples:

- Stealing customer databases.
    
- Copying confidential documents.
    
- Extracting intellectual property.
    

### 5.4 Data Modification

Unauthorized changes can affect the accuracy and reliability of information.

Examples:

- Altering financial records.
    
- Modifying examination results.
    
- Changing transaction details.
    

### 5.5 Data Destruction

Information may be deleted, corrupted, or destroyed intentionally or accidentally.

Examples:

- Ransomware encryption.
    
- Accidental file deletion.
    
- Hardware failure.
    
- Destructive malware.
    

### 5.6 Insider Threats

An insider threat involves someone with legitimate access misusing that access or unintentionally exposing information.

Examples:

- An employee sharing confidential files without permission.
    
- A staff member accidentally sending records to the wrong recipient.
    
- A privileged user abusing administrative access.
    

## 6. Information Security Controls

Security controls are safeguards used to reduce information security risks.

They can be grouped into three major categories.

### 6.1 Administrative Controls

Administrative controls involve policies, procedures, and organizational rules.

Examples:

- Information security policies.
    
- Employee security awareness training.
    
- Access management procedures.
    
- Risk assessments.
    
- Incident response plans.
    

### 6.2 Technical Controls

Technical controls use technology to protect information.

Examples:

- Encryption.
    
- Authentication.
    
- Access control systems.
    
- Antivirus software.
    
- Firewalls.
    
- Data Loss Prevention (DLP) tools.
    

### 6.3 Physical Controls

Physical controls protect the physical environment where information and systems are stored.

Examples:

- Locked server rooms.
    
- Security cameras.
    
- Access cards.
    
- Biometric entry systems.
    
- Secure document storage.
    
- Shredding confidential paper documents.
    

### Comparison

|Control Type|Main Purpose|Example|
|---|---|---|
|Administrative|Establish rules and processes|Security policy|
|Technical|Protect systems and information using technology|Encryption|
|Physical|Protect physical assets and locations|Locked server room|

## 7. Access Control

Access control determines who can access information and what actions they can perform.

### 7.1 Authentication

Authentication verifies the identity of a user or system.

Examples:

- Passwords
    
- Fingerprints
    
- Security keys
    
- One-time passwords
    

### 7.2 Authorization

Authorization determines which resources an authenticated identity is permitted to access.

Example:

A student may view examination results but may not modify them.

### 7.3 Least Privilege

The principle of least privilege means giving users and systems only the permissions required to perform their tasks.

### 7.4 Role-Based Access Control (RBAC)

RBAC assigns permissions based on organizational roles.

Example:

|Role|Permission|
|---|---|
|Student|View personal results|
|Teacher|Manage assigned student records|
|Administrator|Manage authorized system settings|

Related note: [[Security Principles]]

## 8. Data Protection Techniques

### 8.1 Encryption

Encryption converts readable information into ciphertext so unauthorized parties cannot easily understand it.

Two important forms:

- Encryption at rest: Protects stored information.
    
- Encryption in transit: Protects information while it is being transmitted.
    

### 8.2 Hashing

Hashing converts data into a fixed-length digest using a hash function.

It is commonly used for:

- File integrity verification.
    
- Digital signatures.
    
- Password storage when using dedicated password-hashing algorithms.
    

A cryptographic hash is designed to be one-way; it is not the same as encryption.

Examples:

- SHA-256
    
- SHA-3
    

### 8.3 Backup

A backup is a separate copy of information that can be used for recovery.

Good backup practices include:

- Maintaining multiple copies.
    
- Storing copies in separate locations.
    
- Restricting backup access.
    
- Testing restoration procedures.
    
- Protecting backups from ransomware.
    

### 8.4 Data Loss Prevention (DLP)

DLP technologies and policies help identify and prevent unauthorized exposure or transfer of sensitive information.

Examples:

- Detecting sensitive information in outgoing emails.
    
- Restricting copying to unauthorized removable storage.
    
- Monitoring sensitive file transfers.
    

## 9. Information Security Policies

An Information Security Policy defines how an organization protects and manages its information.

A policy may cover:

1. Acceptable use of organizational systems.
    
2. Password requirements.
    
3. Data classification.
    
4. Access permissions.
    
5. Remote working security.
    
6. Information sharing.
    
7. Backup requirements.
    
8. Incident reporting.
    
9. Device security.
    
10. Data retention and disposal.
    

Employees and other authorized users are expected to follow applicable policies.

## 10. Information Security Standards and Frameworks

Organizations use standards and frameworks to establish structured security practices.

### 10.1 ISO/IEC 27001

ISO/IEC 27001 specifies requirements for establishing, implementing, maintaining, and continually improving an Information Security Management System (ISMS).

It provides a systematic approach to managing information security risks.

### 10.2 NIST Cybersecurity Framework

The NIST Cybersecurity Framework provides guidance for managing cybersecurity risk.

Its six functions in CSF 2.0 are:

1. Govern
    
2. Identify
    
3. Protect
    
4. Detect
    
5. Respond
    
6. Recover
    

### 10.3 CIS Controls

The CIS Critical Security Controls provide prioritized safeguards organizations can implement to improve cybersecurity.

These frameworks support security management, but they do not automatically guarantee that an organization is secure.

## 11. Information Security vs Cybersecurity

These terms are related but not identical.

|Information Security|Cybersecurity|
|---|---|
|Protects information in all forms|Focuses on protecting digital systems and environments|
|Includes physical and digital information|Primarily concerns digital threats and assets|
|Covers information handling and protection|Covers networks, devices, applications, and digital infrastructure|
|Includes physical document security|Includes malware defense and network protection|

Information Security is generally broader in its treatment of information regardless of format, while Cybersecurity focuses on digital environments.

## 12. Information Security Incident Handling

When information is exposed, modified, or destroyed without authorization, organizations need a structured response.

Typical activities include:

1. Detect the incident.
    
2. Report and document it.
    
3. Contain the exposure or damage.
    
4. Investigate what happened.
    
5. Recover affected information and systems.
    
6. Notify relevant stakeholders when required.
    
7. Review the incident and improve controls.
    

Incident handling should follow organizational procedures and applicable legal requirements.

## 13. Practical Lab — Information Classification

**Objective:** Learn how to classify information based on sensitivity.

Classify the following fictional information using the four-level model from Section 4.

|Information|Your Classification|
|---|---|
|Public college website URL||
|Internal classroom timetable||
|Student examination records||
|Database administrator password||
|Public event announcement||
|Confidential business proposal||

Then answer:

1. Why should a database administrator password have strict access controls?
    
2. Why should examination records not be publicly accessible?
    
3. What could happen if confidential information is emailed to the wrong person?
    
4. Which technical and administrative controls could protect these records?
    

Write your answers in your notebook.

## 14. Key Terms

|Term|Meaning|
|---|---|
|InfoSec|Information Security|
|CIA Triad|Confidentiality, Integrity, and Availability|
|ISMS|Information Security Management System|
|DLP|Data Loss Prevention|
|RBAC|Role-Based Access Control|
|MFA|Multi-Factor Authentication|
|Encryption|Converts readable information into ciphertext|
|Hashing|Produces a fixed-length digest from data|
|Data Leakage|Unauthorized exposure of information|
|Least Privilege|Giving only necessary permissions|
|ISO 27001|Information Security Management System standard|
|NIST CSF|Cybersecurity risk management framework|

## 15. Summary

Information Security protects information throughout its lifecycle, regardless of its format.

Its major components include:

- Information classification.
    
- Access control.
    
- Encryption and hashing.
    
- Backup and recovery.
    
- Administrative policies.
    
- Technical safeguards.
    
- Physical security.
    
- Risk management and incident handling.
    

Effective Information Security requires people, processes, and technology to work together.

## 16. My Understanding

Write your own explanation:

- What is Information Security?
    
- What are the three goals of the CIA Triad?
    
- What is information classification?
    
- What is the difference between authentication and authorization?
    
- What is the difference between hashing and encryption?
    
- What are administrative, technical, and physical controls?
    
- How is Information Security different from Cybersecurity?
    

## 17. Questions & Doubts

Record unfamiliar terms, standards, and information protection concepts that you want to investigate further.