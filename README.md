# Risk Register & Treatment Implementation
> **Note on AI assistance:** This is a portfolio project completed during my pivot from twenty years of legal practice into AI Governance and cybersecurity GRC. The technical implementation work in this repository was completed with AI tooling (ChatGPT, Claude, Copilot) under my direction. My role on the project was design, evaluation, documentation, and quality assurance — the specific seat the IAPP AIGP credential is designed to fill. I do not represent myself as a hands-on developer or security engineer.

**Author:** Jonathan W. Doolan  
**Date:** October 2025  
**Frameworks:** NIST CSF, CIS Controls v8, ISO 27002, SOC 2, HIPAA Security Rule

---

## Overview

This project documents the development of a comprehensive risk register and the hands-on implementation of four critical security controls addressing high-priority organizational risks aligned with healthcare security frameworks. Each control was identified through formal risk assessment, implemented following industry frameworks, tested for effectiveness, and documented with audit-ready evidence.

## Risk Register

Seven organizational risks were identified and scored using a structured likelihood (1-5) × impact (1-5) methodology. Four were selected for immediate treatment; three remain in planned status.

| Risk ID | Risk Description | Inherent Risk | Treatment | Residual Risk | Reduction |
|---------|-----------------|---------------|-----------|---------------|-----------|
| R-001 | Weak MFA enrollment exploited by phishing | 12 (High) | MFA Enforcement | 6 (Medium) | 50% |
| R-002 | Incomplete centralized logging enabling lateral movement | 15 (High) | SIEM Implementation | 8 (Medium) | 47% |
| R-004 | Inadequate endpoint protection and missing disk encryption | 12 (High) | EDR + BitLocker | 4 (Low) | 67% |
| R-012 | Daily accounts with admin privileges enabling privilege escalation | 12 (High) | Local PAM | 4 (Low) | 67% |

## Treatments Implemented

### Treatment 1: Multi-Factor Authentication (R-001)
- **Platform:** ZITADEL Cloud (Identity Provider)
- **What I Did:** Enabled organization-wide MFA policy with TOTP enforcement. Created test user, verified mandatory MFA enrollment on first login, confirmed OTP requirement for subsequent authentication.
- **Baseline State:** MFA enforcement disabled; password-only authentication.
- **Framework Alignment:** NIST CSF PR.AC-7 | CIS Control 6.3 | SOC 2 CC6.1 | HIPAA § 164.312(a)(2)(i)

### Treatment 2: SIEM / Centralized Logging (R-002)
- **Platform:** Grafana Cloud Logs (HTTP endpoint)
- **What I Did:** Configured Grafana Cloud Logs HTTP endpoint with authenticated ingestion and secure token storage. Sent test logs via PowerShell with JSON payload, verified HTTP 204 success response, confirmed log searchability in Grafana Explore interface.
- **Baseline State:** No SIEM or centralized logging infrastructure.
- **Framework Alignment:** NIST CSF DE.CM-1 | CIS Control 8.2, 8.6 | SOC 2 CC7.2, CC7.3 | HIPAA § 164.312(b)

### Treatment 3: Endpoint Detection & Full Disk Encryption (R-004)
- **Platform:** Windows Defender + BitLocker
- **What I Did:** Verified and enabled real-time monitoring, behavior monitoring, IOAV protection, and tamper protection. Enabled BitLocker with TPM protection. Tested with EICAR test file to verify detection and automatic quarantine.
- **Baseline State:** Basic Defender protection active, BitLocker not enabled.
- **Framework Alignment:** NIST CSF PR.DS-1 | CIS Control 10.1, 10.5 | SOC 2 CC6.6 | HIPAA § 164.312(a)(2)(iv)

### Treatment 4: Local Privileged Access Management (R-012)
- **Platform:** Windows Local User Management
- **What I Did:** Created emergency breakglass account with admin rights, removed daily-use account from Administrators group, verified changes via PowerShell, tested standard user functionality.
- **Baseline State:** Daily-use account with full Administrator privileges, no emergency access account.
- **Framework Alignment:** NIST CSF PR.AC-4 | CIS Control 5.4 | SOC 2 CC6.2 | HIPAA § 164.308(a)(3)

## Key Deliverables

- Formal risk register with 7 identified risks scored by likelihood and impact
- 4 fully implemented and tested security controls
- Audit-ready evidence documentation (screenshots of baseline state, configuration changes, and post-implementation verification for each control)
- Framework mapping to NIST CSF, CIS Controls, ISO 27002, SOC 2, and HIPAA Security Rule
- Business impact analysis for each treatment including cost/risk reduction rationale

## Tools & Technologies

ZITADEL IdP, Grafana Cloud Logs, PowerShell, Windows Defender, BitLocker, Windows Local User Management

## Contact

- [LinkedIn](https://www.linkedin.com/in/jonathanwdoolangrc)
- Email: doolanjw0@gmail.com
