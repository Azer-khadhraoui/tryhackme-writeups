# TryHackMe — Nmap (Complete)

**Room:** [Nmap](https://tryhackme.com/room/furthernmap) · 15 août 2026

## 🎯 Core Concepts Learned

**Port Scanning Basics**
- Ports are networking constructs directing traffic to applications (65535 total per computer)
- Well-known ports: 0–1023 (1024 total) — e.g., 22 SSH, 53 DNS, 80 HTTP, 443 HTTPS
- Port states: open, closed, filtered

**Scan Types**
| Scan | Type | Pros | Cons |
|------|------|------|------|
| TCP Connect `-sT` | Full handshake | Reliable | Slow, logged |
| SYN `-sS` | Half-open | Fast, stealthy | Requires sudo |
| UDP `-sU` | Stateless | Detects UDP services | Very slow |
| NULL/FIN/Xmas | Malformed packets | Firewall evasion | Unreliable vs Windows |

**NSE (Nmap Scripting Engine)**
- Scripts written in Lua language
- Categories: `safe`, `intrusive`, `vuln`, `exploit`, `auth`, `brute`, `discovery`
- Usage: `--script=<category>` or `--script=<script-name>`
- Arguments: `--script-args <name>.<arg>=<value>`

**Firewall Evasion**
- `-Pn`: Skip ping, scan anyway (bypass ICMP block)
- `-f`: Fragment packets
- `--mtu <num>`: Set packet size (multiple of 8)
- `--scan-delay <time>ms`: Add delay between packets
- `--badsum`: Invalid checksum to detect firewalls

**Important Switches**
- `-sV`: Detect service versions
- `-O`: OS detection
- `-oA <file>`: Save in all formats
- `-A`: Aggressive mode (OS + version + scripts + traceroute)
- `-T5`: Timing template level 5 (fastest, noisiest)
- `-p 80`: Scan port 80 only
- `-p-`: Scan all ports

## 🔬 Practical Lab Results

**Target:** 10.129.162.246

```bash
# Q1: Ping test
ping -c 4 10.129.162.246
# Result: 100% packet loss — ICMP blocked (Answer: N)

# Q2: Xmas scan 1-999
sudo nmap -sX -p 1-999 10.129.162.246
# Result: All 999 ports open|filtered

# Q4: SYN scan 1-5000
sudo nmap -sS -p 1-5000 10.129.162.246
# Result: All 5000 ports filtered (Answer: 0 open ports)

# Q6: FTP anon script
nmap --script=ftp-anon -p 21 -Pn 10.129.162.246
# Result: Port 21 filtered — cannot test (Answer: N)
```

**Key Observations:**
- Firewall blocks both SYN and Xmas scans differently (stateful filtering)
- Port 21 (FTP) is filtered, preventing anonymous login test

## ✅ NSE Script Questions Answered

| Script | Argument |
|--------|----------|
| ftp-anon | `maxlist` |
| smb-os-discovery | depends on: `smb-brute` |

## 🔑 Key Takeaways

1. Nmap is the industry standard for port scanning — understand scan types deeply
2. Firewalls respond differently to different packet types
3. NSE scripts are powerful for targeted reconnaissance and exploitation
4. Always use `-Pn` if target blocks ICMP
5. Read script help with `nmap --script-help <name>` for arguments
