# SQL Injection — User Credential Extraction

## Scenario

The objective was to extract all registered user credentials from the application database by exploiting a SQL Injection vulnerability in the search functionality.

Testing was performed in a controlled lab environment using OWASP Juice Shop.

---

## Objective

- Identify SQL Injection in search endpoint.
- Perform UNION-based SQL Injection.
- Extract sensitive user credential data.

---

## Vulnerability Type

SQL Injection (UNION-based Data Exfiltration)

---

## Exploitation Steps

### Step 1 — Identify Injection Point

The search field was tested for SQL injection by inserting special characters and observing application behavior.

The search query parameter was vulnerable to injection.

---

### Step 2 — Craft UNION-Based Payload

Payload used: ö') UNION SELECT 1,email,password,4,5,6,7 FROM users;--


Explanation:

- `UNION SELECT` combines results from another table.
- The number of columns must match the original query.
- `email` and `password` fields were extracted from the `users` table.
- `--` comments out the remaining SQL query.

---

### Step 3 — Alternative Direct API Exploitation

The vulnerable REST endpoint was directly targeted: /rest/product/search?q=a') UNION SELECT email,password,3,4,5,6,7 FROM users;--


This directly returned database records via the web service.

---

## Why This Works

The backend likely used a query similar to: SELECT * FROM products WHERE name LIKE '%<user_input>%';


By injecting a UNION clause, attacker-controlled queries were appended to the original statement.

This allowed retrieval of data from unrelated tables.

---

## Impact

If exploited in a real-world system, attackers could:

- Extract all user credentials
- Access password hashes
- Perform account takeover
- Leak sensitive personal data
- Pivot to further attacks

This is considered a Critical severity vulnerability.

---

## Remediation Recommendations

- Use parameterized queries (Prepared Statements).
- Disable detailed database error messages.
- Apply strict input validation.
- Implement Web Application Firewall (WAF).
- Apply least privilege database roles.

---

## Skills Demonstrated

- Advanced SQL Injection
- UNION-based exploitation
- Database schema manipulation
- Sensitive data extraction
- Web API exploitation
