# SOP v/s CORS v/s CSP

### 1. **Same-Origin Policy (SOP)**

**Definition**: The Same-Origin Policy is a security mechanism implemented by browsers to restrict how a document or script loaded from one origin can interact with resources from another origin.

- **Origin** is defined as a combination of the protocol (e.g., `http` or `https`), domain (e.g., `example.com`), and port (e.g., `:80`).
- **Purpose**: SOP prevents malicious websites from reading sensitive data from other sites a user is logged into (like social media accounts or banking sites). It essentially limits how scripts from one site can access data from another.
- **Example**: If a website `example.com` tries to make a request (e.g., AJAX or fetch) to `anotherdomain.com`, the browser will block this request by default due to SOP, unless explicitly allowed.

---

### 2. **Cross-Origin Resource Sharing (CORS)**

**Definition**: CORS is a protocol that allows servers to specify who can access their resources from different origins. It is a mechanism that allows controlled access to resources on a web server from a different domain than the one the browser is currently on.

- **Purpose**: CORS provides a way for servers to relax the SOP policy by allowing cross-origin requests under certain conditions.
- **How it works**:
    - When a request is made from one domain to another, the browser sends a **preflight request** (for methods like `PUT` or `DELETE`) to check if the server allows it.
    - The server responds with headers (like `Access-Control-Allow-Origin`) indicating which origins are allowed to access the resource.
- **Example**: If a web app on `example.com` needs to fetch data from an API on `api.example.com`, the API server must send an `Access-Control-Allow-Origin: *` or a more specific domain header to allow the request from `example.com`.

---

### 3. **Content Security Policy (CSP)**

**Definition**: CSP is a security feature that helps prevent a variety of attacks, including Cross-Site Scripting (XSS) and data injection attacks, by controlling which content is allowed to load on a web page.

- **Purpose**: CSP helps prevent malicious code (like JavaScript) from being executed by defining which domains are allowed to load specific types of resources (e.g., scripts, images, stylesheets).
- **How it works**:
    - You define a CSP in the HTTP headers or `<meta>` tags in your HTML to specify the sources from which resources can be loaded.
    - It can restrict which scripts can execute, which resources can load, and which URLs can be navigated to, among other things.
- **Example**: A CSP rule might look like:
    
    ```http
    Content-Security-Policy: default-src 'self'; script-src 'self' https://apis.example.com;
    ```
    
    This policy restricts resources to load only from the same origin (`'self'`) and from the trusted script domain `apis.example.com`.
    

---

### Key Differences and Use Cases:

| Concept | Purpose | Example Use Case |
| --- | --- | --- |
| **SOP** | Prevents cross-origin access by default. | Prevents one website from stealing data from another. |
| **CORS** | Allows servers to opt-in and allow specific cross-origin requests. | A web app making API requests to a different domain. |
| **CSP** | Limits the sources from which resources (scripts, images, etc.) can be loaded to prevent attacks like XSS. | Restricting which scripts or content can load on your website. |

---

### Summary:

- **SOP** is the foundational rule in browsers that restricts cross-origin requests by default.
- **CORS** is a way for a server to explicitly allow cross-origin requests.
- **CSP** is a policy to mitigate the risks of malicious content loading on a website by defining trusted sources.
