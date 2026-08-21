# TryHackMe — Detecting Web Attacks

**Date:** 20 août 2026  
**Status:** ✅ Complete (100%)

## 🎯 What You Learn
How to **detect and defend** against web attacks through logs, network monitoring, and WAFs.

## 🛡️ Detection Methods

**Client-Side Attacks**
- XSS, CSRF detection
- Malicious script patterns

**Server-Side Attacks**
- SQL Injection patterns
- Command injection attempts

**Log-Based Detection**
- Analyze failed login attempts
- Track suspicious SQL queries
- Monitor unusual file access

**Network-Based Detection**
- IDS/IPS systems
- Unusual traffic patterns
- Protocol violations

**Web Application Firewall (WAF)**
- Inspects full request packets
- Blocks known attack patterns
- Rate-limiting & abuse prevention
- Challenge-response (CAPTCHA)
- Threat intelligence integration

## 🚨 WAF Rule Examples
If User-Agent contains "sqlmap" then BLOCK
If User-Agent contains "BotTHM" then BLOCK
If IP reputation = malicious then BLOCK
If login attempts > 5/min per IP then RATE_LIMIT

## ✅ Key Takeaways
- WAFs = first line of defense
- Rules block known attack patterns
- Threat intel keeps rules updated
- Balance: block threats without breaking legitimate traffic

**Result:** Room 100% Complete ✅
