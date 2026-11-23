> Application Security (AppSec) is the practice of protecting software applications from vulnerabilities, unauthorized access, data breaches, and other security threats throughout their lifecycle.

## 1. Introduction to Application Security

Applications are used for banking, communication, shopping, education, healthcare, and business operations.

They process sensitive information such as:

- Usernames and passwords
    
- Personal information
    
- Payment details
    
- Business records
    
- Authentication tokens
    
- Confidential documents
    

If an application contains security weaknesses, attackers may exploit them to access data, modify information, or disrupt services.

Application Security focuses on identifying and reducing these weaknesses.

### Main Goals

1. **Confidentiality:** Protect sensitive application data.
    
2. **Integrity:** Prevent unauthorized changes to data and application behavior.
    
3. **Availability:** Keep applications accessible and operational.
    
4. **Authentication:** Verify the identity of users and systems.
    
5. **Authorization:** Ensure users can access only permitted resources.
    

## 2. Components of an Application

A modern application may contain several components.

### 2.1 Frontend

The frontend is the part of an application that users interact with.

Examples:

- Login pages
    
- Forms
    
- Buttons
    
- Dashboards
    
- Navigation menus
    

Common technologies:

- HTML
    
- CSS
    
- JavaScript
    
- React
    
- Angular
    

Frontend security concerns include unsafe handling of user input, exposed sensitive information, and client-side access-control weaknesses.

### 2.2 Backend

The backend handles application logic and communicates with databases and other services.

Common technologies:

- Python
    
- Java
    
- PHP
    
- Node.js
    
- C#
    

Backend security is important because it enforces authentication, authorization, validation, and business rules.

### 2.3 Database

A database stores application information.

Examples:

- MySQL
    
- PostgreSQL
    
- SQLite
    
- MongoDB
    

Database security includes:

- Access control
    
- Secure authentication
    
- Encryption
    
- Backup protection
    
- Input validation
    
- Secure database configuration
    

### 2.4 APIs

An Application Programming Interface (API) allows different software components to communicate.

Examples:

- A frontend requesting user information from a backend.
    
- A mobile application communicating with a server.
    
- A payment service processing transactions.
    

API security requires proper authentication, authorization, input validation, and rate limiting.

## 3. Common Application Security Vulnerabilities

### 3.1 SQL Injection (SQLi)

SQL Injection occurs when untrusted input is improperly included in SQL queries.

It may allow attackers to manipulate database queries.

Potential consequences:

- Unauthorized data access.
    
- Modification or deletion of records.
    
- Authentication bypass.
    
- Exposure of sensitive information.
    

**Prevention:**

- Use parameterized queries.
    
- Avoid constructing SQL queries through unsafe string concatenation.
    
- Apply least-privilege database permissions.
    
- Validate input.
    
- Handle errors securely.
    

### 3.2 Cross-Site Scripting (XSS)

XSS occurs when an application includes untrusted content in a webpage in a way that allows malicious scripts to execute in another user's browser.

Common types:

|Type|Description|
|---|---|
|Stored XSS|Malicious content is stored by the application and later displayed to users.|
|Reflected XSS|Malicious input is immediately reflected in a response.|
|DOM-based XSS|Client-side JavaScript handles untrusted data unsafely, changing the page in a dangerous way.|

**Prevention:**

- Apply context-aware output encoding.
    
- Sanitize HTML when rich HTML input is required.
    
- Use secure frameworks and safe DOM APIs.
    
- Apply Content Security Policy (CSP) as an additional defense.
    
- Avoid inserting untrusted input directly into executable contexts.
    

### 3.3 Broken Access Control

Broken Access Control occurs when an application fails to enforce restrictions on what authenticated users can access or modify.

Example:

A normal user changes a URL containing an account ID and accesses another user's information.

**Prevention:**

- Enforce authorization on the server.
    
- Check permissions for every sensitive operation.
    
- Apply least privilege.
    
- Do not rely on hidden buttons or frontend restrictions.
    
- Test access-control rules using different user roles.
    

### 3.4 Security Misconfiguration

Security Misconfiguration occurs when application components are configured insecurely.

Examples:

- Default passwords.
    
- Debug mode enabled in production.
    
- Unnecessary services enabled.
    
- Publicly exposed administrative interfaces.
    
- Incorrect security headers.
    
- Excessive permissions.
    

**Prevention:**

- Use secure configuration baselines.
    
- Remove unnecessary services.
    
- Disable production debugging.
    
- Change default credentials.
    
- Review configurations regularly.
    

### 3.5 Authentication Failures

Authentication weaknesses may allow unauthorized users to access accounts.

Examples:

- Weak passwords.
    
- Poor password-reset mechanisms.
    
- Missing multi-factor authentication.
    
- Insecure session handling.
    
- Inadequate protection against automated login attempts.
    

**Prevention:**

- Use secure password hashing.
    
- Implement MFA.
    
- Apply rate limiting.
    
- Use secure password-reset workflows.
    
- Protect authentication sessions.
    

### 3.6 Server-Side Request Forgery (SSRF)

SSRF occurs when an attacker can influence a server to send requests to unintended destinations.

This may expose internal services or information that should not be publicly accessible.

**Prevention:**

- Validate and restrict destination addresses.
    
- Use allowlists for permitted destinations.
    
- Block access to sensitive internal services.
    
- Apply network-level restrictions.
    
- Avoid trusting user-supplied URLs without validation.
    

### 3.7 Insecure File Upload

An insecure file-upload feature may allow users to upload dangerous or unexpected files.

Potential risks:

- Malware storage.
    
- Unauthorized file access.
    
- Server-side code execution in vulnerable configurations.
    
- Storage exhaustion.
    

**Prevention:**

- Validate file type and content.
    
- Limit file size.
    
- Generate server-side filenames.
    
- Store uploads outside executable web directories.
    
- Apply appropriate access controls.
    
- Scan uploaded files where appropriate.
    

## 4. OWASP Top 10

The OWASP Top 10 is a widely recognized awareness document highlighting important web application security risks.

OWASP periodically updates its categories.

The 2025 edition includes:

|Category|Description|
|---|---|
|A01:2025 Broken Access Control|Failures in enforcing access restrictions|
|A02:2025 Security Misconfiguration|Insecure application or infrastructure configuration|
|A03:2025 Software Supply Chain Failures|Risks involving software dependencies, build systems, and suppliers|
|A04:2025 Cryptographic Failures|Weak or incorrectly implemented cryptographic protections|
|A05:2025 Injection|Untrusted input being interpreted as commands or queries|
|A06:2025 Insecure Design|Security weaknesses originating in design decisions|
|A07:2025 Authentication Failures|Weaknesses in identity verification and authentication|
|A08:2025 Software or Data Integrity Failures|Failures to protect software and data integrity|
|A09:2025 Security Logging and Alerting Failures|Inadequate security logging, detection, and alerting|
|A10:2025 Mishandling of Exceptional Conditions|Improper handling of errors and unexpected conditions|

The OWASP Top 10 is an awareness resource, not a complete application security testing checklist.

Related concepts: [[Types of Cyber Attacks]], [[Security Principles]]

## 5. Secure Software Development Lifecycle (SSDLC)

The Secure Software Development Lifecycle integrates security into every stage of software development.

### Main Stages

1. **Planning:** Identify security requirements and potential risks.
    
2. **Design:** Create secure architecture and threat models.
    
3. **Development:** Follow secure coding practices.
    
4. **Testing:** Identify and fix security weaknesses.
    
5. **Deployment:** Configure production environments securely.
    
6. **Maintenance:** Monitor, update, and improve application security.
    

Security should not be added only after development is complete.

## 6. Secure Coding Practices

Secure coding means writing software in a way that reduces security vulnerabilities.

Important practices:

### Input Validation

Validate input received from users and external systems.

Check:

- Data type
    
- Length
    
- Format
    
- Allowed values
    
- Expected structure
    

### Output Encoding

Encode untrusted data appropriately before displaying it in a browser.

This helps prevent injection into HTML, JavaScript, and other contexts.

### Password Security

- Never store plaintext passwords.
    
- Use dedicated password-hashing algorithms such as Argon2id, bcrypt, or scrypt.
    
- Use unique salts.
    
- Protect password-reset workflows.
    

### Error Handling

- Do not expose stack traces or sensitive internal details to users.
    
- Record useful diagnostic information securely.
    
- Avoid logging passwords, authentication tokens, or other secrets.
    

### Access Control

- Enforce permissions on the server.
    
- Follow least privilege.
    
- Verify resource ownership.
    
- Deny access by default when permission is not established.
    

### Dependency Management

- Use trusted software packages.
    
- Update vulnerable dependencies.
    
- Review third-party libraries.
    
- Remove unused dependencies.
    
- Monitor software supply-chain risks.
    

## 7. Application Security Testing

Security testing helps identify weaknesses before attackers exploit them.

### 7.1 Static Application Security Testing (SAST)

SAST examines source code or compiled code without running the application.

It can identify:

- Unsafe coding patterns.
    
- Potential injection vulnerabilities.
    
- Hardcoded secrets.
    
- Certain insecure API usages.
    

### 7.2 Dynamic Application Security Testing (DAST)

DAST tests a running application from the outside.

It can identify issues such as:

- Improper security headers.
    
- Certain injection vulnerabilities.
    
- Authentication weaknesses.
    
- Exposed application behavior.
    

### 7.3 Interactive Application Security Testing (IAST)

IAST analyzes an application while it is running, often using instrumentation to observe application behavior internally.

### 7.4 Software Composition Analysis (SCA)

SCA identifies and evaluates third-party libraries and dependencies used by an application.

It can help detect:

- Known vulnerable dependencies.
    
- Outdated packages.
    
- License risks.
    
- Dependency-related security issues.
    

### Comparison

|Testing Method|Main Focus|
|---|---|
|SAST|Source code or compiled code|
|DAST|Running application from the outside|
|IAST|Application behavior during execution|
|SCA|Third-party dependencies|

## 8. Web Application Security Tools

|Tool|Purpose|
|---|---|
|Burp Suite|Intercepts and analyzes web application traffic|
|OWASP ZAP|Web application security testing|
|Nmap|Network and service discovery|
|Nikto|Web server security scanning|
|Semgrep|Static code analysis|
|SonarQube|Code quality and security analysis|
|Dependency-Check|Identifies vulnerable dependencies|

Use testing tools only against applications you own or have explicit permission to assess.

Related notes:

- [[Security Tools]]
    
- [[Cybersecurity Labs]]
    

## 9. Application Security Best Practices

### For Developers

1. Follow secure coding practices.
    
2. Validate untrusted input.
    
3. Use parameterized database queries.
    
4. Implement proper authentication and authorization.
    
5. Store passwords using secure hashing.
    
6. Protect session identifiers.
    
7. Handle errors securely.
    
8. Keep dependencies updated.
    
9. Avoid exposing secrets in source code.
    
10. Perform security testing before deployment.
    

### For Application Administrators

1. Use HTTPS.
    
2. Apply security updates.
    
3. Disable unnecessary services.
    
4. Configure secure HTTP headers.
    
5. Monitor application logs.
    
6. Restrict administrative access.
    
7. Maintain secure backups.
    
8. Review application permissions.
    

## 10. Practical Lab — Understand Input Validation

**Objective:** Observe how applications should validate user input.

Create a small HTML file named `input-validation.html` on your computer.

Use this example:

```
<!DOCTYPE html>
<html>
<head>
    <title>Input Validation Lab</title>
</head>
<body>
    <h2>Username Validation</h2>

    <form id="userForm">
        <label>Username:</label>
        <input
            type="text"
            id="username"
            minlength="3"
            maxlength="20"
            required
        >

        <button type="submit">Submit</button>
    </form>

    <p id="result"></p>

    <script>
        const form = document.getElementById("userForm");
        const username = document.getElementById("username");
        const result = document.getElementById("result");

        form.addEventListener("submit", function(event) {
            event.preventDefault();

            const value = username.value.trim();

            if (!/^[a-zA-Z0-9_]{3,20}$/.test(value)) {
                result.textContent = "Invalid username.";
                return;
            }

            result.textContent = "Username accepted.";
        });
    </script>
</body>
</html>
```

### Test Cases

|Input|Expected Result|
|---|---|
|`Mohit123`|Accepted|
|`abc`|Accepted|
|`ab`|Rejected|
|`user@123`|Rejected|
|`user name`|Rejected|
|Empty input|Rejected|

### Important Security Observation

This exercise demonstrates client-side validation only.

A real application must validate input again on the server because users can bypass browser-side restrictions.

Also, validation does not replace context-aware output encoding or safe database queries.

Record:

- Which inputs were accepted?
    
- Which inputs were rejected?
    
- Why is client-side validation insufficient?
    
- Where should validation occur in a real application?
    

## 11. Key Terms

|Term|Meaning|
|---|---|
|AppSec|Application Security|
|OWASP|Open Worldwide Application Security Project|
|SQLi|SQL Injection|
|XSS|Cross-Site Scripting|
|SSRF|Server-Side Request Forgery|
|SSDLC|Secure Software Development Lifecycle|
|SAST|Static Application Security Testing|
|DAST|Dynamic Application Security Testing|
|IAST|Interactive Application Security Testing|
|SCA|Software Composition Analysis|
|CSP|Content Security Policy|
|API|Application Programming Interface|

## 12. Summary

Application Security protects software throughout its lifecycle.

Important areas include:

- Secure application architecture.
    
- Authentication and authorization.
    
- Input validation and output encoding.
    
- Secure database access.
    
- Secure coding.
    
- Vulnerability testing.
    
- Dependency management.
    
- Secure deployment and maintenance.
    

A secure application requires cooperation between developers, security professionals, administrators, and testers.

## 13. My Understanding

Write your own explanation:

- What is Application Security?
    
- What is the difference between authentication and authorization?
    
- How does SQL Injection happen?
    
- What is the difference between stored and reflected XSS?
    
- Why is server-side validation necessary?
    
- What is the difference between SAST and DAST?
    
- Why is security important during software development?
    

## 14. Questions & Doubts

Record unfamiliar vulnerabilities, tools, and secure coding concepts that you want to investigate further.