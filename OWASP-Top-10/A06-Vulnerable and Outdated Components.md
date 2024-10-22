# A06-Vulnerable and Outdated Components

# Introduction

Vulnerable and outdated components pose a significant risk to application security. This category is unique in the OWASP Top 10 as it's challenging to test and assess risk, and it's the only category without mapped Common Vulnerability and Exposures (CVEs).

## You are likely vulnerable:

- If you do not know the versions of all components you use (both client-side and server-side). This includes components you directly use as well as nested dependencies.
- If the software is vulnerable, unsupported, or out of date. This includes the OS, web/application server, database management system (DBMS), applications, APIs and all components, runtime environments, and libraries.
- If you do not scan for vulnerabilities regularly and subscribe to security bulletins related to the components you use.
- If you do not fix or upgrade the underlying platform, frameworks, and dependencies in a risk-based, timely fashion. This commonly happens in environments when patching is a monthly or quarterly task under change control, leaving organizations open to days or months of unnecessary exposure to fixed vulnerabilities.
- If software developers do not test the compatibility of updated, upgraded, or patched libraries.
- If you do not secure the components’ configurations (see [A05:2021-Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)).

## Common Weakness Enumeration (CWE)

The notable CWE associated with this category is:

- [CWE-1104: Use of unmaintained third-party components](https://cwe.mitre.org/data/definitions/1104.html)

## Common Vulnerabilities and Exposures (CVEs)

Interestingly, there are no CVEs directly related to CWE-1104. This absence of specific vulnerabilities highlights the unique nature of this security risk, emphasizing the importance of proactive component management and regular updates.

## Mitigation Strategies

To address the risks associated with vulnerable and outdated components, consider the following strategies:

- Implement a patch management process to remove unused dependencies, unnecessary features, components, files, and documentation.
- Continuously inventory versions of both client-side and server-side components and their dependencies.
- Monitor sources like CVE and NVD for vulnerabilities in your components. Use software composition analysis tools to automate the process.
- Only obtain components from official sources over secure links. Prefer signed packages to reduce the risk of including a modified, malicious component.
- Monitor for libraries and components that are unmaintained or do not create security patches for older versions.
- If patching is not possible, consider deploying a virtual patch to monitor, detect, or protect against the discovered issue.

## Example Attack Scenarios

**Scenario #1:** Components typically run with the same privileges as the application itself, so flaws in any component can result in serious impact. Such flaws can be accidental (e.g., coding error) or intentional (e.g., a backdoor in a component). Some example exploitable component vulnerabilities discovered are:

- CVE-2017-5638, a Struts 2 remote code execution vulnerability that enables the execution of arbitrary code on the server, has been blamed for significant breaches.
- While the internet of things (IoT) is frequently difficult or impossible to patch, the importance of patching them can be great (e.g., biomedical devices).

## **Examples of attacker scenarios using juice shop**

Typically scenario:

- Components run with the same privileges as the application itself, so flaws in any component can result in serious impact. Such flaws can be accidental (e.g., coding error) or intentional (e.g., a backdoor in a component).

Juice-Shop:

- `Vulnerable Library` - Inform the shop about a vulnerable library it is using. Mention the exact library name and version in your comment.

## Conclusion

Managing vulnerable and outdated components is crucial for maintaining a robust security posture. By adopting a proactive approach to component management, regular updates, and continuous monitoring, organizations can significantly reduce their exposure to this pre
