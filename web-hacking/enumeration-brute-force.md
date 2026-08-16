# TryHackMe — Enumeration & Brute Force

**Date:** 16 août 2026  
**Status:** 🔄 In Progress (Lab DNS issues)

## 🎯 What You Learn
- **Enumeration** = Finding valid usernames/emails before attacking
- **Brute Force** = Testing multiple passwords to crack accounts
- Finding valid users through registration pages, password reset, verbose errors

## 🔍 Enumeration Techniques

**Common Places to Enumerate:**
1. **Registration Pages** — App confirms if email exists
2. **Password Reset** — Different responses reveal if username exists
3. **Verbose Error Messages** — "Username not found" vs "Wrong password"
4. **Data Breaches** — Testing reused credentials across platforms

## 🛠️ Tools Used
- Python script (requests library) to automate email checking
- dirb for directory enumeration

## Key Learnings
- Verbose error messages leak information about valid users
- Enumeration = first step before brute force
- Script can test 100s of emails automatically

## ❌ Challenges Encountered
- Lab DNS resolution issues (enum.thm not accessible)
- Tested multiple solutions but server connectivity problem

## Next Steps
- Retry when lab infrastructure is stable
- Learn brute force password cracking techniques
