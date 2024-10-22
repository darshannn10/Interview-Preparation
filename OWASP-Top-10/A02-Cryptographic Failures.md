# A02-Cryptographic Failures

Previously known as *Sensitive Data Exposure,* **Cryptographic Failures** now focuses on the root cause rather than the symptom. This shift emphasizes that the primary concern is failures related to cryptography (or its absence), which can lead to the exposure of sensitive data.

## Understanding Cryptographic Failures

Cryptographic failures occur when an application fails to properly implement cryptographic measures to protect sensitive information. These failures can manifest in various ways, including:

- Using weak or outdated encryption algorithms
- Improper implementation of cryptographic functions
- Inadequate key management practices
- Failure to encrypt sensitive data at rest or in transit

## Common Weakness Enumerations (CWEs)

Notable CWEs associated with Cryptographic Failures include:

- [CWE-259: Use of Hard-coded Password](https://cwe.mitre.org/data/definitions/259.html) - This weakness occurs when a password is hard-coded into the application, making it easily discoverable by attackers.
- [CWE-327: Broken or Risky Crypto Algorithm](https://cwe.mitre.org/data/definitions/327.html) - This involves the use of a cryptographic algorithm that is either inherently flawed or implemented incorrectly, compromising the security of encrypted data.
- [CWE-331: Insufficient Entropy](https://cwe.mitre.org/data/definitions/331.html) - This weakness arises when there's not enough randomness in cryptographic operations, potentially making encrypted data vulnerable to prediction or brute-force attacks.

## Common Vulnerabilities and Exposures (CVEs)

Examples of CVEs related to these CWEs can be found at:

- [CVEs related to CWE-259](https://www.opencve.io/cve?cwe=CWE-259)
- [CVEs related to CWE-327](https://www.opencve.io/cve?cwe=CWE-327)
- [CVEs related to CWE-331](https://www.opencve.io/cve?cwe=CWE-331)

## Preventing Cryptographic Failures

To mitigate the risk of cryptographic failures, organizations should:

- Use strong, up-to-date encryption algorithms and protocols
- Implement proper key management practices
- Regularly audit and update cryptographic implementations
- Encrypt all sensitive data both at rest and in transit
- Avoid storing sensitive data unnecessarily
- [OWASP's transport layer protection cheat sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html)
- [OWASP's user privacy protection cheat sheet](https://cheatsheetseries.owasp.org/cheatsheets/User_Privacy_Protection_Cheat_Sheet.html)
- [OWASP's password and cryptographic storage cheat sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)

## Example Attack Scenarios

**Scenario #1**: An application encrypts credit card numbers in a database using automatic database encryption. However, this data is automatically decrypted when retrieved, allowing a SQL injection flaw to retrieve credit card numbers in clear text.

**Scenario #2**: A site doesn't use or enforce TLS for all pages or supports weak encryption. An attacker monitors network traffic (e.g., at an insecure wireless network), downgrades connections from HTTPS to HTTP, intercepts requests, and steals the user's session cookie. The attacker then replays this cookie and hijacks the user's (authenticated) session, accessing or modifying the user's private data. Instead of the above they could alter all transported data, e.g., the recipient of a money transfer.

**Scenario #3**: The password database uses unsalted or simple hashes to store everyone's passwords. A file upload flaw allows an attacker to retrieve the password database. All the unsalted hashes can be exposed with a rainbow table of pre-calculated hashes. Hashes generated by simple or fast hash functions may be cracked by GPUs, even if they were salted.

## **Examples of attacker scenarios using juice shop**

- **`Weird Crypto`** - Inform the shop about an algorithm or library it should definitely not use the way it does.
    - Hint: What is known weak cryptographic algorithms?
    - Create a new juice-shop user and change password for your new user with an easy one e.g 'admin123' and observe response from /change-password (In the Firefox tool)
    - For feedback use http://<yourhost>/#/contact
- `Forged Coupon` - Manipulate shopping coupon by discovering crypto algorithm.

By addressing these areas, organizations can significantly reduce their vulnerability to cryptographic failures and better protect sensitive information.