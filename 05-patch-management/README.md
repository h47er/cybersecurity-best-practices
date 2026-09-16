# Module 05: Patch Management & System Updates

> Unpatched vulnerabilities are one of the primary vectors for initial access and ransomware deployment. Effective patch management balances rapid remediation with operational system stability.

---

## ⏳ 1. Remediation Service Level Agreements (SLAs)

Remediation timelines must be governed by threat severity and active exploitation status:

| Severity Level | CVSS v3/v4 Score | Active Exploitation (EPSS / KEV) | Remediation SLA Target |
| :--- | :--- | :--- | :--- |
| **Emergency (Zero-Day)** | 9.0 – 10.0 | **CISA KEV Listed** | **24 – 48 Hours** |
| **Critical** | 9.0 – 10.0 | No known active exploit | **7 Days** |
| **High** | 7.0 – 8.9 | High EPSS probability | **14 Days** |
| **Medium** | 4.0 – 6.9 | Low probability | **30 Days** |
| **Low** | 0.1 – 3.9 | Informational | **60 – 90 Days** |

*Note: CISA KEV = CISA Known Exploited Vulnerabilities Catalog.*

---

## 🔄 2. Deployment Ring Model

Never deploy patches to all production hosts simultaneously. Use a staged deployment ring model:

```
[Ring 0: IT Test Lab] ---> [Ring 1: Pilot Group (5%)] ---> [Ring 2: General Business (50%)] ---> [Ring 3: Critical Prod (100%)]
     (Day 1)                      (Day 3)                             (Day 7)                            (Day 14)
```

1. **Ring 0 (Dev/Test Lab)**: Automated deployment to non-critical test systems to detect immediate blue-screens or boot failures.
2. **Ring 1 (Pilot Users)**: IT staff and volunteer tech-savvy business users.
3. **Ring 2 (General Enterprise)**: Broad deployment across non-critical production departments.
4. **Ring 3 (Critical Servers & Infrastructure)**: High-availability databases, Domain Controllers, and production clusters during approved maintenance windows.

---

## ⏪ 3. Rollback & Contingency Planning

Every patch deployment change request must include a verified **Rollback Procedure**:

* **Virtual Machines**: Create a hypervisor snapshot or backup checkpoint prior to executing patch installation.
* **Database / App Servers**: Document exact commands to uninstall KB patches (e.g., `wusa /uninstall /kb:XXXXXX /quiet`).
* **Health Verification Checklist**: Verify key service ports, application health checks, and log ingestion in SIEM immediately following reboot.
