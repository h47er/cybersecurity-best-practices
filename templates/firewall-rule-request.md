# 📄 Firewall Rule Change Request Form

**Ticket / Change Request ID**: `CR-________`  
**Requestor**: `[Name / Department]`  
**Date Submitted**: `YYYY-MM-DD`  
**Target Execution Date**: `YYYY-MM-DD`  
**Business Justification**: `[Detailed description of application or service requiring rule]`  

---

## ⚙️ 1. Proposed Firewall Rule Specifications

| Direction | Source IP / Subnet | Destination IP / Subnet | Protocol & Port | Action | Expiration Date |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `Inbound / Outbound` | `10.x.x.x/24` | `192.168.x.x` | `TCP / 443` | `ALLOW / DENY` | `Permanent / YYYY-MM-DD` |

---

## 🛡️ 2. Security Risk Assessment

- [ ] Does this rule allow traffic from the **Public Internet** directly to an internal subnet? *(Requires SecOps Approval)*
- [ ] Is destination traffic using **unencrypted protocols** (e.g., Telnet/23, HTTP/80, FTP/21)? *(If yes, request encryption)*
- [ ] Are source and destination definitions restricted to specific host IPs rather than broad CIDRs?

---

## ⏪ 3. Rollback & Verification Plan

* **Verification Step**: `nc -zv <Destination_IP> <Port>` from source host.
* **Rollback Action**: Disable/Delete rule `CR-________` from Firewall Policy Management console.

---

## ✍️ Approvals

* **Network Administrator**: `[Approved / Denied]` - `Date: _______`
* **Information Security Officer**: `[Approved / Denied]` - `Date: _______`
