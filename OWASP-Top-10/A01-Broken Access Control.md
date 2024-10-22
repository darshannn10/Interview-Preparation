# A01-Broken Access Control

A broken access control occurs when users are able to act outside their intended permissions. This type of flaw can have severe consequences for an application's ***security*** and ***data integrity***. Here's a detailed look at this vulnerability:

## Definition

Broken access control refers to a situation where an ***application fails to properly restrict user access*** to certain resources or functionalities, allowing users to perform actions they shouldn't be authorized to do.

## Common Causes

Broken access control can occur due to various reasons, including:

- Improper implementation of access control checks
- Relying solely on [client-side access control](https://www.notion.so/Server-Side-Access-Control-vs-Client-Side-Access-Control-11f21d4fb40d806b8f4ff47fdc3a44c1?pvs=21)
- [Insecure direct object references (IDORs)](https://www.notion.so/Insecure-Direct-Object-References-IDOR-11f21d4fb40d808ebecbf376a33de5a0?pvs=21)
- Failure to enforce re-authentication for sensitive operations

## Consequences

The failures 

- Unauthorized modification of data
- Unauthorized destruction of data
- Performance of business functions outside the user's intended limits

## Impact on Organizations

The impact of broken access control can be significant, potentially leading to:

- Data breaches
- Reputational damage
- Financial losses
- Legal and regulatory consequences

## Prevention Strategies

To prevent broken access control vulnerabilities, developers should:

- Implement proper [server-side access controls](https://www.notion.so/Server-Side-Access-Control-vs-Client-Side-Access-Control-11f21d4fb40d806b8f4ff47fdc3a44c1?pvs=21)
- Use the principle of least privilege
- Implement robust authentication and session management
- Regularly audit and test access control mechanisms

More info in OWASP's [Authorization cheat sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)

## **CWEs**

Notable Common Weakness Enumerations (CWEs):

- [CWE-200:](https://cwe.mitre.org/data/definitions/200.html) Exposure of Sensitive Information to an Unauthorized Actor
- [CWE-201:](https://cwe.mitre.org/data/definitions/201.html) Exposure of Sensitive Information Through Sent Data
- [CWE-352:](https://cwe.mitre.org/data/definitions/352.html) Cross-Site Request Forgery

## **CVEs**

Examples of CVEs :

- [200](https://www.opencve.io/cve?cwe=CWE-200)
- [201](https://www.opencve.io/cve?cwe=CWE-201)
- [352](https://www.opencve.io/cve?cwe=CWE-352)

## Example Attack Scenarios

**Scenario #1:** The application uses unverified data in a SQL call that is accessing account information:

```
 pstmt.setString(1, request.getParameter("acct"));
 ResultSet results = pstmt.executeQuery( );
```

An attacker simply modifies the browser's 'acct' parameter to send whatever account number they want. If not correctly verified, the attacker can access any user's account.

```
 https://example.com/app/accountInfo?acct=notmyacct
```

**Scenario #2:** An attacker simply forces browses to target URLs. Admin rights are required for access to the admin page.

```
 https://example.com/app/getappInfo
 https://example.com/app/admin_getappInfo
```

If an unauthenticated user can access either page, it's a flaw. If a non-admin can access the admin page, this is a flaw.

## **Examples of attacker scenarios using juice shop**

- **`Login as admin`** - Log in with the administrator's user account
- **`Admin Section`** - Access the administration section of the juice store
- **`View Basket`** - View another user's shopping basket

Understanding and addressing broken access control is crucial for maintaining the security and integrity of applications and protecting sensitive data from unauthorized access or manipulation.
