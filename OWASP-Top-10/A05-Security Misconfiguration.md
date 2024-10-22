# A05-Security Misconfiguration

# Introduction

Security misconfiguration is a critical issue in application security, ranking as the fifth most prevalent risk in the OWASP Top 10. 

The application might be vulnerable if the application is:

- Missing appropriate security hardening across any part of the application stack or improperly configured permissions on cloud services.
- Unnecessary features are enabled or installed (e.g., unnecessary ports, services, pages, accounts, or privileges).
- Default accounts and their passwords are still enabled and unchanged.
- Error handling reveals stack traces or other overly informative error messages to users.
- For upgraded systems, the latest security features are disabled or not configured securely.
- The security settings in the application servers, application frameworks (e.g., Struts, Spring, ASP.NET), libraries, databases, etc., are not set to secure values.
- The server does not send security headers or directives, or they are not set to secure values.
- The software is out of date or vulnerable.

Without a concerted, repeatable application security configuration process, systems are at a higher risk.

## Notable CWEs

Two significant Common Weakness Enumerations associated with this risk are:

- *CWE-16 Configuration*
- *CWE-611 Improper Restriction of XML External Entity Reference*

## Mitigation Strategies

To address security misconfiguration risks, consider the following approaches:

- Implement a repeatable hardening process
- Develop a minimal platform without unnecessary features, components, documentation, or samples
- Review and update configurations of all security notes, updates, and patches as part of the patch management process
- Implement a segmented application architecture providing separation between components
- Send security directives to clients, such as Security Headers
- Automate the process to verify the effectiveness of the configurations in all environments

## Example Attack Scenarios

**Scenario #1:** The application server comes with sample applications not removed from the production server. These sample applications have known security flaws attackers use to compromise the server. Suppose one of these applications is the admin console, and default accounts weren't changed. In that case, the attacker logs in with default passwords and takes over.

**Scenario #2:** Directory listing is not disabled on the server. An attacker discovers they can simply list directories. The attacker finds and downloads the compiled Java classes, which they decompile and reverse engineer to view the code. The attacker then finds a severe access control flaw in the application.

**Scenario #3:** The application server's configuration allows detailed error messages, e.g., stack traces, to be returned to users. This potentially exposes sensitive information or underlying flaws such as component versions that are known to be vulnerable.

**Scenario #4:** A cloud service provider (CSP) has default sharing permissions open to the Internet by other CSP users. This allows sensitive data stored within cloud storage to be accessed.

## **Examples of attacker scenarios using juice shop**

- `Error Handling` - *Provoke an error that is neither very gracefully nor consistently handled.*
- `Deprecated Interface` - *Use a deprecated B2B interface that was not properly shut down.*

## Conclusion

Security misconfiguration poses a significant risk to application security. By understanding its nature and implementing robust mitigation strategies, organizations can substantially reduce their vulnerability to this prevalent threat.
