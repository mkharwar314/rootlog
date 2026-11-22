## 📌 What is Ransomware?
**Ransomware** is a critical type of malware that locks a user out of their system or denies access to their files, typically by encrypting them. The attacker then demands a payout (usually in cryptocurrency like Bitcoin) in exchange for the decryption key needed to restore access.

---

## 🔒 How It Works: The Attack Chain
1. **Infiltration:** Enters the system via phishing links, malicious email attachments, or exploiting open, unauthenticated remote desktop protocol (RDP) ports.
2. **Key Generation & Encryption:** The malware contacts the attacker's Command and Control (C2) server to generate an encryption key. It then silently encrypts personal documents, databases, images, and system files.
3. **The Note:** The malware drops a text file or changes the desktop wallpaper to display a ransom note with payment instructions and a countdown timer.

---

## 💥 Modern Evolution: Double Extortion
Modern ransomware actors don't just lock files; they use a technique called **Double Extortion**:
* **Phase 1:** They encrypt the files so the victim can't use their systems.
* **Phase 2:** Before encrypting, they sneakily exfiltrate (steal) the sensitive data. If the victim refuses to pay because they have backups, the attackers threaten to leak the stolen data publicly or sell it on the dark web.

---

## 🗺️ Navigation
* Back to Hub: [[Cyber Security]]
* Previous Note: [[Trojan]]
* Next Note: [[Spyware]]

---