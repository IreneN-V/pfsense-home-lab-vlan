\# pfSense Home Lab — VLAN Segmentation



Home lab project: pfSense firewall configured from scratch with VLAN-based network segmentation.



\## Goal

Segment a home network into isolated VLANs (trusted LAN, IoT, Guest) to limit lateral movement 

and demonstrate firewall rule design based on least-privilege access.



\## Environment

\- pfSense (version TBD) running in VirtualBox

\- VLAN tagging (802.1Q) configured at the pfSense level on a trunked interface



\## Network Design

\*(diagram and VLAN table — coming in docs/)\*



\## What's in this repo

\- `docs/` — architecture, firewall rules, NAT config, testing results

\- `screenshots/` — configuration screenshots

\- `configs/` — sanitized pfSense config exports (no secrets)



\## Status

In progress

