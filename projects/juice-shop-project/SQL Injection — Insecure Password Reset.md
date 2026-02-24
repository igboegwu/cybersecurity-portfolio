# Insecure Password Reset — Bender Account Takeover

## Scenario

The objective was to change the password of user **Bender** to `slurmCl4ssic` by exploiting insecure session handling and weak password storage mechanisms.

Testing was performed in a controlled lab environment using OWASP Juice Shop.

---

## Objective

- Analyze authentication token storage
- Extract sensitive information from cookies
- Identify weak password hashing
- Perform account takeover

---

## Vulnerability Type

- Sensitive Data Exposure
- Weak Hashing Algorithm (MD5)
- Insecure Session Design

---

## Exploitation Steps

### Step 1 — Login as Bender

Logged into the application using Bender's account.

After login, a session token was stored in the browser cookie.

---

### Step 2 — Decode the Session Token

The session cookie was Base64 decoded.

Decoded content revealed a JSON structure:

{
"status":"success",
"data":{
"id":3,
"email":"bender@juice-sh.op
",
"password":"fa3360bfd5e190cb65a113c198dfa164"
}
}


The password field contained an MD5 hash.

---

### Step 3 — Crack the MD5 Hash

The extracted hash: fa3360bfd5e190cb65a113c198dfa164


Using publicly available MD5 hash lookup databases, the plaintext password was identified as: booze


This demonstrates weak password hashing implementation.

---

### Step 4 — Change Password

Logged in using:

Email:
bender@juice-sh.op

Password:
booze

Navigated to the Change Password section and set new password to: slurmCl4ssic


Challenge successfully completed.

---

## Why This Works

- The application exposes sensitive data inside client-side cookies.
- Passwords are stored using MD5 (a broken hashing algorithm).
- No proper session protection or encryption was enforced.

---

## Impact

In real-world systems, this could allow attackers to:

- Extract password hashes
- Perform offline cracking attacks
- Take over user accounts
- Escalate privileges

This is considered a High severity vulnerability.

---

## Remediation Recommendations

- Never store password hashes in client-side tokens.
- Use secure password hashing algorithms (bcrypt, Argon2).
- Sign and encrypt session tokens.
- Implement secure HTTP-only cookies.
- Avoid exposing sensitive fields in authentication responses.

---

## Skills Demonstrated

- Session token analysis
- Base64 decoding
- Hash identification
- Password cracking methodology
- Account takeover exploitation
- Security impact assessment


