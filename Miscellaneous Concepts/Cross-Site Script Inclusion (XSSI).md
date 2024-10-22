# Cross-Site Script Inclusion (XSSI)

**Cross-Site Script Inclusion (XSSI)** is a type of web attack where an attacker tries to steal sensitive data by tricking a user’s browser into loading a script (typically a JavaScript file) from another site into the attacker's website. XSSI takes advantage of the fact that browsers don't enforce the **Same-Origin Policy (SOP)** on static resources like JavaScript files in the same way they do for other types of resources (e.g., AJAX requests).

In an **XSSI attack**, the attacker includes a script from a vulnerable site (which might contain sensitive data) into their own web page and attempts to steal the data that the script exposes.

### Key Points of XSSI:

1. **Inclusion of Scripts**: The attacker’s website includes or references a script (e.g., a `.js` file) from the target domain, such as:
    
    ```html
    <script src="https://victim-website.com/api/data"></script>
    ```
    
    This script may return sensitive data (like user details or other information) in JavaScript format.
    
2. **Accessing the Data**: If the vulnerable website doesn’t protect its data properly, the attacker can trick the browser into loading the sensitive information in the form of JavaScript. While the attacker cannot access the response directly (due to SOP), the script might unintentionally expose data in a way that can be extracted through other means (such as examining the script's content in the browser or using callbacks).

### Difference Between XSSI and XSS

- **XSSI**: Involves the inclusion of JavaScript from a trusted domain to steal data. It's more about how static resources like scripts are served and how their data is exposed.
- **XSS (Cross-Site Scripting)**: Involves injecting malicious scripts directly into a trusted website to execute code in the victim's browser.

### Example Scenario of an XSSI Attack:

Imagine a website, `example.com`, has a script file at `example.com/api/user_data.js` that returns sensitive information like this:

```jsx
var userData = {
  name: "John Doe",
  email: "john@example.com"
};

```

If the script is included on another site (the attacker's site), the attacker could gain access to the user's name and email, even though SOP would prevent direct access to the server response.

### How **SameSite Cookies** Help:

SameSite cookies can help protect against XSSI by ensuring that sensitive data or session information is not automatically sent with cross-origin script requests. If the cookies (like session cookies or authentication tokens) are restricted using `SameSite=Lax` or `SameSite=Strict`, the browser won’t send them with the cross-site script inclusion, making it harder for attackers to exploit this vulnerability. However, **SameSite cookies are just one part of the defense**, and additional steps (like using proper CORS headers and avoiding exposing sensitive data in JavaScript files) should be taken.

### Mitigation Strategies for XSSI:

1. **Avoid Serving Sensitive Data in Scripts**: Keep sensitive data out of JavaScript files that can be included by other websites. Use proper APIs (e.g., JSON served through AJAX) with appropriate access controls.
2. **CORS (Cross-Origin Resource Sharing)**: Implement CORS headers to ensure that sensitive data is not served to unauthorized origins.
3. **SameSite Cookies**: Use the `SameSite` attribute to limit when cookies are sent with cross-origin requests.
4. **Content-Type Headers**: Set appropriate `Content-Type` headers (`application/json` for JSON data rather than `application/javascript`) to prevent browsers from interpreting the response as executable JavaScript.

By controlling how scripts and data are shared across origins and securing cookies with attributes like **SameSite**, the risk of XSSI attacks can be significantly reduced.
