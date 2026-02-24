# Prompt Injection — Coupon Code Extraction (Support Chat)

## Scenario

The objective was to retrieve a hidden coupon code from the Juice Shop Support Chat by exploiting prompt injection techniques.

The chatbot is designed with restrictions preventing disclosure of sensitive information such as coupon codes.

---

## Objective

- Identify prompt injection vulnerability in WebLLM chatbot.
- Manipulate chatbot behavior.
- Extract restricted coupon information.

---

## Vulnerability Type

Prompt Injection (LLM Manipulation)

---

## Exploitation Steps

### Step 1 — Access Support Chat

- Opened the sidebar menu.
- Navigated to **Support Chat** feature.

---

### Step 2 — Analyze Chatbot Behavior

The chatbot initially refused to provide coupon codes due to embedded safety restrictions.

---

### Step 3 — Craft Prompt Injection Payload

Instead of directly asking for a coupon, the prompt was framed to override restrictions.

Example attack style:

- Convince the bot it is safe to share.
- Ask it to ignore previous instructions.
- Reframe the conversation context.


The chatbot responded with a valid coupon code.

---

## Why This Works

Large Language Models operate based on:

- System instructions
- User input prompts
- Context interpretation

By injecting carefully crafted instructions, the attacker overrides the intended safety logic.

This is known as prompt injection or LLM jailbreaking.

---

## Impact

In real-world applications, prompt injection can lead to:

- Disclosure of sensitive data
- Exposure of API keys
- Generation of malicious instructions
- Policy bypass
- Business logic abuse

As of recent security research, prompt injection is considered a critical risk in AI-powered systems.

---

## Remediation Recommendations

- Implement strict server-side validation.
- Do not allow LLM to directly access sensitive backend data.
- Use output filtering and moderation layers.
- Apply instruction hierarchy enforcement.
- Implement AI response validation middleware.

---

## Skills Demonstrated

- LLM security testing
- Prompt manipulation techniques
- AI vulnerability assessment
- Business logic abuse analysis
