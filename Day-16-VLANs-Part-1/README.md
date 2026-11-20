# Day 16: VLANs (Part 1)

## Lab Objectives
* Understand the role of VLANs in segmenting Layer 2 broadcast domains.
* Create and name VLANs on a Cisco switch via the CLI.
* Configure switch interfaces as **Access ports** and assign them to their respective VLANs using `interface range`.
* Verify the VLAN configuration and test network connectivity within the same VLAN and across different VLANs.

---

## VLAN & Addressing Plan

| VLAN ID | Name | Subnet | Assigned Ports (Example) |
| :--- | :--- | :--- | :--- |
| **10** | `ENGINEERING` / `SALES` | `10.0.0.0/26` | `Fa0/1 - 4` |
| **20** | `HR` / `MARKETING` | `10.0.0.64/26` | `Fa0/5 - 8` |
| **30** | `IT` / `MANAGEMENT` | `10.0.0.128/26` | `Fa0/9 - 12` |

*(Note: Adjust the VLAN names and interface ranges to match the exact Packet Tracer lab topology.)*

---

## CLI Configuration (Switch)

```ios
enable
configure terminal

! 1. Create and name VLANs
vlan 10
 name ENGINEERING
vlan 20
 name HR
vlan 30
 name IT
exit

! 2. Configure Access ports for VLAN 10
interface range fastEthernet 0/1 - 4
 switchport mode access
 switchport access vlan 10
exit

! 3. Configure Access ports for VLAN 20
interface range fastEthernet 0/5 - 8
 switchport mode access
 switchport access vlan 20
exit

! 4. Configure Access ports for VLAN 30
interface range fastEthernet 0/9 - 12
 switchport mode access
 switchport access vlan 30
exit

! 5. Save the configuration
end
write memory
