\# Firewall Rules



\## Interface Overview



| Interface   | VLAN | Subnet             | Purpose                          |

|-------------|------|---------------------|-----------------------------------|

| LAN\_TRUSTED | 10   | 192.168.10.0/24     | Trusted personal devices          |

| IOT         | 20   | 192.168.20.0/24     | IoT devices, isolated from trust  |

| GUEST       | 30   | 192.168.30.0/24     | Guest Wi-Fi, fully isolated       |



!\[Interface assignments](../screenshots/interface\_assignments.png)



\## LAN\_TRUSTED Rules

Trusted devices have unrestricted outbound access, including to other VLANs.



!\[LAN\_TRUSTED rules](../screenshots/LAN\_TRUSTED\_rules.png)



| Rule | Source | Destination | Action |

|------|--------|-------------|--------|

| Allow LAN\_TRUSTED to anywhere | LAN\_TRUSTED subnets | Any | Pass |



\## IOT Rules

IoT devices can reach the internet but are blocked from both other internal 

VLANs, limiting the blast radius of a compromised IoT device.



!\[IOT rules](../screenshots/IOT\_rules.png)



| Rule | Source | Destination | Action |

|------|--------|-------------|--------|

| Block IOT to LAN\_TRUSTED | IOT subnets | 192.168.10.0/24 | Block |

| Block IOT to GUEST | IOT subnets | 192.168.30.0/24 | Block |

| Allow IOT to internet | IOT subnets | Any | Pass |



\## GUEST Rules

Guest network is fully isolated from internal VLANs, internet-only.



!\[GUEST rules](../screenshots/GUEST\_rules.png)



| Rule | Source | Destination | Action |

|------|--------|-------------|--------|

| Block GUEST to LAN\_TRUSTED | GUEST subnets | 192.168.10.0/24 | Block |

| Block GUEST to IOT | GUEST subnets | 192.168.20.0/24 | Block |

| Allow GUEST to internet | GUEST subnets | Any | Pass |



\## Rule Ordering

pfSense evaluates rules top-down, first match wins. Block rules are placed 

above the general "allow to internet" rule on both IOT and GUEST — otherwise 

the permissive rule would match first and the blocks would never be reached.

