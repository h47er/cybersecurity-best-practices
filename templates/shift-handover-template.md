# 📋 SOC Shift Handover Report Template

**Date / Time**: `YYYY-MM-DD HH:MM UTC`  
**Outgoing Analyst**: `[Name / ID]`  
**Incoming Analyst**: `[Name / ID]`  
**Shift**: `[Day / Night / Weekend]`  

---

## 🔴 1. Active / Unresolved Incidents (P1 / P2)

| Incident ID | Severity | Target Host / User | Summary of Actions Taken | Next Steps Required |
| :--- | :--- | :--- | :--- | :--- |
| `INC-10492` | **P1 - High** | `SRV-SQL-02` | Isolated host via EDR. Memory dump captured. | Forensic analysis of suspicious LSASS access. |
| `INC-10498` | **P2 - Medium** | `user.name` | Password reset initiated. Token revoked. | Verify MFA re-enrollment with user. |

---

## 🟡 2. Ongoing Maintenance & Change Windows

* [ ] Firewall Policy Update scheduled for `22:00 UTC` (Change Request `CR-8841`). Expect brief log noise from subnet `10.4.0.0/24`.
* [ ] Domain Controller reboot ring active (`23:00 - 01:00 UTC`).

---

## 🟢 3. Health & Tooling Status

* **SIEM Log Ingestion**: `Normal / Degradation / Interrupted`
* **EDR Console**: `Healthy`
* **Email Gateway**: `Healthy`

---

## 📝 4. General Notes & Handover Sign-off

```
[Outgoing Analyst Sign-off]: ___________________
[Incoming Analyst Sign-off]: ___________________
```
