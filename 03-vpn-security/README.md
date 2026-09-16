# Module 03: VPN Security & Zero-Trust Remote Access

> Virtual Private Networks (VPNs) create an encrypted tunnel between remote users and internal network resources. However, modern security paradigms are transitioning from traditional VPNs to Zero Trust Network Access (ZTNA).

---

## 🔒 1. VPN Hardening Fundamentals

| Security Control | Threat Mitigated | Best Practice Recommendation |
| :--- | :--- | :--- |
| **Mandatory MFA** | Credential Theft & Password Spraying | Enforce FIDO2 Hardware Keys or Push Notifications with Number Matching. Disable SMS/Voice MFA. |
| **Host Health Checks (Posture)** | Compromised Remote Endpoint Access | Verify endpoint compliance (Active EDR, Disk Encryption enabled, OS updated) before granting tunnel access. |
| **Certificate-Based Auth** | Unauthorized Rogue Devices | Combine user credentials with device-specific PKI client certificates. |
| **Session Inactivity Timeouts** | Unattended Session Hijacking | Terminate idle VPN sessions after 15–30 minutes of inactivity. |

---

## ⚡ 2. Split-Tunneling vs. Full-Tunneling

```
FULL-TUNNEL:
[Remote User] --(Encrypted Tunnel)--> [Corporate Firewall] --> [Internet]

SPLIT-TUNNEL:
[Remote User] --(Encrypted Tunnel)--> [Corporate Network]
              \----------------------> [Direct Internet Access]
```

* **Full-Tunneling (Higher Security)**: All user internet traffic is routed through the corporate VPN firewall. Allows full inspection, DLP, and URL filtering, but increases bandwidth consumption.
* **Split-Tunneling (Higher Performance)**: Only internal enterprise subnet traffic goes through the tunnel; internet traffic bypasses the corporate firewall. **Risk**: Compromised user browsing can infect endpoint while connected to corporate network.

---

## 🛡️ 3. Transitioning from VPN to ZTNA (Zero Trust Network Access)

| Dimension | Legacy VPN | Zero Trust Network Access (ZTNA) |
| :--- | :--- | :--- |
| **Access Model** | Network-level access (User gains visibility to whole subnet). | App-level access (User connects only to specific authorized app). |
| **Trust Assumption** | Implicit trust inside the tunnel. | Never trust, always verify every request. |
| **Visibility** | Hides user from external internet, reveals internal LAN. | Micro-segments application access, keeping internal network dark. |
