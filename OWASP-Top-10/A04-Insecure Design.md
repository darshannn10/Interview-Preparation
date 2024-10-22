# A04-Insecure Design

Insecure design is a critical category in the OWASP Top 10 for 2021, focusing on risks related to design and architectural flaws in software development. This category emphasizes the importance of pre-code activities and the principles of Secure by Design, moving beyond the traditional "shift-left" approach in coding.

## Definition and Scope

Insecure design represents a broad category of weaknesses characterized by "**missing or ineffective control design**." It's crucial to understand that an insecure design cannot be remedied by perfect implementation alone, as the necessary security controls were never established to defend against specific attacks.

## Factors Contributing to Insecure Design

- Lack of business risk profiling in software or system development
- Failure to determine the appropriate level of security design required
- Insufficient threat modeling during the design phase
- Inadequate use of secure design patterns and reference architectures

# Key Components of Secure Software Development

To address insecure design, the following elements are essential:

- Secure Development Lifecycle (SDL)
- Secure design patterns
- Paved road methodology
- Secured component library
- Appropriate tooling
- Comprehensive threat modeling

# Notable Common Weakness Enumerations (CWEs)

Several CWEs are associated with insecure design:

- [CWE-209:](https://cwe.mitre.org/data/definitions/209.html) Generation of Error Message Containing Sensitive Information
- [CWE-256:](https://cwe.mitre.org/data/definitions/256.html) Unprotected Storage of Credentials
- [CWE-501:](https://cwe.mitre.org/data/definitions/501.html) Trust Boundary Violation
- [CWE-522:](https://cwe.mitre.org/data/definitions/522.html) Insufficiently Protected Credentials

# Related Common Vulnerabilities and Exposures (CVEs)

For specific examples of vulnerabilities related to insecure design, refer to the following CVE lists:

- [CVEs related to CWE-209](https://www.opencve.io/cve?cwe=CWE-209)
- [CVEs related to CWE-256](https://www.opencve.io/cve?cwe=CWE-256)
- [CVEs related to CWE-501](https://www.opencve.io/cve?cwe=CWE-501)
- [CVEs related to CWE-522](https://www.opencve.io/cve?cwe=CWE-522)

# Best Practices for Mitigating Insecure Design

- Implement a comprehensive threat modeling process
- Integrate security considerations early in the software development lifecycle
- Utilize secure design patterns and reference architectures
- Conduct regular security assessments and penetration testing
- Provide ongoing security training for development teams
- Establish and maintain a secure coding standard

## Example Attack Scenarios

**Scenario #1:** A credential recovery workflow might include “questions and answers,” which is prohibited by NIST 800-63b, the OWASP ASVS, and the OWASP Top 10. Questions and answers cannot be trusted as evidence of identity as more than one person can know the answers, which is why they are prohibited. Such code should be removed and replaced with a more secure design.

**Scenario #2:** A cinema chain allows group booking discounts and has a maximum of fifteen attendees before requiring a deposit. Attackers could threat model this flow and test if they could book six hundred seats and all cinemas at once in a few requests, causing a massive loss of income.

**Scenario #3:** A retail chain’s e-commerce website does not have protection against bots run by scalpers buying high-end video cards to resell auction websites. This creates terrible publicity for the video card makers and retail chain owners and enduring bad blood with enthusiasts who cannot obtain these cards at any price. Careful anti-bot design and domain logic rules, such as purchases made within a few seconds of availability, might identify inauthentic purchases and rejected such transactions.

# Conclusion

Addressing insecure design is crucial for developing robust and secure software systems. By focusing on pre-code activities, implementing secure design principles, and utilizing appropriate tools and methodologies, organizations can significantly reduce the risks associated with insecure design and enhance their overall security posture.
