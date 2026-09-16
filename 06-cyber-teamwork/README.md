# Module 06: Cyber Teamwork & Incident Collaboration

> Cybersecurity is a team sport. Technical expertise must be matched with clear communication, standardized handovers, and structured incident escalation workflows.

---

## 💬 1. Ticket Documentation Standards (SBAR Format)

When documenting security incident tickets or escalating to Tier 2 / Incident Response teams, use the **SBAR Framework**:

* **`S` - Situation**: What is happening right now? (e.g., *"High-severity SIEM alert triggered for potential Mimikatz execution on host WORKSTATION-84."*)
* **`B` - Background**: What context is relevant? (e.g., *"User `j.smith` logged in via RDP at 14:20 from an internal IP address. Host was missing Endpoint EDR agent updates."*)
* **`A` - Assessment**: What did your initial investigation reveal? (e.g., *"Event 4688 confirms `lsass.exe` memory dump attempt by `powershell.exe`. VirusTotal flag on hash: 54/70 detection."*)
* **`R` - Recommendation**: What action should be taken next? (e.g., *"Isolate WORKSTATION-84 from network immediately, revoke `j.smith` active tokens, and initiate forensic image capture."*)

---

## 🔄 2. SOC Shift Handover Protocol

Miscommunications during shift changeovers lead to dropped alerts and delayed incident containment.

### Shift Change Checklist
- [x] **Open High-Severity Incidents**: Review active tickets requiring ongoing monitoring.
- [x] **Pending Change Windows**: Note upcoming network maintenance, firewall rule pushes, or server patching scheduled during the incoming shift.
- [x] **SIEM & Tool Status**: Report any ongoing log ingestion delays or agent outages.
- [x] **VIP & Threat Advisory Watch**: Highlight active zero-day threats or high-risk user monitoring alerts.

*(See the full operational template in [`/templates/shift-handover-template.md`](../templates/shift-handover-template.md))*

---

## 🤝 3. Cross-Functional Collaboration

Cybersecurity teams work constantly alongside adjacent IT departments:

| Partner Team | Key Touchpoints | Collaboration Best Practices |
| :--- | :--- | :--- |
| **System Administrators** | Patching, GPO updates, Server Hardening | Provide clear CVE impact context and prioritize patches by business risk rather than just sending raw vulnerability lists. |
| **Network Engineers** | Firewall changes, VLAN routing, VPN issues | Use pre-approved change templates with exact IP/Port specs and pre-calculated rollback steps. |
| **DevOps & Cloud Engineers** | IAM roles, Azure resources, Container security | Integrate security checks into CI/CD pipelines early ("Shift Left") rather than blocking deployments late. |
| **Helpdesk / Tier 1 IT** | User account locks, Phishing reports, Endpoint isolation | Provide Tier 1 with clear playbooks to handle user phishing triage and initial account resets safely. |
