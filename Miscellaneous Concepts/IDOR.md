# **Insecure Direct Object References(IDOR)**

## **What are insecure direct object references (IDOR)?**

Insecure direct object references (IDOR) are a type of access control vulnerability that arises when an application uses user-supplied input to access objects directly. IDOR vulnerabilities are most commonly associated with horizontal privilege escalation, but they can also arise in relation to vertical privilege escalation.

## **IDOR examples**

There are many examples of access control vulnerabilities where user-controlled parameter values are used to access resources or functions directly.

### **IDOR vulnerability with direct reference to database objects**

Consider a website that uses the following URL to access the customer account page, by retrieving information from the back-end database:

```
https://insecure-website.com/customer_account?customer_number=132355
```

Here, the customer number is used directly as a record index in queries that are performed on the back-end database. If no other controls are in place, an attacker can simply modify the `customer_number` value, bypassing access controls to view the records of other customers. This is an example of an IDOR vulnerability leading to horizontal privilege escalation.

An attacker might be able to perform horizontal and vertical privilege escalation by altering the user to one with additional privileges while bypassing access controls. Other possibilities include exploiting password leakage or modifying parameters once the attacker has landed in the user's accounts page, for example.

### **IDOR vulnerability with direct reference to static files**

IDOR vulnerabilities often arise when sensitive resources are located in static files on the server-side filesystem. For example, a website might save chat message transcripts to disk using an incrementing filename, and allow users to retrieve these by visiting a URL like the following:

```
https://insecure-website.com/static/12144.txt
```

In this situation, an attacker can simply modify the filename to retrieve a transcript created by another user and potentially obtain user credentials and other sensitive data.

## **Mitigation**

To mitigate IDOR vulnerabilities, consider implementing the following strategies:

- **Implement proper access control checks:** For each object that users try to access, ensure robust access control checks are in place. Many web frameworks provide built-in mechanisms to facilitate this.
- **Use complex identifiers:** As a defense-in-depth measure, use complex, non-sequential identifiers instead of simple, predictable ones. However, remember that this is not a substitute for proper access control.
- **Avoid exposing identifiers:** When possible, avoid exposing identifiers in URLs and POST bodies. Instead, determine the currently authenticated user from session information.
- **Use session-based identifiers:** In multi-step flows, pass identifiers in the session to prevent tampering.
- **Implement object-level access control:** When looking up objects based on primary keys, use datasets that users have access to. For example, in Ruby on Rails:

```ruby
# Vulnerable, searches all projects
@project = Project.find(params[:id])

# Secure, searches projects related to the current user
@project = @current_user.projects.find(params[:id])
```

- **Verify permissions consistently:** Check the user's permission every time an access attempt is made. Implement this structurally using the recommended approach for your web framework.
- **Use UUIDs or random values:** As an additional defense-in-depth measure, consider using UUIDs or other long random values as primary keys instead of sequential numeric identifiers.

Remember, while these mitigation strategies can significantly reduce the risk of IDOR vulnerabilities, it's crucial to implement a comprehensive security approach that includes regular security audits and penetration testing.
