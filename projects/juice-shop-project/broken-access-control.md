# SQL Injection — Administrator Login Bypass

## Scenario
The objective was to gain unauthorized access to the administrator account by testing the login functionality for SQL Injection vulnerabilities.

Testing was performed in a controlled lab environment using OWASP Juice Shop.

---

## Objective
- Identify SQL Injection vulnerability in authentication mechanism.
- Attempt privilege escalation via login bypass.
- Demonstrate insecure query handling.

---

## Tools Used
- Browser

---

## Vulnerability Type
SQL Injection (Authentication Bypass)

---

## Exploitation Steps

### Step 1 — Input Injection Payload

In the login form:

Email: ' OR 1=1;--


Password:  any value can suffice in this case - "fakepassword" was used


---

### Step 2 — Authentication Bypass

The application accepted the injected SQL condition.

Because:

- `OR 1=1` always evaluates to TRUE
- `--` comments out the remaining SQL query

This resulted in the application logging in as the first user in the database (Administrator).

---

## Why This Works

The backend query likely resembled: SELECT * FROM users WHERE email = '<user_input>' AND password = '<password>';

After injection, it becomes:
SELECT * FROM users WHERE email = '' OR 1=1;--' AND password = '';


Since `1=1` is always TRUE, authentication is bypassed.

---

## Impact

If exploited in a real-world system, attackers could:

- Gain administrative access
- Steal user data
- Modify application settings
- Escalate privileges

This represents a critical security vulnerability.

---

## Remediation Recommendations

- Use parameterized queries (prepared statements)
- Implement ORM frameworks safely
- Validate and sanitize user input
- Apply least privilege database permissions

---

## Skills Demonstrated

- SQL Injection testing
- Authentication bypass exploitation
- Understanding of backend query manipulation
- Security vulnerability documentation
