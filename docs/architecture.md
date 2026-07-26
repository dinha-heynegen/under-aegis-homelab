# Architecture — Under-Aegis

> Full network design and rationale behind the segmentation choices. All IP ranges, hostnames, and domain names in this document are anonymized/templated.

---

## Overview

Under-Aegis is a self-hosted homelab virtualized on Proxmox VE, protected by an OPNsense firewall enforcing zero-trust segmentation across five VLANs.

---

## Network Segmentation

| VLAN | Purpose |
|---|---|
| Themis (VLAN10) | *TBD* |
| Gaia (VLAN20) | *TBD* |
| Eos (VLAN30) | *TBD* |
| Eris (VLAN40) | *TBD* |
| Kalypso (VLAN50) | *TBD* |

---

## Zero-Trust Rationale

*TBD — explanation of inter-VLAN rules, default-deny policy, and why the offensive/vulnerable segment is fully isolated.*

---

## IP Addressing Scheme (sanitized)

*TBD — documentation-safe ranges, e.g. 192.0.2.0/24, used as placeholders for the real scheme.*

---

## Notes

This document is a work in progress and will be expanded as the lab evolves.
