# Broken Access Control Testing — OWASP Juice Shop

## Scenario
Security testing was performed on a vulnerable web application to identify broken access control vulnerabilities.

Access control vulnerabilities occur when an application fails to properly enforce permissions between users.

Testing was performed on OWASP Juice Shop security training platform.

---

## Objective
- Identify authorization weaknesses.
- Attempt unauthorized access to restricted resources.
- Understand privilege escalation risks.

Training platform: OWASP Security Labs.

---

## Tools Used
- Browser Developer Tools
- Burp Suite Proxy (Optional)
- Application UI Manipulation

Training platform: :contentReference[oaicite:0]{index=0} Juice Shop.

---

## Methodology

### Step 1 — Reconnaissance
- Logged into application using normal user account.
- Explored available user functionalities.

---

### Step 2 — Admin Section Access Testing
Attempted to access restricted admin pages by modifying URL paths.

Example attempts:
/admin
/#/admin
/api/admin

Result:
- Successfully accessed administrative interface without proper authorization validation.

---

### Step 3 — Basket Manipulation Testing
Tested ability to access other users' shopping baskets.

Observed:
- Application failed to properly validate user ownership of resources.

This allowed viewing or modifying other users' data.

---

### Step 4 — CSRF Testing (Optional Advanced)
Attempted cross-origin request testing to evaluate session security controls.

---

## Impact Analysis
If exploited in real systems, attackers could:
- Access sensitive user data.
- Modify administrative settings.
- Perform privilege escalation.
- Manipulate business transactions.

---

## Remediation Recommendations
- Implement strict role-based access control (RBAC).
- Validate user permissions on server side.
- Protect sensitive endpoints.
- Apply session validation checks.

---
