# Web Application Security Testing — Burp Suite & Reflected XSS Exploitation

## Scenario
A vulnerable web application support ticket form was tested to identify common input validation weaknesses. The objective was to determine whether an attacker could inject malicious scripts into user inputs and execute code in victim browsers through Reflected Cross-Site Scripting (XSS).

---

## Objective
- Identify web application vulnerabilities.
- Test input validation mechanisms.
- Demonstrate exploitation of Reflected XSS vulnerabilities.

---

## Tools Used
- TryHackMe Lab Environment  
- Burp Suite Proxy  
- Burp Suite Repeater  
- Burp Suite Intruder  

---

## Methodology

### Traffic Interception
- Configured browser traffic to route through Burp Suite Proxy.
- Enabled intercept mode to capture HTTP requests between client and server.

**Evidence (Add Screenshot Here)**  
- Burp Proxy interception request.

---

### Form Submission Testing
Submitted legitimate data into the support form:

Email:pentester@example.thm


Captured request using Burp Proxy for modification.

---

### Payload Injection & Filter Bypass
Modified the email input field with a malicious payload:

```html
<script>alert("Succ3ssful XSS")</script>

Used URL encoding (Ctrl + U in Burp Suite) to bypass client-side filtering mechanisms.

Exploitation — Reflected XSS

Forwarded modified request to server.

Browser executed injected JavaScript payload.

Successful execution confirmed vulnerability.

Evidence (Add Screenshot Here)

Payload request modification.

XSS execution popup.

Impact Analysis

If exploited by an attacker, this vulnerability could allow:

Execution of malicious scripts.

Session cookie theft.

Phishing attacks.

Client-side data manipulation.

Remediation Recommendations

Implement server-side input validation.

Apply output encoding.

Enforce Content Security Policy (CSP).

Avoid relying only on client-side filtering.

Skills Demonstrated

Web application penetration testing

Vulnerability analysis

XSS exploitation techniques

Security reporting and remediation thinking
