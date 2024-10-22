# Host Header Injection

### Host Header :

Host Header is a standard HTTP header field that is used to specify the domain name of the website that a user is trying to access. The host header is used by the web server to determine which website to show the user. 

### Host Header Injection Vulnerability :

An HTTP Host Header attack is a type of attack where the attacker sends a request to a server with fake host header. This can be used to trick the server from thinking that the request is coming from a different domain or to redirect the request to a different website.

The HTTP Host header is a mandatory request header as of `HTTP/1.1`. It specifies the domain name that the client wants to access. For example, when a user visits [PortSwigger's website](https://portswigger.net/web-security), their browser will compose a request containing a Host header as follows:

```html
GET /web-security HTTP/1.1 Host: [portswigger.net](http://portswigger.net/)
```

In some cases, such as when the request has been forwarded by an intermediary system, the Host value may be altered before it reaches the intended back-end component 

### Consequences of Host Header Vulnerability :

1. `Domain Spoofing` : By manipulating the host header an attacker can make the webserver believe that the request is coming from a different domain than it actually is. 
2. `Cross Site Scripting (XSS)` : If an application is vulnerable, an attacker can inject a malicious host header that includes a script that can steals user credentials or perform other malicious act. 
3. `Request Smuggling` : Host header injection can also be used in conjunction (added up) with other vulnerability.
4. `SQL Injection` : Every HTTP header is a potential vector for exploiting classic server-side vulnerabilities, the Host header is no exception. For example, you should try the usual SQL injection probing techniques via the Host header. If the value of the header is passed into a SQL statement, this could be exploitable.
5. `Web Cache Poisoning` : Manipulating caching systems into storing a page generated with a malicious Host and serving it to others.
6. `Password Reset Poisoning` : Exploiting password reset emails and tricking them to deliver poisoned content directly to the target.
7. `Cross Site Scripting` : XSS can be performed, if the value of Host header is used for writing links without HTML-encoding. For example Joomla used to write Host header to every page without HTML Encoding like this: `<link href=”http://_SERVER['HOST']”>` which led to cross site scripting
