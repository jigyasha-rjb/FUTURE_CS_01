# 🔍 OWASP Juice Shop – Web Security Testing Report

Simulated attacks. Real vulnerabilities. Clear fixes.

---

## 📄 Report

**WebSecurityTestingReport.pdf**  
Detailed security assessment of OWASP Juice Shop v18.0.0  
Includes:  
- Automated scan results (ZAP)  
- Manual findings (Burp Suite)  
- PoCs for XSS & SQLi  
- Mitigation steps  
- OWASP Top 10 mapping  

📁 File: [`WebSecurityTestingReport.pdf`](./WebSecurityTestingReport.pdf)

---

## 🎯 Payloads

Custom payloads used during testing:

📁 Folder: [`/payloads`](./payloads)

- `xss.txt` – Bypass attempts, DOM-based injection  
- `sqli.txt` – Login bypass, error-based injection  

---

## 🧠 Highlights

- SQL injection still effective on modern stacks  
- Client-side sanitization ≠ backend protection  
- Misconfigured CORS and exposed dev files = silent threats  
- Angular

---

## ⚙️ Stack

- OWASP Juice Shop v18.0.0  
- OWASP ZAP v2.16.1  
- Burp Suite CE v2025.5.6  
- Firefox + FoxyProxy  
- Docker on Windows 11 Pro

---

## 💡 TL;DR

What you see sanitized on the frontend means nothing if the backend trusts it.
Frontend polish doesn’t fix backend cracks.



