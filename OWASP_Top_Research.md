# OWASP Top 10 Vulnerabilities Research
**Cyber Security Internship Track – Week 1**

**Name:** Nayab Akhtar
**Track:** Cyber Security Internship  
**Date:** 20th July, 2026


# Introduction

The Open Web Application Security Project (OWASP) is a nonprofit organization that improves software security through open-source projects, documentation, and community education. The **OWASP Top 10 (2021)** is one of the most respected resources in cybersecurity. It identifies the ten most critical security risks affecting web applications.

This report discusses five major vulnerabilities from the OWASP Top 10 list. Each section explains the vulnerability in simple language, how attackers exploit it, a real-world example, and methods developers can use to prevent it.


# 1. Injection

## What is Injection?

Injection occurs when an application accepts untrusted user input and includes it directly in a command or database query without proper validation. This allows an attacker to send malicious input that changes the intended command.

The most common type is **SQL Injection**, where attackers manipulate SQL database queries.

### Example (Plain Language)

Imagine a website login form asks for a username and password. Instead of entering a normal username, an attacker enters SQL code that tricks the database into logging them in without knowing the password.


## How an Attacker Exploits It

An attacker:

- Finds a form that communicates with a database.
- Enters malicious SQL code instead of normal input.
- The database executes the attacker's SQL command.
- Sensitive information such as usernames, passwords, or financial records may be exposed.


## Real-World Example

### Equifax Data Breach (2017)

Although the main cause involved an unpatched vulnerability in Apache Struts, attackers also executed malicious database queries after gaining access. Personal information of approximately **147 million people** was exposed, including Social Security numbers and addresses.


## Prevention

Developers should:

- Use parameterized queries (Prepared Statements).
- Validate and sanitize all user inputs.
- Avoid building SQL queries by concatenating strings.
- Apply the principle of least privilege for database accounts.
- Use Web Application Firewalls (WAF).


# 2. Broken Access Control

## What is Broken Access Control?

Broken Access Control happens when users can access information or perform actions they should not be allowed to.

In simple words, the application fails to properly check whether a user has permission before giving access.


## How an Attacker Exploits It

An attacker may:

- Change a URL manually.
- Modify request parameters.
- Access administrator pages without authorization.
- View or edit another user's information.

Example:

Instead of visiting:

```
/profile?id=15
```

the attacker changes it to

```
/profile?id=16
```

and gains access to another user's profile.


## Real-World Example

### Facebook View As Bug (2018)

A vulnerability in Facebook's "View As" feature allowed attackers to steal access tokens, affecting around **50 million user accounts**.


## Prevention

Developers should:

- Check authorization on every request.
- Deny access by default.
- Use Role-Based Access Control (RBAC).
- Never trust client-side permissions.
- Regularly test access control mechanisms.


# 3. Cryptographic Failures

## What is a Cryptographic Failure?

Cryptographic Failures occur when sensitive data is not properly protected through encryption.

Examples include:

- Plain text passwords
- Unencrypted credit card data
- Weak encryption algorithms

## How an Attacker Exploits It

If data is stored or transmitted without proper encryption, attackers can:

- Intercept network traffic.
- Read confidential information.
- Steal passwords.
- Perform identity theft.

## Real-World Example

### Yahoo Data Breaches (2013–2014)

More than **3 billion accounts** were compromised. Weak password protection and outdated security practices contributed to the scale of the breach.

## Prevention

Developers should:

- Use HTTPS everywhere.
- Encrypt sensitive data.
- Store passwords using strong hashing algorithms such as bcrypt or Argon2.
- Never store passwords in plain text.
- Keep encryption libraries updated.

# 4. Cross-Site Scripting (XSS)

## What is Cross-Site Scripting?

Cross-Site Scripting (XSS) happens when an attacker injects malicious JavaScript into a website viewed by other users.

Instead of attacking the website directly, the attacker attacks the users of the website.

## How an Attacker Exploits It

An attacker:

- Finds an input field that displays user content.
- Inserts malicious JavaScript.
- Another user opens the page.
- The script runs inside the victim's browser.

The attacker may steal:

- Session cookies
- Login tokens
- Personal information

## Real-World Example

### eBay Cross-Site Scripting Vulnerability (2014)

Attackers created fake product listings containing malicious JavaScript that redirected users to phishing websites where login credentials were stolen.

## Prevention

Developers should:

- Escape all user-generated output.
- Validate and sanitize user input.
- Use Content Security Policy (CSP).
- Encode HTML output.
- Use secure frameworks that automatically escape output.

# 5. Security Misconfiguration

## What is Security Misconfiguration?

Security Misconfiguration happens when applications, servers, databases, or cloud services are left with insecure default settings.

Examples include:

- Default passwords
- Debug mode enabled
- Open cloud storage
- Unnecessary services running

## How an Attacker Exploits It

Attackers scan websites looking for:

- Open admin panels
- Default credentials
- Misconfigured servers
- Public cloud storage

Once found, they may gain unauthorized access or steal sensitive information.

## Real-World Example

### Capital One Data Breach (2019)

A cloud server configuration error allowed an attacker to access personal information belonging to over **100 million customers**.

## Prevention

Developers should:

- Disable unnecessary services.
- Remove default usernames and passwords.
- Regularly update software.
- Perform security configuration reviews.
- Use automated security scanning tools.


# Summary Table

| Vulnerability | Main Risk | Prevention |
|--------------|-----------|------------|
| Injection | Database manipulation | Prepared statements, input validation |
| Broken Access Control | Unauthorized access | Authorization checks, RBAC |
| Cryptographic Failures | Exposure of sensitive data | Encryption, HTTPS, strong password hashing |
| Cross-Site Scripting (XSS) | Browser attacks on users | Output encoding, CSP, input validation |
| Security Misconfiguration | Unauthorized access due to insecure settings | Secure configuration, updates, remove defaults |


# Personal Reflection

The vulnerability that surprised me the most was **Security Misconfiguration**. Before researching this topic, I believed most cyberattacks relied on advanced hacking techniques. I learned that many serious breaches happen simply because systems are configured incorrectly or left with default settings. This showed me that good cybersecurity depends not only on writing secure code but also on properly configuring and maintaining systems.


# References

1. OWASP Foundation. *OWASP Top 10:2021*. https://owasp.org/www-project-top-ten/

2. OWASP Cheat Sheet Series. https://cheatsheetseries.owasp.org/

3. National Institute of Standards and Technology (NIST). https://www.nist.gov/

4. CISA Cybersecurity Resources. https://www.cisa.gov/

5. freeCodeCamp Cybersecurity Articles. https://www.freecodecamp.org/news/
