# A08-**Software and Data Integrity Failures**

Software and data integrity failures occur when code and infrastructure do not adequately protect against integrity violations. This category of vulnerabilities can lead to serious security risks in applications and systems.

## Key Failures:

- **Untrusted Sources**: Applications relying on plugins, libraries, or modules from untrusted sources, repositories, and content delivery networks (CDNs).
- **Insecure CI/CD Pipelines**: Potential for unauthorized access, malicious code injection, or system compromise due to inadequate security measures in the development and deployment process.
- **Auto-Update Vulnerabilities**: Applications with auto-update functionality that download and apply updates without sufficient integrity verification.
- **Insecure Deserialization**: Vulnerabilities arising from objects or data encoded or serialized into a structure that attackers can modify.

## Notable Common Weakness Enumerations (CWEs)

- [CWE-829:](https://cwe.mitre.org/data/definitions/829.html) Inclusion of Functionality from Untrusted Control Sphere
- [CWE-494:](https://cwe.mitre.org/data/definitions/494.html) Download of Code Without Integrity Check
- [CWE-502:](https://cwe.mitre.org/data/definitions/502.html) Deserialization of Untrusted Data

## Related Common Vulnerabilities and Exposures (CVEs)

For specific examples of vulnerabilities related to these CWEs, refer to:

- [CVEs related to CWE-829](https://www.opencve.io/cve?cwe=CWE-829)
- [CVEs related to CWE-494](https://www.opencve.io/cve?cwe=CWE-494)
- [CVEs related to CWE-502](https://www.opencve.io/cve?cwe=CWE-502)

## Primary Defense Strategies

- Implement digital signatures or similar mechanisms to verify software or data integrity.
- Use trusted repositories for libraries and dependencies.
- Employ software supply chain security tools like OWASP Dependency Check or OWASP CycloneDX.
- Establish a thorough review process for code and configuration changes.
- Ensure proper segregation, configuration, and access control in CI/CD pipelines.
- Implement integrity checks or digital signatures for unsigned or unencrypted serialized data sent to untrusted clients.

## Example Attack Scenarios

**Scenario #1:** An attacker uploads a malicious update to a widely-used library hosted on a public repository. Applications that automatically update from this repository without proper integrity checks incorporate the malicious code, potentially compromising numerous systems.

**Scenario #2:** A developer unknowingly includes a library from an untrusted source in their application. This library contains malicious code that can exfiltrate sensitive data from the application's users.

**Scenario #3:** An application uses insecure deserialization of user-supplied data. An attacker exploits this by crafting malicious serialized objects, which, when deserialized by the application, execute arbitrary code on the server.

## Conclusion

Software and data integrity failures represent a significant risk to application security. By implementing robust integrity checks, securing the software supply chain, and following best practices in development and deployment processes, organizations can significantly reduce their vulnerability to these types of attacks.
