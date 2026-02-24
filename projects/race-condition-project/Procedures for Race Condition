## Procedures

### Step 1 — Account Session Preparation
- Logged into multiple user accounts using separate browser tabs.
- Prepared two concurrent sessions to simulate real-world parallel transaction behavior.

This allowed testing of shared resource handling under simultaneous requests.

---

### Step 2 — Proxy Configuration
- Started Burp Suite.
- Enabled FoxyProxy browser extension.
- Configured browser traffic to route through Burp Suite proxy.
- Enabled Intercept Mode in Burp Proxy.

This allowed capture and modification of HTTP requests.

---

### Step 3 — Transaction Request Capture
- Navigated to the payment and recharge section of the application.
- Entered transaction details including:
  - Source account
  - Destination account
  - Transaction amount

Request interception was verified before submitting the transaction.

---

### Step 4 — Payload Analysis and Request Modification
- Captured POST transaction request using Burp Proxy.
- Sent request to Burp Repeater for analysis.

Multiple parallel requests were prepared to exploit timing validation windows.

---

### Step 5 — Parallel Request Exploitation
- Created tab groups inside Burp Repeater.
- Duplicated transaction requests across multiple tabs.
- Configured requests to send in parallel mode.

This exploited the small timing window between:
- Balance validation
- Transaction execution

---

### Step 6 — Verification of Exploit Success
- Observed unusual balance changes between accounts.
- Verified flag retrieval inside the lab environment.

**Captured Flag:**  
