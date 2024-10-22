# A03-**Injection**

Injection vulnerabilities, once the top concern in web application security, have now been ranked third in the OWASP Top 10 2021 list. Despite this shift, injection attacks remain a significant threat, with widespread impact across tested applications.

## Prevalence and Impact

According to the 2021 OWASP report:

- 94% of applications were tested for some form of injection
- Maximum incidence rate: 19%
- Average incidence rate: 3%
- Total occurrences: 274,000

## Vulnerability Factors

An application becomes vulnerable to injection attacks when:

- User-supplied data is not properly validated, filtered, or sanitized
- Dynamic queries or non-parameterized calls without context-aware escaping are used directly in the interpreter
- Hostile data is used within object-relational mapping (ORM) search parameters to extract additional, sensitive records
- Malicious data is directly used or concatenated in dynamic queries, commands, or stored procedures

## Common Weakness Enumerations (CWEs)

Notable CWEs associated with injection vulnerabilities include:

- [CWE-79: Cross-site Scripting](https://cwe.mitre.org/data/definitions/79.html)
- [CWE-89: SQL Injection](https://cwe.mitre.org/data/definitions/89.html)
- [CWE-73: External Control of File Name or Path](https://cwe.mitre.org/data/definitions/73.html)

These are just a few examples, as there are many more CWEs related to injection vulnerabilities.

## Common Vulnerabilities and Exposures (CVEs)

Examples of CVEs related to injection vulnerabilities can be found at:

- [CWE-20 related CVEs](https://www.opencve.io/cve?cwe=CWE-20)
- [CWE-74 related CVEs](https://www.opencve.io/cve?cwe=CWE-74)
- [CWE-75 related CVEs](https://www.opencve.io/cve?cwe=CWE-75)

## Prevention Strategies

To mitigate injection vulnerabilities, consider implementing the following strategies:

- Use parameterized queries or prepared statements
- Implement proper input validation and sanitization
- Utilize Object-Relational Mapping (ORM) tools
- Apply the principle of least privilege
- Regularly update and patch systems

## **Primary defenses**

OWASP's Injection prevention - [injection prevent rules](https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html#injection-prevention-rules) :

- Rule #1 (Perform proper input validation)
- Rule #2 (Use a safe API)
- Rule #3 (Contextually escape user data)

## Other relevant cheat sheets:

- [OWASP's Injection prevention](https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html)
- [OWASP's Injection prevention in Java](https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet_in_Java.html)
- [OWASP's Query parameterization](https://cheatsheetseries.owasp.org/cheatsheets/Query_Parameterization_Cheat_Sheet.html)

## Example Attack Scenarios

**Scenario #1:** An application uses untrusted data in the construction of the following vulnerable SQL call:

```python
String query = "SELECT \* FROM accounts WHERE custID='" + request.getParameter("id") + "'";
```

**Scenario #2:** Similarly, an application’s blind trust in frameworks may result in queries that are still vulnerable, (e.g., Hibernate Query Language (HQL)):

```python
Query SQLQuery = session.createQuery("FROM accounts WHERE custID='" + request.getParameter("id") + "'");
```

In both cases, the attacker modifies the ‘id’ parameter value in their browser to send: ' UNION SLEEP(10);--. For example:

```python
 http://example.com/app/accountView?id=' UNION SELECT SLEEP(10);--
```

This changes the meaning of both queries to return all the records from the accounts table. More dangerous attacks could modify or delete data or even invoke stored procedures.

## **Examples of attacker scenarios using juice shop**

- **`Login Bender`** - Log in with Bender's user account
    - Use domain name and user name - (find domain name in application-configuration)
    - You are familiar with the vulnerability in the e-mail field
- **`Login Jim`** - Log in with Jim's user account.
    - Hint injection vulnerability in the search box
    - A user table named User with columns id, email, password exist
- `Expired coupon` - Successfully redeem an expired campaign coupon code
- `Payback time` - Place an order that makes you rich
