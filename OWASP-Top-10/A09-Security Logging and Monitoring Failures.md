# A09-Security Logging and Monitoring Failures

# Introduction

Security logging and monitoring failures represent a critical vulnerability in modern software systems. This category, ranked #9 in the OWASP Top 10 2021, emphasizes the importance of detecting, escalating, and responding to active breaches.

# Key Vulnerabilities

- Insufficient logging of auditable events (e.g., logins, failed logins, high-value transactions)
- Inadequate or unclear log messages for warnings and errors
- Lack of monitoring for suspicious activity in application and API logs
- Local-only storage of logs
- Ineffective alerting thresholds and response escalation processes
- Failure to trigger alerts during penetration testing or DAST scans
- Inability to detect, escalate, or alert for active attacks in real-time or near real-time

# Prevention Strategies

To mitigate security logging and monitoring failures, developers should implement the following controls:

- Ensure comprehensive logging of login attempts, access control, and server-side input validation failures
- Generate logs in easily consumable formats for log management solutions
- Implement proper log data encoding to prevent injections or attacks on logging systems
- Establish audit trails with integrity controls for high-value transactions
- Implement effective monitoring and alerting systems for quick detection and response to suspicious activities
- Adopt an incident response and recovery plan (e.g., NIST 800-61r2)

# Tools and Frameworks

Several tools can assist in improving security logging and monitoring:

- OWASP ModSecurity Core Rule Set
- Elasticsearch, Logstash, Kibana (ELK) stack
- Custom dashboards and alerting systems

# Conclusion

Effective security logging and monitoring are essential for maintaining the integrity and security of software systems. By implementing robust logging practices and monitoring systems, organizations can significantly improve their ability to detect and respond to security breaches, ultimately enhancing their overall security posture.
