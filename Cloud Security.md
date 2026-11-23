> Cloud Security is the practice of protecting cloud-based infrastructure, applications, services, identities, and data from unauthorized access, attacks, misconfigurations, and other security risks.

## 1. Introduction to Cloud Security

Cloud computing allows individuals and organizations to access computing resources over the internet instead of managing all infrastructure locally.

These resources may include:

- Virtual machines
    
- Storage
    
- Databases
    
- Networking
    
- Applications
    
- Development platforms
    
- Security services
    

Cloud Security focuses on protecting these resources and ensuring that they remain confidential, integral, and available.

### Main Goals

1. **Confidentiality:** Prevent unauthorized access to cloud data.
    
2. **Integrity:** Prevent unauthorized modification of cloud resources.
    
3. **Availability:** Keep cloud services accessible.
    
4. **Identity Protection:** Ensure only authorized identities can access resources.
    
5. **Compliance:** Meet applicable legal, regulatory, and organizational requirements.
    

Related note: [[CIA Triad]]

## 2. What Is Cloud Computing?

Cloud computing is the delivery of computing services over a network, usually the internet.

Instead of purchasing and maintaining every physical server, organizations can rent computing resources from cloud providers.

Examples of cloud providers:

- Amazon Web Services (AWS)
    
- Microsoft Azure
    
- Google Cloud Platform (GCP)
    

### Advantages of Cloud Computing

- Scalability
    
- Flexible resource usage
    
- Reduced infrastructure maintenance
    
- Remote accessibility
    
- Backup and recovery options
    
- Faster deployment
    

Cloud computing also introduces security responsibilities that must be managed properly.

## 3. Cloud Service Models

Cloud services are commonly divided into three models.

### 3.1 Infrastructure as a Service (IaaS)

IaaS provides virtualized computing infrastructure.

The customer manages much of the operating system, applications, and configuration, while the provider manages the underlying physical infrastructure.

Examples:

- Amazon EC2
    
- Azure Virtual Machines
    
- Google Compute Engine
    

Security responsibilities commonly include:

- Operating system updates.
    
- Firewall configuration.
    
- Application security.
    
- Identity and access management.
    
- Data protection.
    

### 3.2 Platform as a Service (PaaS)

PaaS provides a platform for developing and deploying applications.

The cloud provider manages more of the underlying infrastructure and platform components.

Examples:

- Azure App Service
    
- Google App Engine
    
- AWS Elastic Beanstalk
    

Customer responsibilities commonly include:

- Application security.
    
- Data protection.
    
- Identity and access configuration.
    
- Secure application settings.
    

### 3.3 Software as a Service (SaaS)

SaaS provides ready-to-use applications through the internet.

The provider manages the application infrastructure, while customers remain responsible for appropriate account, access, and data security settings.

Examples:

- Microsoft 365
    
- Google Workspace
    
- Salesforce
    

### Comparison

|Model|What the Provider Supplies|Customer Security Focus|
|---|---|---|
|IaaS|Virtualized infrastructure|OS, applications, network configuration, data|
|PaaS|Managed application platform|Application, data, identity, configuration|
|SaaS|Ready-to-use software|Accounts, access, data, usage configuration|

## 4. Cloud Deployment Models

### 4.1 Public Cloud

Cloud infrastructure is provided by a third-party provider and shared across multiple customers through logically separated environments.

Examples:

- AWS
    
- Azure
    
- Google Cloud
    

### 4.2 Private Cloud

Cloud infrastructure is dedicated to one organization.

It may be hosted internally or by a third-party provider.

Advantages may include greater control over infrastructure and customization.

### 4.3 Hybrid Cloud

Hybrid cloud combines private infrastructure with public cloud services.

Organizations can distribute workloads between environments.

### 4.4 Multi-Cloud

Multi-cloud means using services from multiple cloud providers.

For example, an organization may use AWS for computing and Microsoft Azure for other services.

## 5. Shared Responsibility Model

The Shared Responsibility Model explains how security responsibilities are divided between a cloud provider and its customer.

The exact division depends on the provider and service model.

### Cloud Provider Responsibilities

Typically include:

- Physical data center security.
    
- Physical hardware protection.
    
- Underlying infrastructure.
    
- Core cloud platform security.
    

### Customer Responsibilities

Depending on the service model, typically include:

- User account security.
    
- Access permissions.
    
- Data classification.
    
- Application security.
    
- Secure configurations.
    
- Operating system maintenance where applicable.
    

### Example

If a customer accidentally makes a cloud storage bucket publicly accessible, this is generally a customer-side configuration issue.

A secure cloud provider does not automatically guarantee secure customer configurations.

## 6. Common Cloud Security Threats

### 6.1 Misconfiguration

Incorrect cloud settings may expose resources to unauthorized users.

Examples:

- Publicly accessible storage.
    
- Overly permissive access policies.
    
- Exposed management interfaces.
    
- Unrestricted network rules.
    

**Prevention:**

- Review configurations regularly.
    
- Apply secure configuration baselines.
    
- Restrict public access.
    
- Use automated configuration monitoring.
    

### 6.2 Data Breaches

A data breach occurs when sensitive information is accessed, disclosed, or acquired without authorization.

Possible causes:

- Stolen credentials.
    
- Misconfigured storage.
    
- Vulnerable applications.
    
- Excessive permissions.
    

**Prevention:**

- Encrypt sensitive data.
    
- Apply least privilege.
    
- Monitor access.
    
- Protect credentials.
    
- Maintain appropriate backups.
    

### 6.3 Account Hijacking

Account hijacking occurs when an attacker gains control of a legitimate cloud account.

Common causes:

- Phishing.
    
- Stolen passwords.
    
- Credential reuse.
    
- Exposed access keys.
    

**Prevention:**

- Enable MFA.
    
- Use strong unique passwords.
    
- Rotate exposed credentials.
    
- Monitor unusual sign-in activity.
    
- Restrict privileged accounts.
    

### 6.4 Insecure APIs

Cloud platforms expose APIs for managing resources and services.

Weak API security may allow unauthorized operations or data access.

**Prevention:**

- Require authentication.
    
- Enforce authorization.
    
- Validate input.
    
- Apply rate limiting.
    
- Monitor API activity.
    

### 6.5 Denial of Service

Cloud services can be affected by attacks that consume computing, storage, or network resources.

**Prevention:**

- Use appropriate traffic protection.
    
- Apply rate limiting.
    
- Monitor resource consumption.
    
- Configure scaling and service limits.
    

### 6.6 Insider Threats

An insider threat involves a person with legitimate organizational access misusing that access, intentionally or accidentally.

**Prevention:**

- Apply least privilege.
    
- Monitor privileged activities.
    
- Review permissions regularly.
    
- Remove access when no longer required.
    

### 6.7 Insecure Credentials and Secrets

Cloud applications may depend on API keys, passwords, tokens, and certificates.

If these are exposed, attackers may gain access to cloud resources.

**Prevention:**

- Use a secrets manager.
    
- Avoid hardcoding credentials.
    
- Restrict key permissions.
    
- Rotate exposed secrets.
    
- Monitor credential usage.
    

## 7. Cloud Security Controls

### 7.1 Identity and Access Management (IAM)

IAM controls which users and services can access cloud resources.

Important concepts:

- Users
    
- Groups
    
- Roles
    
- Policies
    
- Permissions
    
- Service identities
    

Follow the principle of least privilege: provide only the permissions necessary for a task.

Related note: [[Identity and Access Management]]

### 7.2 Multi-Factor Authentication

MFA requires additional verification beyond a password.

It helps reduce the risk of account compromise when passwords are stolen.

Enable MFA for privileged and sensitive cloud accounts.

### 7.3 Encryption

Encryption protects information by converting readable data into ciphertext.

Two important states:

|Type|Description|
|---|---|
|Encryption at rest|Protects stored data|
|Encryption in transit|Protects data moving between systems|

Encryption keys must also be securely managed.

### 7.4 Network Security

Cloud networks require controls that restrict communication between resources.

Common controls:

- Virtual networks.
    
- Security groups.
    
- Network access control lists.
    
- Firewalls.
    
- Private endpoints.
    
- Network segmentation.
    

### 7.5 Logging and Monitoring

Cloud logging records activities performed by users, applications, and services.

Monitoring helps identify suspicious behavior.

Examples:

- Unexpected login locations.
    
- Unusual API activity.
    
- Changes to access policies.
    
- Unexpected public exposure.
    
- Unusual resource consumption.
    

### 7.6 Backup and Recovery

Cloud data should be backed up according to business and recovery requirements.

Important considerations:

- Backup frequency.
    
- Retention period.
    
- Backup encryption.
    
- Access restrictions.
    
- Recovery testing.
    
- Protection against backup deletion or ransomware.
    

## 8. Cloud Security Tools and Services

|Tool or Service|Purpose|
|---|---|
|AWS IAM|Manages identities and permissions in AWS|
|AWS CloudTrail|Records AWS account activity|
|AWS GuardDuty|Detects potential threats in AWS environments|
|Microsoft Defender for Cloud|Provides cloud security posture and threat protection capabilities|
|Microsoft Entra ID|Manages identity and access|
|Google Cloud IAM|Controls access to Google Cloud resources|
|Google Security Command Center|Helps identify and manage cloud security risks|
|HashiCorp Vault|Manages secrets and sensitive credentials|

These tools have different capabilities and are not direct substitutes for one another.

## 9. Cloud Security Best Practices

1. Enable MFA.
    
2. Apply least-privilege permissions.
    
3. Encrypt sensitive information.
    
4. Secure storage services.
    
5. Monitor cloud activity.
    
6. Protect API keys and secrets.
    
7. Apply security updates.
    
8. Use secure network configurations.
    
9. Maintain tested backups.
    
10. Review access permissions regularly.
    
11. Enable appropriate security logging.
    
12. Follow the provider's shared responsibility model.
    

## 10. Practical Lab — Understand Cloud Security Concepts

**Objective:** Understand cloud security responsibilities without creating a paid cloud resource.

### Step 1: Study a Cloud Scenario

Imagine an organization stores customer documents in a cloud storage service.

The organization accidentally configures the storage resource so that anyone with the public link can access the documents.

### Step 2: Identify the Risks

Answer:

1. Which security principle is affected?
    
2. What type of cloud security weakness occurred?
    
3. Who is generally responsible for configuring customer storage permissions?
    
4. How could the organization prevent this issue?
    
5. What should the organization do after discovering the exposure?
    

### Step 3: Understand the Shared Responsibility Model

Choose an example from IaaS, PaaS, or SaaS.

Write down:

- What the provider manages.
    
- What the customer manages.
    
- Which security responsibilities remain with the customer.
    

### Step 4: Document Your Findings

Create a short observation in your notebook:

- Cloud service model:
    
- Security weakness:
    
- Possible impact:
    
- Preventive controls:
    
- Recovery action:
    

## 11. Key Terms

|Term|Meaning|
|---|---|
|Cloud Computing|Delivery of computing services over a network|
|IaaS|Infrastructure as a Service|
|PaaS|Platform as a Service|
|SaaS|Software as a Service|
|IAM|Identity and Access Management|
|MFA|Multi-Factor Authentication|
|API|Application Programming Interface|
|CSP|Cloud Service Provider|
|Shared Responsibility Model|Division of security responsibilities between provider and customer|
|Encryption at Rest|Protection of stored data|
|Encryption in Transit|Protection of data during transmission|
|Secrets Management|Secure handling of credentials and keys|

## 12. Summary

Cloud Security protects cloud infrastructure, applications, identities, and data.

Its major components include:

- Identity and access management.
    
- Encryption.
    
- Network security.
    
- Secure configuration.
    
- Logging and monitoring.
    
- Backup and recovery.
    
- Shared responsibility.
    

Cloud security requires both provider-side protection and correct customer-side configuration.

## 13. My Understanding

Write your own explanation:

- What is Cloud Security?
    
- What is the difference between IaaS, PaaS, and SaaS?
    
- What is the Shared Responsibility Model?
    
- Why are cloud misconfigurations dangerous?
    
- What is the difference between encryption at rest and in transit?
    
- Why is IAM important in cloud environments?
    

## 14. Questions & Doubts

Record unfamiliar cloud services, security controls, and concepts that you want to investigate further.