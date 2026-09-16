# Module 02: Next-Gen Firewalls & Network Hardening

> Firewalls act as the primary perimeter defense and internal traffic segmentation controllers for enterprise networks.

---

## 🏗️ 1. Firewall Rule Processing Architecture

Firewall engines evaluate rules sequentially from **Top to Bottom**. Once a matching rule condition is met, execution stops, and the action (`ALLOW` or `DENY`) is taken.

```
+-------------------------------------------------------+
| Rule #1: [Explicit Deny] Any -> Malicious Threat Feeds|
+-------------------------------------------------------+
| Rule #2: [Allow] Mgmt Subnet -> Firewall Admin Port  |
+-------------------------------------------------------+
| Rule #3: [Allow] Internal Servers -> DB (Port 5432)   |
+-------------------------------------------------------+
| Rule #99: [EXPLICIT DENY ALL] Any -> Any              |
+-------------------------------------------------------+
```

---

## 🧱 2. Network Segmentation Zones

Enterprise networks must be partitioned into strict security zones to limit lateral movement by attackers:

| Security Zone | Purpose | Inbound Rules | Outbound Rules |
| :--- | :--- | :--- | :--- |
| **DMZ (Demilitarized Zone)** | Publicly accessible services (Web servers, Mail proxies). | Restricted to Ports 80/443 from Internet. | **Blocked** to Internal LAN unless explicitly required. |
| **Corporate LAN** | Employee workstations and office endpoints. | Denied from DMZ. | Allowed to Internet via Secure Web Gateway (SWG). |
| **Management Zone** | Hypervisors, Domain Controllers, Switch Management interfaces. | Only accessible from dedicated Jump Hosts / Bastions via SSH/RDP. | Strictly restricted. |
| **PCI / Sensitive Data Zone** | Systems storing credit card or PII data. | Highly restricted; multi-factor authenticated jump boxes only. | Logged and monitored 24/7. |

---

## 🛡️ 3. Firewall Policy Best Practices Checklist

- [x] **Enforce Implicit Deny**: Ensure rule `#99` / final rule is `DENY ALL ANY ANY`.
- [x] **Avoid "ANY" in Source/Destination**: Replace broad network objects with specific CIDR blocks or host tags.
- [x] **Strict Egress Filtering**: Block outbound connections on non-standard ports (e.g., prevent IRC on port 6667 or outbound SMB on port 445).
- [x] **Disable Unused Interfaces**: Shutdown administrative interfaces facing external networks.
- [x] **Rule Review Schedule**: Conduct quarterly firewall rule audits to prune temporary rules and redundant policies.
- [x] **Log All Denied Traffic**: Ensure dropped packet logging is enabled for threat hunting and forensic analysis.
