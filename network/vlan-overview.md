# VLAN Architecture — HomeLab

## Why VLANs?

Isolating the attack lab (Kali Purple + Metasploitable3) from
production infrastructure. VLAN30 is the "danger zone" — completely
isolated from VLAN20 where real services run.

## VLAN Table

| VLAN | Name | Subnet | Purpose | Inter-VLAN |
|---|---|---|---|---|
| 10 | Management | — | Network device mgmt | Restricted |
| 20 | Server | 10.0.20.0/24 | VMs, AD, Monitoring | Limited |
| 30 | Security Lab | 10.0.30.0/24 | Kali Purple, Metasploitable3 | BLOCKED |
| 40 | Home | — | Home devices | Separate |

## OPNsense Firewall Rules (VLAN30 — Security Lab)

```
VLAN30 → VLAN20: BLOCK ALL   ← Kali cannot reach production
VLAN30 → WAN:    ALLOW (temp) ← for package installation only
VLAN20 → VLAN30: BLOCK ALL
```

## Key Learnings

- **Inter-VLAN routing** must be explicitly enabled in OPNsense
  (disabled by default — good!)
- **VLAN30 isolation** works: Kali scans are visible in Grafana
  but cannot reach VLAN20 services
- **Known issue:** OPNsense blocks outbound from 10.0.20.50 (VLAN20)
  Workaround: direct Fritzbox connection for apt installs
  Root cause: still investigating

## Hardware

- **Backbone:** Dell Force10 S55 (odd-numbered ports only, cable mgmt)
- **Connected via:** Protectli VP2430 (OPNsense gateway)
- **SSH to Force10:** requires legacy cipher flags + connect via TP-Link SW

---
*Last updated: 2026-06*
