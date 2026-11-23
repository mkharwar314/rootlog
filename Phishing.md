> Understand how attackers use deceptive messages and websites to steal information, distribute malware, and gain unauthorized access.

## 1. What Is Phishing?

**Phishing** is a type of cyberattack in which an attacker impersonates a trusted person, organization, or service to trick victims into revealing sensitive information or performing unsafe actions.

Attackers commonly attempt to steal:

- Usernames and passwords.
    
- Banking information.
    
- Credit and debit card details.
    
- One-time passwords (OTPs).
    
- Personal information.
    
- Corporate login credentials.
    

Phishing is a form of social engineering because it manipulates human trust and behaviour.

## 2. How Phishing Works

A typical phishing attack follows these steps:

1. **Target selection:** The attacker identifies potential victims.
    
2. **Impersonation:** The attacker pretends to represent a trusted organization or person.
    
3. **Message delivery:** A deceptive email, SMS, phone call, or social media message is sent.
    
4. **Victim interaction:** The victim clicks a link, opens an attachment, or shares information.
    
5. **Information theft or compromise:** The attacker collects credentials, delivers malware, or gains unauthorized access.
    
6. **Misuse:** The attacker may use stolen information for fraud, account takeover, or further attacks.
    

### Example

A victim receives an email claiming that their bank account will be suspended unless they verify their account immediately.

The email contains a link to a fake login page.

The victim enters their credentials, and the attacker captures them.

## 3. Types of Phishing

### 3.1 Email Phishing

Attackers send fraudulent emails that appear to come from legitimate organizations.

Common characteristics:

- Urgent language.
    
- Suspicious links.
    
- Unexpected attachments.
    
- Requests for sensitive information.
    
- Fake sender identities.
    

**Example:** A fake email claiming that an online account needs immediate verification.

### 3.2 Spear Phishing

Spear phishing targets a specific individual or organization.

Attackers may research the victim before creating a personalized message.

**Example:** An employee receives an email mentioning their manager and a real project, asking them to open a malicious document.

### 3.3 Whaling

Whaling is a type of spear phishing that specifically targets senior executives or other high-value individuals.

**Example:** An attacker impersonates a company executive to request confidential financial information.

### 3.4 Smishing

Smishing means SMS phishing.

Attackers use text messages to trick victims into clicking malicious links or sharing sensitive information.

**Example:** A fraudulent delivery message asks the recipient to pay an unexpected fee through a suspicious link.

### 3.5 Vishing

Vishing means voice phishing.

Attackers use phone calls or voice communication to manipulate victims.

**Example:** Someone impersonates a bank representative and requests an OTP.

### 3.6 Clone Phishing

In clone phishing, an attacker creates a copy of a legitimate message but replaces its original attachment or link with a malicious one.

**Example:** A victim receives a modified copy of a previously received business email containing a malicious attachment.

### 3.7 Angler Phishing

Angler phishing uses fake social media accounts or support profiles to impersonate legitimate brands or customer service representatives.

**Example:** A fake customer support account contacts someone who posted a complaint and requests their login information.

### 3.8 Search Engine Phishing

Attackers create deceptive websites or advertisements that appear in search results.

Victims may visit these websites believing they are legitimate services.

## 4. Phishing Comparison

|Type|Target or Delivery Method|
|---|---|
|Email phishing|General email recipients|
|Spear phishing|Specific individuals or organizations|
|Whaling|Senior executives|
|Smishing|SMS messages|
|Vishing|Phone or voice calls|
|Clone phishing|Copies of legitimate messages|
|Angler phishing|Social media users|
|Search engine phishing|Search engine users|

## 5. Common Phishing Techniques

### 5.1 Email Spoofing

Attackers manipulate email sender information to make a message appear to come from another address.

However, the displayed sender name alone does not establish the actual sender's identity.

### 5.2 Fake Websites

Attackers create websites that imitate legitimate services.

These websites may contain copied logos, login forms, and similar-looking page layouts.

### 5.3 URL Manipulation

Attackers use deceptive domain names or URLs to make malicious links look legitimate.

Examples of suspicious patterns include:

- Misspelled domain names.
    
- Extra words added to a domain.
    
- Unusual subdomains.
    
- Lookalike characters.
    
- URL shorteners hiding the destination.
    

Always inspect the actual destination rather than trusting the visible link text.

### 5.4 Malicious Attachments

Phishing messages may contain attachments designed to execute malicious code or exploit vulnerable software.

Unexpected attachments should be treated carefully, especially executable files and macro-enabled documents.

### 5.5 Psychological Manipulation

Attackers commonly use:

- Fear: "Your account will be blocked."
    
- Urgency: "Respond within 10 minutes."
    
- Curiosity: "See your confidential report."
    
- Authority: "Your manager requires this."
    
- Reward: "You have won a prize."
    

These techniques pressure victims into acting without verification.

## 6. Warning Signs of Phishing

Look for these indicators:

1. Unexpected requests for sensitive information.
    
2. Unusual urgency or threats.
    
3. Suspicious sender addresses.
    
4. Misspelled or misleading domains.
    
5. Unexpected attachments.
    
6. Requests for passwords or OTPs.
    
7. Unusual payment instructions.
    
8. Messages that do not match normal communication patterns.
    
9. Unexpected login prompts.
    
10. Links that lead to unrelated websites.
    

**Important:** A message can be grammatically correct and professionally written while still being fraudulent. Attackers increasingly use automation and AI to create convincing messages.

## 7. Phishing Prevention

### For Individuals

- Verify unexpected messages through official communication channels.
    
- Avoid opening suspicious attachments.
    
- Inspect links before visiting them.
    
- Never share passwords or OTPs with callers or message senders.
    
- Use multi-factor authentication.
    
- Keep browsers and operating systems updated.
    
- Use a password manager to reduce the risk of entering credentials on lookalike websites.
    

### For Organizations

- Conduct phishing-awareness training.
    
- Deploy email security gateways.
    
- Configure SPF, DKIM, and DMARC.
    
- Use multi-factor authentication.
    
- Monitor suspicious login activity.
    
- Establish procedures for reporting phishing messages.
    
- Apply least-privilege access controls.
    

## 8. Email Authentication Technologies

Email authentication helps receiving mail servers evaluate whether messages are authorized to use a domain.

### SPF — Sender Policy Framework

SPF allows a domain owner to specify which mail servers are authorized to send email for that domain.

### DKIM — DomainKeys Identified Mail

DKIM uses a digital signature to help verify that an email was authorized by the signing domain and that signed message content has not been altered.

### DMARC — Domain-based Message Authentication, Reporting and Conformance

DMARC builds on SPF and DKIM to define how receiving systems should handle messages that fail authentication checks and to provide reporting mechanisms.

**Important:** SPF, DKIM, and DMARC reduce certain types of email spoofing, but they do not guarantee that every email is safe.

## 9. What to Do If You Receive a Phishing Message

1. Do not click suspicious links.
    
2. Do not download unexpected attachments.
    
3. Do not provide personal information.
    
4. Verify the message using the organization's official website or contact details.
    
5. Report the message to the relevant email provider or security team.
    
6. Delete or quarantine the message according to your organization's procedure.
    

## 10. What to Do If You Become a Victim

If you entered credentials on a suspicious website:

1. Change the compromised password immediately using the official website.
    
2. Change the same password on other services where it was reused.
    
3. Enable multi-factor authentication.
    
4. Sign out other active sessions if the service provides that option.
    
5. Contact your bank immediately if financial information was exposed.
    
6. Inform your organization's IT or security team if a work account was affected.
    
7. Monitor accounts for suspicious activity.
    
8. Preserve relevant messages and evidence.
    

If malware may have been installed, disconnect the affected device from the network when appropriate and seek help from a qualified security professional.

## 11. Practical Lab — Identifying Phishing Indicators

This exercise uses a fictional email. Do not visit any links.

### Sample Email

```
From: Security Team <security-alert@example.net>

Subject: URGENT! Your Account Will Be Suspended

Dear User,

We detected unusual activity in your account.

Your account will be permanently suspended
unless you verify your information immediately.

Click here to verify your account:
http://example.com/account-verification

Thank you,
Security Team
```

### Your Task

Identify at least five warning signs.

Consider:

- Sender identity.
    
- Message urgency.
    
- Threat of account suspension.
    
- Unexpected verification request.
    
- Link destination.
    
- Whether the communication can be independently verified.
    

### PowerShell Exercise — Inspect a URL

You can examine a URL without opening it:

```
$url = "http://example.com/account-verification"

$uri = [System.Uri]$url

$uri.Scheme
$uri.Host
$uri.AbsolutePath
```

This displays the URL scheme, hostname, and path.

It does not determine whether the website is malicious. URL analysis requires additional context.

## 12. Phishing vs Spam

|Phishing|Spam|
|---|---|
|Attempts to deceive victims|Usually unwanted bulk communication|
|Often seeks sensitive information|Often promotes products or services|
|Can lead to account compromise|May simply be unwanted advertising|
|Can deliver malware|Can also contain malicious links or attachments|

Not all spam is phishing, and not all phishing messages are spam.

## 13. Key Takeaways

- Phishing is a social engineering attack.
    
- Attackers impersonate trusted people and organizations.
    
- Email phishing, spear phishing, whaling, smishing, and vishing are common types.
    
- Fake websites and deceptive URLs are common techniques.
    
- Urgency and fear are frequently used to manipulate victims.
    
- SPF, DKIM, and DMARC help improve email authentication.
    
- Multi-factor authentication reduces the impact of stolen passwords.
    
- Verification through trusted channels is essential.
    
- Report suspicious messages instead of interacting with them.
    

## 14. Related Notes

- [[Malware]]
    
- [[Types of Cyber Attacks]]
    
- [[Social Engineering]]
    
- [[Cybersecurity Terminology]]
    
- [[Security Principles]]
    
- [[Authentication and Authorization]]
    
- [[Security Tools]]
    
- [[Cybersecurity Labs]]