# 🏴 Homelab Journey — T0L9U4RD

> Career changer. FiSi Trainee (IT System Integration, IHK).
> Intern @ SinCera Tech GmbH. CEH Candidate. Road to OSCP.

## 🔧 Current Setup

| Component | Hardware | Role |
|---|---|---|
| Hypervisor | HP ProLiant DL380 G7 | Proxmox VE |
| Firewall | Protectli VP2430 | OPNsense |
| Backbone Switch | Dell Force10 S55 | VLAN Backbone |
| Storage | HP ProLiant DL160 G6 | TrueNAS SCALE |
| Monitoring | Dell OptiPlex 3010 | Grafana + Prometheus |

## 🌐 Network Segmentation

| VLAN | Subnet | Purpose |
|---|---|---|
| VLAN10 | Management | Network management |
| VLAN20 | 10.0.20.0/24 | Server / VMs |
| VLAN30 | 10.0.30.0/24 | Security Lab (isolated) |
| VLAN40 | Home | Home network |

## 💻 Virtual Machines

| VM | OS | IP | Purpose |
|---|---|---|---|
| DC01 | Windows Server 2022 | 10.0.20.x | Active Directory (lab.local) |
| VM101 | Ubuntu Server 24.04 | 10.0.20.x | Linux Server |
| VM102 | Kali Purple 2026.1 | 10.0.30.10 | Attack Platform |
| VM103 | Metasploitable 3 | 10.0.30.20 | Vulnerable Target |
| monitoring-01 | Debian 13 | 10.0.20.50 | Grafana + Prometheus |

## 🎯 Learning Path

```
FiSi AP1: 30.09.2026
FiSi AP2: 25./26.05.2027
CEH v13:  ~Juli 2026
HTB CJCA: 21.5% completed ✅
HTB CPTS: → nach CJCA
OSCP:     2028/2029
```

## 📂 Repository Structure

```
homelab-journey/
├── network/          # VLAN configs, firewall rules, topology
├── monitoring/       # Grafana dashboards, Prometheus configs
├── active-directory/ # AD/GPO setups, lab.local configs
├── incidents/        # What broke, what I learned
└── docs/             # General documentation
```

## 🔗 Links

- HTB Profile: [hackthebox.com/u/T0L9U4RD](#)
- LinkedIn: [linkedin.com/in/TODO](#)

---
*This is a learning journey, not a polished product.*
*Mistakes included.*
