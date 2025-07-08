# 🔐 Vulnerability Assessment & Penetration Testing (VAPT) Report

**Client Name:** XYZ Corporation  
**Project Title:** Web Application Penetration Testing  
**Assessment Date:** June 20–25, 2025  
**Report Date:** July 1, 2025  
**Prepared by:** Sifat | Security Analyst  
**Confidentiality:** Strictly Confidential  

---

## 🧾 1. Executive Summary

This report documents the findings of a web application penetration test performed on the XYZ Corporation’s online portal. The objective was to identify security vulnerabilities that could be exploited by attackers and to provide actionable recommendations.

> **Risk Summary:**  
> - Total Vulnerabilities: 12  
> - Critical: 2  
> - High: 3  
> - Medium: 4  
> - Low: 3  

---

## 🛰️ 2. Scope of Engagement

| Asset | Type | IP / URL | Notes |
|------|------|----------|-------|
| `https://portal.xyzcorp.com` | Web App | Public | Primary test target |
| `api.xyzcorp.com` | API Endpoint | Public | Used by mobile app |

---

## ⚙️ 3. Methodology

Testing was performed using a **black-box** approach following the **OWASP Testing Guide v4** and **NIST SP 800-115**. The phases included:

- Reconnaissance  
- Vulnerability Scanning  
- Exploitation  
- Post-exploitation  
- Reporting

**Tools Used:**
- Nmap  
- Burp Suite Pro  
- OWASP ZAP  
- Nikto  
- SQLmap  
- Metasploit Framework

---

## 🚨 4. Key Findings & Risk Ratings

| ID | Vulnerability | Severity | Affected URL | CWE |
|----|---------------|----------|--------------|-----|
| V-001 | SQL Injection | 🔴 **Critical** | `/login` | CWE-89 |
| V-002 | Broken Authentication | 🔶 **High** | `/auth` | CWE-287 |
| V-003 | Reflected XSS | 🟡 Medium | `/search?q=` | CWE-79 |
| V-004 | Server Info Disclosure | 🟢 Low | `/server-status` | CWE-200 |

---

### 🔍 Example Finding: SQL Injection (Critical)

- **Affected URL:** `https://portal.xyzcorp.com/login`  
- **Parameter:** `username`  
- **Payload:** `' OR 1=1--`  
- **Impact:** Bypass authentication, full DB access  
- **Evidence:**  
  - DB dump extracted using SQLmap  
  - Able to retrieve user password hashes

**Recommendation:**
- Use parameterized queries (prepared statements)  
- Apply input validation and WAF filtering  
- Regularly scan and patch back-end services  

---

## 🛡️ 5. Recommendations Overview

| Category | Fix Summary |
|----------|-------------|
| Input Validation | Implement input sanitization for all user inputs |
| Authentication | Enforce MFA and rate limiting on login endpoints |
| Server Configuration | Disable unnecessary services and info pages |
| Patch Management | Regularly update third-party libraries |

---

## 📁 6. Appendix

### 🔧 Tools Used

- Nmap (v7.95)  
- Burp Suite Pro (v2025.6)  
- OWASP ZAP  
- SQLmap  
- Nikto  
- Dirb / Gobuster

### 📚 References

- [OWASP Top 10 – 2025](https://owasp.org/Top10)  
- [CWE Common Weakness Enumeration](https://cwe.mitre.org)  
- [NIST SP 800-115](https://csrc.nist.gov/publications/detail/sp/800-115/final)

---

## 🔒 7. Confidentiality Statement

This document contains confidential information intended solely for XYZ Corporation. It must not be shared without written permission from the author.

---

## 📌 Notes for Portfolio

- Replace sensitive details (client name, domain, IPs) with fictitious data.
- You can include this report in a repository like:  
  `github.com/yourusername/vapt-report-samples`
- Optionally add screenshots of tools (e.g., Burp Suite, Nmap, SQLmap outputs).

