# 🔍 OWASP Juice Shop – Web Security Testing Report

One vulnerable app. A few payloads. Plenty of surprises.

---

## 📄 Report

**WebSecurityTestingReport.pdf**  
Detailed security assessment of OWASP Juice Shop v18.0.0  
Covers:
- Automated scanning with ZAP
- Manual testing with Burp Suite
- Exploits for XSS & SQLi
- Misconfigurations and insecure defaults
- OWASP Top 10 mappings and remediations 

📁 File: [`WebSecurityTestingReport.pdf`](./WebSecurityTestingReport.pdf)

---

## 🎯 Payloads

Payloads used during testing:

📁 Folder: [`/payloads`](./payloads)

- `xss.txt` – Bypass attempts, DOM-based injection  
- `sqli.txt` – Login bypass, error-based injection  

---
## 🚨 Attack Summary

| Vulnerability              | OWASP Category     | Severity | Tool Used  | Vector                                 |
|----------------------------|--------------------|----------|------------|----------------------------------------|
| SQL Injection (Login Bypass) | A03: Injection     | 🔴 High  | Burp Suite | `POST /rest/user/login`                |
| Reflected XSS              | A03: Injection     | 🔴 High  | Burp Suite | `/#/search?q=<payload>`                |
| Missing CSP Header         | A05: Misconfiguration | 🟠 Medium | ZAP        | Site-wide response headers             |
| Open CORS (Wildcard Origin)| A01: Broken Access Control | 🟠 Medium | ZAP        | `Access-Control-Allow-Origin: *`       |
| Hidden Files Accessible    | A05: Misconfiguration | 🟠 Medium | ZAP        | `.env`, `.git`, and more               |
| 3rd-Party Script Inclusion | A08: Integrity Failures | 🟡 Low   | ZAP        | External JS without SRI                |

> 📌 These are **prioritized findings** based on impact, exploitability, and coverage within the scope of this report.  
> Juice Shop contains more challenges and vulnerabilities by design.

---

## ⚙️ Test Environment

- Juice Shop v18.0.0  
- OWASP ZAP v2.16.1  
- Burp Suite CE v2025.5.6  
- Firefox + FoxyProxy  
- Dockerized lab (Win 11 Pro 24H2)

---

## ✨ Highlights

- 🧬 **SQL Injection still works in 2025**  
  A classic `' OR 1=1--` still gets you logged in. Some things never change.

- 🎭 **Angular sanitization ≠ protection**  
  `<script>` was blocked, but `<iframe src=javascript:...>` walked right in.

- 🌍 **CORS says: everyone’s invited**  
  Wildcard origins exposed private APIs to any domain. Oops.

- 🔍 **Hidden files aren't hiding**  
  `.env`, `.git`, and other dev artifacts were fully accessible in production.

- 🚧 **No Content Security Policy**  
  Like leaving the front door open, but for scripts.

- 🔗 **3rd-party scripts with no integrity check**  
  If they change upstream, you won't know until it's too late.

- 🧪 **Manual testing caught what automation missed**  
  ZAP gave the baseline. Burp exposed the core issues.

---

## 💡 TL;DR

What you see sanitized on the frontend means nothing if the backend trusts it.
Frontend polish doesn’t fix backend cracks.



