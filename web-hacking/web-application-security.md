# TryHackMe — Web Application Security

Date: 16 août 2026
Status: ✅ Completed
Room: Web Application Security

## 🎯 What You Learn

This room introduces the fundamentals of web application security and covers some common vulnerabilities found in web applications.

Main topics:

* Understanding how web applications work
* Identification and Authentication Failures
* Broken Access Control
* Injection
* Cryptographic Failures
* Insecure Direct Object References (IDOR)

## 🌐 Task 1 — Introduction

A web application is essentially an application running on a remote server that can be accessed through a web browser.

Unlike traditional applications, there is no need to install the application locally. The browser communicates with the remote server using HTTP/HTTPS.

Examples of web applications include:

* Webmail
* Online shopping platforms
* Online banking
* Social media
* Online office applications

A typical web application can interact with several backend components, such as databases containing:

* Product information
* Customer information
* Orders and invoices

This makes web applications an important attack surface because a vulnerability can potentially expose sensitive information.

### Answer

**What do you need to access a web application?**

`Browser`

## 🔐 Task 2 — Web Application Security Risks

The room introduces several common categories of web application vulnerabilities.

### Identification and Authentication Failure

Authentication is responsible for verifying that a user is who they claim to be.

Common weaknesses include:

* Weak passwords
* Brute-force attacks
* Unlimited login attempts
* Poor password storage
* Weak authentication mechanisms

For example, if a login page allows unlimited password attempts without rate limiting or account lockout, an attacker can perform a brute-force attack.

### Answer

**What is the category of a login page allowing unlimited login attempts?**

`Identification and Authentication Failure`

---

### Broken Access Control

Broken Access Control occurs when users can access resources or perform actions that should not be available to them.

Examples include:

* Accessing another user's account
* Accessing administrative functionality without authorization
* Modifying another user's information
* Accessing protected pages without authentication

This category is especially important when an application relies on user-controlled identifiers.

---

### Injection

Injection vulnerabilities occur when untrusted user input is interpreted as code or commands by the application.

Examples include:

* SQL Injection
* Command Injection
* Other forms of malicious input

Proper input validation, sanitization, and parameterized queries are important defenses against injection attacks.

---

### Cryptographic Failures

Cryptographic failures occur when sensitive information is not adequately protected.

Examples include:

* Sending credentials over HTTP instead of HTTPS
* Using weak encryption algorithms
* Using weak cryptographic keys
* Storing sensitive information without appropriate protection

### Answer

**What is the category when username and password are sent in cleartext?**

`Cryptographic Failures`

## 🧪 Task 3 — Practical Example: IDOR

The practical part of the room demonstrates an **Insecure Direct Object Reference (IDOR)** vulnerability.

IDOR is a type of **Broken Access Control** vulnerability.

The basic idea is that an application uses a user-controlled identifier to access an object, but does not properly verify whether the current user is authorized to access that object.

For example, an application might use:

```text
/activity?user_id=11
```

If changing the value to another number allows access to another user's activity, the application may be vulnerable to IDOR.

### 🔎 Testing the IDOR

The first step is to identify parameters controlled by the user.

In this lab, the interesting parameter is:

```text
user_id
```

Instead of only accessing the current user's activity, we can test other identifiers:

```text
user_id=1
user_id=2
user_id=3
...
```

The important observation is whether changing the identifier exposes information belonging to another user.

This demonstrates why authorization checks must be performed server-side.

### 📦 Inventory Management System

The vulnerable application is an Inventory Management System.

The application contains several sections, including:

* Planned Shipments
* Inventory
* Your Activity

The lab simulates an attacker who modified shipment information, causing incorrect tires to be assigned to different assembly lines.

The objective is to identify the user responsible for the malicious changes and revert those changes.

### 🕵️ Exploiting the IDOR

The `Your Activity` page uses a user identifier in the URL.

By modifying the `user_id` parameter, it is possible to access the activity of other users.

This is an IDOR because the application trusts the supplied identifier without correctly checking whether the current user is authorized to access that user's information.

After checking the different users, the malicious activity can be identified.

The changes made by the attacker can then be reverted through the application.

### 🚩 Flag

After reverting the malicious changes, the application provides the following flag:

```text
THM{IDOR_EXPLORED}
```

## 🧠 Key Learnings

* Web applications are an important attack surface.
* Authentication and authorization are different concepts.
* Broken Access Control can expose sensitive resources.
* User-controlled IDs should never be trusted without authorization checks.
* IDOR vulnerabilities are often easy to test by modifying parameters.
* Sensitive information should be protected using appropriate cryptography and HTTPS.
* Input validation is important for preventing injection attacks.

## 🛠️ Concepts

`Web Application Security` • `Authentication` • `Authorization` • `Broken Access Control` • `IDOR` • `Injection` • `Cryptography`

## 🏁 Conclusion

This room provided a practical introduction to web application security.

The most important practical lesson was understanding how an IDOR vulnerability can allow one user to access another user's information simply by modifying an object identifier.

The room was successfully completed.

**Flag:** `THM{IDOR_EXPLORED}`

---

**Room:** Web Application Security
**Status:** ✅ Completed
