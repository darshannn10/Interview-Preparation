# A07-Identification and Authentication Failures

Previously known as "Broken Authentication," this category focuses on vulnerabilities related to user identity confirmation, authentication processes, and session management. These aspects are crucial for protecting against authentication-related attacks.

Applications may have authentication weaknesses if they:

- Allow automated attacks like credential stuffing, where attackers use lists of valid usernames and passwords.
- Permit brute force or other automated attacks.
- Accept default, weak, or well-known passwords (e.g., "Password1" or "admin/admin").
- Implement weak or ineffective credential recovery and forgot-password processes, such as easily guessable "knowledge-based answers."
- Store passwords in plain text, encrypted, or weakly hashed formats (see A02:2021-Cryptographic Failures).
- Lack or have ineffective multi-factor authentication.
- Expose session identifiers in URLs.
- Reuse session identifiers after successful login.
- Fail to properly invalidate session IDs, authentication tokens, or single sign-on (SSO) tokens during logout or after periods of inactivity.

## Notable Common Weakness Enumerations (CWEs)

- [CWE-297:](https://cwe.mitre.org/data/definitions/297.html) Improper Validation of Certificate with Host Mismatch
- [CWE-287:](https://cwe.mitre.org/data/definitions/287.html) Improper Authentication
- [CWE-384:](https://cwe.mitre.org/data/definitions/384.html) Session Fixation

## Related Common Vulnerabilities and Exposures (CVEs)

For specific examples of vulnerabilities related to these CWEs, refer to:

- [CVEs related to CWE-297](https://www.opencve.io/cve?cwe=CWE-297)
- [CVEs related to CWE-287](https://www.opencve.io/cve?cwe=CWE-287)
- [CVEs related to CWE-384](https://www.opencve.io/cve?cwe=CWE-384)

## Prevention Strategies

To mitigate identification and authentication failures, consider implementing:

- Multi-factor authentication
- Strong password policies
- Secure session management
- Proper certificate validation
- Robust credential recovery processes

For detailed prevention strategies, consult the latest OWASP guidelines and industry best practices.

## Example Attack Scenarios

**Scenario #1:** Credential stuffing, the use of lists of known passwords, is a common attack. Suppose an application does not implement automated threat or credential stuffing protection. In that case, the application can be used as a password oracle to determine if the credentials are valid.

**Scenario #2:** Most authentication attacks occur due to the continued use of passwords as a sole factor. Once considered best practices, password rotation and complexity requirements encourage users to use and reuse weak passwords. Organizations are recommended to stop these practices per NIST 800-63 and use multi-factor authentication.

**Scenario #3:** Application session timeouts aren't set correctly. A user uses a public computer to access an application. Instead of selecting "logout," the user simply closes the browser tab and walks away. An attacker uses the same browser an hour later, and the user is still authenticated.

## **Examples of attacker scenarios using juice shop**

- `Password Strength` - Log in with the administrator's user credentials without previously changing them or applying SQL Injection.
- `GDPR Data Erasure` - Log in with Chris' erased user account.
