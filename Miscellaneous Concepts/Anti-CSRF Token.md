# Anti-CSRF Token

An **Anti-CSRF Token** (also known as a **CSRF Token**) is a security measure used to protect web applications from **Cross-Site Request Forgery (CSRF)** attacks. CSRF is a type of attack where a malicious website tricks a user into performing actions on another site (e.g., making a transfer, changing a password, or other sensitive actions) without the user's knowledge or consent. This happens because the victim's browser automatically includes credentials (such as cookies) in requests, even when they are made from an untrusted site.

### How does Anti-CSRF Tokens work?

An Anti-CSRF token works by embedding a unique, random token in requests (usually in a form or in a custom header). This token is validated by the server to ensure that the request is legitimate and originated from the same site where the user is interacting, preventing malicious third-party sites from forging such requests.

### Key Concepts:

1. **Token Generation**: When a user first loads a page that contains sensitive actions (like submitting a form or changing settings), the server generates a unique token and embeds it in the HTML of the page (usually in a hidden form field or a custom header).
2. **Token Submission**: When the user submits the form or sends a request, the token is included with the request (in the body of the form or in an HTTP header, such as `X-CSRF-Token`).
3. **Token Verification**: On the server side, the application checks the token in the incoming request against the one it generated earlier. If the tokens match, the request is processed. If they don't match, the request is rejected, as it might be forged.

### Example Workflow:

1. **Server-Side (Generating the CSRF Token)**:
    - When a user loads a page with a form that performs an action (e.g., submitting a request to change their password), the server generates a CSRF token, which is then embedded in the form as a hidden field or sent as part of the response headers.
    
    Example (in HTML):
    
    ```html
    html
    Copy code
    <form action="/update-password" method="POST">
        <input type="hidden" name="csrf_token" value="unique_token_value">
        <input type="password" name="new_password">
        <input type="submit" value="Change Password">
    </form>
    
    ```
    
2. **Client-Side (Submitting the Form with the Token)**:
    - When the user submits the form, the CSRF token is sent along with the form data.
3. **Server-Side (Validating the Token)**:
    - On the server side, the CSRF token sent by the client is compared with the token stored on the server (usually in the user's session). If they match, the request is considered legitimate.
4. **If the Tokens Don't Match**:
    - If the token is missing or doesn't match, the server should reject the request and potentially send an error or a 403 Forbidden response.

### Example of CSRF Protection with Tokens

Here’s an example using a typical web framework:

### HTML (Frontend):

```html
html
Copy code
<form method="POST" action="/submit-form">
    <input type="hidden" name="csrf_token" value="{{ csrf_token }}">
    <input type="text" name="username">
    <input type="submit" value="Submit">
</form>

```

### Backend (Server-Side Validation in Python/Flask Example):

```python
python
Copy code
from flask import Flask, render_template, request, session, abort
from werkzeug.exceptions import BadRequest

app = Flask(__name__)
app.secret_key = 'a_random_secret_key'

@app.route('/submit-form', methods=['POST'])
def submit_form():
    csrf_token = request.form.get('csrf_token')

    # Check if the CSRF token is valid
    if not csrf_token or csrf_token != session.get('csrf_token'):
        abort(403)  # Forbidden if tokens don't match

    # Process form submission (e.g., save data)
    return "Form submitted successfully!"

@app.route('/form')
def form():
    # Generate a unique CSRF token and store it in the session
    csrf_token = 'unique_token_value'  # Generate securely
    session['csrf_token'] = csrf_token
    return render_template('form.html', csrf_token=csrf_token)

```

In the example:

- The server generates a CSRF token when the page is loaded and stores it in the user session.
- When the form is submitted, the token is included as a hidden field and compared with the one in the session. If they don't match, the request is rejected.

### Benefits of Using Anti-CSRF Tokens:

- **Prevents CSRF Attacks**: It blocks attackers from submitting requests on behalf of the user without their knowledge or consent.
- **User-Specific Protection**: Each token is tied to a user's session, ensuring that it only works for actions that the user explicitly initiates.
- **Stateless Protection**: CSRF tokens are typically stored in the server-side session or as a part of the request, offering a way to protect the application without needing to rely on the same-origin policy of cookies.

### Best Practices:

- **Use Secure Tokens**: Tokens should be cryptographically secure and difficult to guess.
- **Token Expiration**: Tokens should have an expiration time or be invalidated after a short period to reduce the window of opportunity for attacks.
- **Token Rotation**: After each request, the token can be rotated to enhance security.
- **SameSite Cookie Attribute**: Use the `SameSite` attribute in cookies alongside CSRF tokens for additional security against cross-site attacks.

By using Anti-CSRF tokens, you ensure that the application is more resistant to unauthorized, forged requests that could have malicious consequences.
