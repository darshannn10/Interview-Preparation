# A10-Server Side Request Forgery (SSRF)

# Server Side Request Forgery (SSRF)

Server Side Request Forgery (SSRF) is a web security vulnerability that allows an attacker to induce the server-side application to make requests to an unintended location. This vulnerability occurs when a web application is fetching a remote resource without properly validating the user-supplied URL.

## Overview

SSRF flaws enable attackers to manipulate a vulnerable web application into sending crafted requests to unexpected destinations, even when those destinations are protected by firewalls, VPNs, or other network access controls. The increasing prevalence of SSRF vulnerabilities is partly due to the growing complexity of modern web applications and the widespread use of cloud services.

## Key Characteristics

- Allows attackers to bypass network security measures
- Can lead to data exposure, internal network scanning, and further attacks
- Often exploits trust relationships between servers
- Severity is amplified in cloud environments

## Prevention Strategies

### Network Layer Defenses

- Segment remote resource access functionality in separate networks
- Implement "deny by default" firewall policies
- Establish ownership and lifecycle for firewall rules
- Log all accepted and blocked network flows on firewalls

### Application Layer Defenses

- Sanitize and validate all client-supplied input data
- Enforce URL schema, port, and destination with a positive allow list
- Avoid sending raw responses to clients
- Disable HTTP redirections
- Be aware of URL consistency to prevent DNS rebinding and TOCTOU race conditions

Note: Avoid using deny lists or regular expressions for SSRF mitigation, as attackers can often bypass these measures.

### Additional Measures

- Avoid deploying security-relevant services on front-end systems
- Control local traffic on front-end systems
- Consider using network encryption (e.g., VPNs) for high-protection needs

## Example Attack Scenarios

Attackers can use SSRF to attack systems protected behind web application firewalls, firewalls, or network ACLs, using scenarios such as:

**Scenario #1:** Port scan internal servers – If the network architecture is unsegmented, attackers can map out internal networks and determine if ports are open or closed on internal servers from connection results or elapsed time to connect or reject SSRF payload connections.

**Scenario #2:** Sensitive data exposure – Attackers can access local files or internal services to gain sensitive information such as `file:///etc/passwd` and `http://localhost:28017/`.

**Scenario #3:** Access metadata storage of cloud services – Most cloud providers have metadata storage such as `http://169.254.169.254/`. An attacker can read the metadata to gain sensitive information.

**Scenario #4:** Compromise internal services – The attacker can abuse internal services to conduct further attacks such as Remote Code Execution (RCE) or Denial of Service (DoS).

## **Examples of attacker scenarios using juice shop**

- `Server-side XSS Protection` - Perform a persisted XSS attack with `<iframe src="javascript:alert(`xss`)">` bypassing a server-side security mechanism.
- **DOM XSS** - Perform a *DOM* XSS attack with <iframe src="javascript:alert(`xss`)">
    - **Client-side XSS Protection (XSS)** - Perform a *persisted* XSS attack with <iframe src="javascript:alert(`xss`)"> bypassing a client-side security mechanism
        - Hint: Register a user - Resend feature in Firefox
        - /#/administration portal from previous challenge list all users

## Conclusion

SSRF represents a significant threat to web application security, particularly in complex and cloud-based environments. By implementing a combination of network and application-layer defenses, organizations can significantly reduce their vulnerability to SSRF attacks. Continuous monitoring, regular security assessments, and staying informed about emerging SSRF techniques are crucial for maintaining robust protection against this evolving threat.
