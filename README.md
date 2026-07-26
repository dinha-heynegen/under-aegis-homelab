# 🛡️ Under-Aegis — Cybersecurity Homelab

> A self-hosted, segmented homelab where I build, break, and defend my own infrastructure — designing zero-trust network architecture, standing up virtualization and secure remote access, deploying detection tooling, and running a full range of offensive scenarios (network, web, and Active Directory attacks).

Hosted on **Hera**, a repurposed tower PC running **Proxmox VE**. All components follow a naming convention drawn from feminine figures in Greek mythology.

---

## 🎯 Goals

- Build hands-on experience across both **Red Team** and **Blue Team** disciplines
- Practice network segmentation and zero-trust firewall design
- Deploy and tune a SIEM for real detection engineering practice
- Prepare for **Security+** and, longer-term, the **OSCP**

---

## 🏗️ Architecture Overview

```
                        ┌──────────────────────┐
                        │   Hera (Proxmox VE)  │
                        │   Physical Host      │
                        └──────────┬───────────┘
                                   │
                        ┌──────────┴───────────┐
                        │   Athena (OPNsense)  │
                        │   Firewall / Router  │
                        └──────────┬───────────┘
                                   │
        ┌───────────┬──────────────┼──────────────┬─────────────┐
        │           │              │              │             │
   ┌────┴───┐  ┌────┴───┐    ┌─────┴────┐   ┌─────┴────┐    ┌───┴─────┐
   │ Themis │  │  Gaia  │    │   Eos    │   │   Eris   │    │ Kalypso │
   │ VLAN10 │  │ VLAN20 │    │  VLAN30  │   │  VLAN40  │    │ VLAN50  │
   └────────┘  └────────┘    └──────────┘   └──────────┘    └─────────┘
```

**Zero-trust principle:** inter-VLAN traffic is denied by default; only explicitly required flows are allowed. The Eris VLAN, which hosts the offensive toolkit and intentionally vulnerable machines, is fully isolated from the rest of the lab — a compromise there stays contained.

> 📌 IP ranges, hostnames of vulnerable targets, and domain names throughout this repo are anonymized/templated. See [`docs/architecture.md`](docs/architecture.md) for the full (sanitized) breakdown.

---

## 🧩 Components

| Name | Role |
|---|---|
| **Hera** | Proxmox VE host |
| **Athena** | OPNsense firewall/router |
| **Iris** | WireGuard VPN |
| **Nemesis** | Wazuh SIEM |
| **Astraea** | First Wazuh agent target |
| **Hestia** | Nginx reverse proxy |
| **Artemis** | Kali Linux — offensive toolkit |
| **SRV-AD-1** | Windows Server 2022 (Active Directory) |

---

## 📂 Repository Structure

```
under-aegis-homelab/
├── README.md
├── LICENSE
├── docs/
│   ├── architecture.md      # full network design, VLAN rationale
│   └── diagrams/
├── configs/
│   ├── proxmox/
│   ├── opnsense/             # Athena — firewall rules (templated)
│   ├── wazuh/                # Nemesis — SIEM rules, agent configs
│   ├── nginx/                # Hestia — reverse proxy configs (templated)
│   ├── kali/                 # Artemis — provisioning scripts, tool list
│   └── ad/                   # Windows Server — Active Directory setup notes
└── scripts/
```

---

## 🔧 Stack

- **Virtualization:** Proxmox VE
- **Firewall / Routing:** OPNsense, 5-VLAN zero-trust segmentation
- **VPN:** WireGuard
- **SIEM:** Wazuh
- **Reverse Proxy:** Nginx
- **Offensive Toolkit:** Kali Linux
- **Directory Services:** Windows Server 2022 (UEFI/TPM), Active Directory

---

## 🚧 Roadmap

- [ ] Expand Wazuh detection rules and alerting
- [ ] Build out Active Directory attack scenarios (Kerberoasting, BloodHound mapping, etc.)
- [ ] Document GoPhish phishing simulation campaigns
- [ ] Security+ certification prep
- [ ] OSCP-track exercises

---

## ⚠️ Security Note

This is a personal lab. All configuration files in this repository have been **anonymized**: real IP ranges, domain names, credentials, and certificates have been replaced with placeholders or documentation-safe values (e.g. `192.0.2.0/24`, `example.com`). The structure and logic are real; the specific values are not.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Dinha** — First-year engineering student at ESIEA, in apprenticeship. Aspiring Red Teamer.
