# TryHackMe — Web Application Pentesting: Enumeration & Brute Force

**Room:** Enumeration & Brute Force  
**Date:** 15 août 2026  
**Status:** 🔄 In Progress

## 🎯 Objective
Learn enumeration and brute force techniques for web application penetration testing.

## 📝 Key Concepts — Task 1

**Enumeration = Finding valid usernames/emails in a web application**

### Common Places to Enumerate:

1. **Registration Pages**
   - App confirms if email/username already exists
   - Attackers use this to build lists of valid users

2. **Password Reset Features**
   - Different responses reveal if username exists
   - "Username found" vs "Username not found" messages

3. **Verbose Error Messages**
   - Distinguish between "username not found" and "incorrect password"
   - Directly confirms valid usernames

4. **Data Breach Information**
   - Compromised credentials from past breaches
   - Attackers test username/password reuse across platforms

## ✅ Task 1 Answers

| Question | Answer |
|----------|--------|
| Type of error messages revealing valid usernames | Verbose error messages |

## 🔜 Next
Task 2 — Brute Force techniques
