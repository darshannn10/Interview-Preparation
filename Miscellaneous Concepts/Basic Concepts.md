### What are cookies on websites?
- Cookies are small files of information that a web server generates and sends to a web browser. Web browsers store the cookies they receive for a predetermined period of time, or for the length of a user's session on a website. They attach the relevant cookies for any future requests the user makes to the web server. Cookies help to inform websites about the user, enabling the websites to personalize the user experience. For example, ecommerce websites use cookies to know what merchandise users have placed in their shopping carts. In addition, some cookies are necessary for security purposes, such as authentication cookies (see below). Let say you visit a website which is not in your local language (let’s say English). You choose the English option in the language section of the website. Now if you visit the same website 5 times a day, you might have to change the language 5 times. Therefore, this information is saved as a cookie in your system. So the next time you send the request, the server will know that you want to see the website in English. The cookies that are used on the Internet are also called "HTTP cookies."

### Session
A session is the total time devoted to an activity. In computer systems, a user session begins when a user logs in to or accesses a particular computer, network, or software service. It ends when the user logs out of the service, or shuts down the computer. A session can temporarily store information related to the activities of the user while connected. A session cookie is used in web pages for storing information in case the user leaves the web page or closes down their Internet browser. For example, this is one way a website can remember what is in your shopping cart if you leave and come back.

### Difference Between Session and Cookies :

	
|               Cookie	                                                       | Session                                                 | 
| -------------                                                                |:-------------:| 
| Cookies are client-side files on a local computer that hold user information.| 	Sessions are server-side files that contain user data.| 
| Cookies end on the lifetime set by the user.                                 | 	When the user quits the browser or logs out of the programmed, the session is over.
| It can only store a certain amount of info.	                                 |  It can hold an indefinite quantity of data. |
| The browser’s cookies have a maximum capacity of 4 KB.	                     |We can keep as much data as we like within a session, however there is a maximum memory restriction of 128 MB that a script may consume at one time.
| Because cookies are kept on the local computer, we don’t need to run a function to start them.	|To begin the session, we must use the session start() method.
| Cookies are not secured.	|Session are more secured compare than cookies.|
| Cookies stored data in text file.	|Session save data in encrypted form.|
| Cookies stored on a limited data.	|Session stored a unlimited data.|

### What is HTTP Security Header?
- Basically, an HTTP security header is a set of commands or directives that are being exchanged between your web browser (or any web client) and a webserver to specify the security-related details of HTTP communication. These exchanges or sharing of information are part of the HTTP protocol. These commands or directives let your browser know what is allowed to show or whatnot, for your website, to ensure its security and no malware injection.

### Why do You Need to Implement HTPP Security Header?
- There have been multiple articles and reports circulating on the internet about the peak rise in cyber-attacks and data breaching cases in past recent years. And one of the main culprits of all these mishaps happening is poor security measures and misconfigurations. These HTTP security headers help to stop some of the most common hacker attacks, malware injections, clickjacking, malicious scrip injection, etc. They provide an extra layer of protection by restricting some activities between the server and the web browser, while the web application is running.

Most Important HTTP Security Header List
Let us check out some of the most important HTTP security headers you must implement on your web applications to enhance security and enable an extra layer of protection.

1. `X-Frame Options` : For the first time, Microsoft has introduced the X-Frame Options in their Microsoft internet explorer, which helps to protect against malicious script injection or cross-site scripting attacks. This HTTP security header protects your website iFrames by instructing browsers to ask whether to process iFrame to the website or not. It mainly protects from all clickjacking attacks in which an attacker implements multiple layers on a link or button to redirect users to another page and steal their vital information.
2. `Strict-Transport-Security` :  Strict-Transport-Security or HTTPS Strict Transport Security header helps to protect from MIM attacks and cookie hijacking when enabled. This directive enforces the browser to use HTTPS rather than HTTP communication. Let us understand how it works if you are running any website on HTTP and migrated to it on HTTPS. Your old visitors will still try to access the old URL with HTTP. Since you have already migrated your website to HTTPS, the old URL will redirect it to the new one. But the point is, your visitors can still able to access the non-encrypted version of your website before redirecting to the new encrypted URL. In between the process, the hackers get an opportunity to do MIM or Man in the middle attacks. But when you enable Strict-Transport-Security, the browser will get instructions to not load HTTP websites rather enforce the browser to communicate over HTTPS.
3. `Content Security Policy` : This HTTP security Header instructs the browser to load only those contents that are mentioned in the policy. It means you will have the power to control the resources of your website and allow browsers to load only content resources that you have whitelisted. It helps browsers to decide from where to load content resources such as scripts, images, or CSS. If you can implement this HTTP security header successfully it will protect your website from Clickjacking, Cross-Site Scripting (XSS), and any malicious code injection. Although it doesn’t 100% guarantee protection, it helps to prevent and limit possible damages.Even, the majority of browsers are now identifying this serious issue and started supporting it.
4. `X-content-Type-Options` : This type of header lets you restrict or prevent MIME type sniffing by telling the browser that MIME types are deliberately configured on the server. Basically, in MIME sniffing, it provides an opportunity for the attackers to inject any executable malicious script.  This header was introduced in the Internet Explorer 8 of Microsoft For example, an attacker has injected any malicious resource that has changed the response of an innocent other resource say images. Due to MIME sniffing, the browser will stop rendering the image content type rather than start executing the malicious resources that have been injected. When you enable this header, it will entrust and force the browser to follow only the MIME types that have been specified in Content-type headers. This way you can easily protect and prevent malicious script injection or cross-site scripting attacks.
5. `Referrer Policy` :This header security will allow you to control whether the referrer information should be revealed? If yes then by how much. However, for other requests, the browser will share only information about the origin. Syntax to follow:
  
|1|Referrer-Policy: origin-when-cross-origin|
| ------------- |:-------------:|
|2|Referrer-Policy: no-referrer-when-downgrade|

Instruction explanation: origin-when-cross-origin: The browser will share complete referral information for same-origin requests and other requests, the browser will share only about the origin. no-referrer-when-downgrade: The browser will not share referral information when sending the Referrer header for requests to less secure destinations.

6. `Feature or Permissions-Policy` : This security header lets a website decide whether or not to provide access to any particular feature or API on the browser. With the help of this header, you can easily control the functionality of any application on your browser, that can malign your privacy and allow only if you find it legit and necessary. For example, if you do not want the website to access your microphone, webcam, or location and want to restrict their functionality.
7. `X-Permitted Cross Domain` : With the help of this HTTP security Header, you can give instructions to the browser and have control over all the requests that come from cross-domain. When you enable this header, you will be limiting your website to load unnecessary website assets that come from other domains. So that website resources can be used efficiently. This security header is optional and it is not necessary to have them, but it is good to install them and enable them.

## CIA Triad
When talking about network security, the CIA triad is one of the most important models which is designed to guide policies for information security within an organization.  CIA stands for :
1.	Confidentiality
2.	Integrity
3.	Availability

### Confidentiality
Confidentiality means that only authorized individuals/systems can view sensitive or classified information. The data being sent over the network should not be accessed by unauthorized individuals.

### Integrity
Integrity means the data transmitted, processed, and stored has not been changed from its original form either accidentally or maliciously.  Corruption of data is a failure to maintain data integrity. To check if our data has been modified or not, we make use of a hash function.  We have two common types: SHA (Secure Hash Algorithm) and MD5(Message Direct 5). Now MD5 is a 128-bit hash and SHA is a 160-bit hash if we’re using SHA-1. There are also other SHA methods that we could use like SHA-0, SHA-2, and SHA-3.

### Availability 
This means that the network should be readily available to its users. This applies to systems and to data. To ensure availability, the network administrator should maintain hardware, make regular upgrades, have a plan for fail-over, and prevent bottlenecks in a network. Attacks such as DoS or DDoS may render a network unavailable as the resources of the network get exhausted.

### What is AAA (Authentication, Authorization, and Accounting)?
Authentication, Authorization, and Accounting (AAA) is an architectural framework to gain access to computer resources, enforcing policies, auditing usage, to provide essential information required for billing of services and other processes essential for network management and security. This process is mainly used so that network and software application resources are accessible to some specific and legitimate users. The AAA concept is widely used in reference to the network protocol RADIUS.

### The first step: Authentication
Authentication is the method of identifying the user. With the help of the user’s authentication credentials, it checks if the user is legitimate or not or if the user has access to the network, by checking if the user’s credentials match with credentials stored in the network database. After the authentication is approved the user gains access to the internal resources of the network.

### Authorization
For the user to perform certain tasks or to issue commands to the network, he must gain authorization. It determines the extent of access to the network and what type of services and resources are accessible by the authenticated user. Authorization is the method of enforcing policies.

### Accounting
In this stage, the usage of system resources by the user is measured: Login time, Data Sent, Data Received, and Logout Time. Accounting Process is carried out by logging out the session statistics and usage information and is used for authorization control, billing, resource utilization.

### RADIUS – 
RADIUS stands for Remote Authentication Dial-In User Service, is a security protocol used in the AAA framework to provide centralized authentication for users who want to gain access to the network. 
Some of the features of RADIUS are: 
1. Open standard protocol for AAA framework.
2. It uses UDP as a transmission protocol. 
3. It uses UDP port number 1812 for authentication and authorization and 1813 for accounting.

### TCP 3-Way Handshake Process
The process of communication between devices over the internet happens according to the current TCP/IP suite model(stripped out version of OSI reference model). The Application layer is a top pile of a stack of TCP/IP models from where network referenced applications like web browsers on the client-side establish a connection with the server. From the application layer, the information is transferred to the transport layer. 

- Step 1: In the first step, client wants to establish a connection with a server, so it sends a segment with SYN(Synchronize Sequence Number) which informs the server that the client is likely to start communication and with what sequence number it starts segments with.
-   Step 2 (SYN + ACK): Server responds to the client request with SYN-ACK signal bits set. Acknowledgement(ACK) signifies the response of the segment it received and SYN signifies with what sequence number it is likely to start the segments with.
-  Step 3 (ACK): In the final part client acknowledges the response of the server and they both establish a reliable connection with which they will start the actual data transfer.

### How mechanism works In TCP : 
 
1. Step 1 (FIN From Client) – 
Suppose that the client application decides it wants to close the connection. (Note that the server could also choose to close the connection). This causes the client to send a TCP segment with the FIN bit set to 1 to the server and to enter the FIN_WAIT_1 state. While in the FIN_WAIT_1 state, the client waits for a TCP segment from the server with an acknowledgment (ACK).
2. Step 2 (ACK From Server) – When the Server received the FIN bit segment from Sender (Client), Server Immediately sends acknowledgement (ACK) segment to the Sender (Client).
3. Step 3 (Client waiting) – While in the FIN_WAIT_1 state, the client waits for a TCP segment from the server with an acknowledgment. When it receives this segment, the client enters the FIN_WAIT_2 state. While in the FIN_WAIT_2 state, the client waits for another segment from the server with the FIN bit set to 1.
4. Step 4 (FIN from Server) – The server sends the FIN bit segment to the Sender(Client) after some time when the Server sends the ACK segment (because of some closing process in the Server).
5. Step 5 (ACK from Client) – When the Client receives the FIN bit segment from the Server, the client acknowledges the server’s segment and enters the TIME_WAIT state. The TIME_WAIT state lets the client resend the final acknowledgment in case the ACK is lost. The time spent by clients in the TIME_WAIT state depends on their implementation, but their typical values are 30 seconds, 1 minute, and 2 minutes. After the wait, the connection formally closes and all resources on the client-side (including port numbers and buffer data) are released.

## Difference Between Threat, Vulnerability and Risk in Computer Network

### Threat
A cyber threat is a malicious act that seeks to steal or damage data or discompose the digital network or system. Threats can also be defined as the possibility of a successful cyber attack to get access to the sensitive data of a system unethically.

### Vulnerability:
In cybersecurity, a vulnerability is a flaw or weakness in a system’s design, security procedures, internal controls, etc., that can be exploited by cybercriminals.

### Risk: 
Cyber risk is a potential consequence of the loss or damage of assets or data caused by a cyber threat. Risk can never be completely removed, but it can be managed to a level that satisfies an organization’s tolerance for risk. So, our target is not to have a risk-free system, but to keep the risk as low as possible.

## Cyber Security, Types and Importance
Cyber Security is the body of technologies, processes, and practices designed to protect networks, devices, programs, and data from attack, theft, damage, modification or unauthorized access. It’s also known as Information Security (INFOSEC), Information Assurance (IA), or System Security.
Cyber Security proper began in 1972 with a research project on ARPANET (The Advanced Research Projects Agency Network), a precursor to the internet. ARPANET developed protocols for remote computer networking.
