# CCNA Lab: Day 9 - Switch & Router Interfaces Configuration

## 📌 Objective
The goal of this lab is to perform foundational configuration on Cisco routers and switches. This includes setting hostnames, hardcoding interface speeds and duplex settings, managing port states (enabling/disabling), and applying interface descriptions to maintain a well-documented topology.

## 🛠️ Topology Overview
* **R1** (Router 1)
* **SW1** & **SW2** (Layer 2 Switches)
* **End Hosts** (PCs connected to the switches)

## 📝 Configuration Steps & Execution

### 1. Hostname Configuration
Assigned clear identifiers to all network devices to ensure accurate administration.
* `R1`, `SW1`, and `SW2`

### 2. Router (R1) Configuration
* Navigated via CLI and verified interface statuses using `show ip interface brief`.
* Configured the primary GigabitEthernet interface connecting to the LAN.
* Hardcoded the link negotiation parameters:
  * `speed 1000`
  * `duplex full`
* Shut down all unused interfaces and marked them as "not in use" for security purposes.
* Saved the running configuration to NVRAM using the `write` command.

### 3. Switch (SW1 & SW2) Configuration
* Verified active connections and port statuses using `show interfaces status`.
* Applied configurations to specific ports (e.g., `G0/1`, `G0/2`) where end hosts and uplinks are connected.
* Hardcoded the interfaces to `speed 1000` and `duplex full`.
* Added interface `description` labels to easily identify connected endpoints.
* **Security Best Practice:** Disabled all unused ports by administratively shutting them down.
* Saved the configuration using the standard command:
  * `copy running-config startup-config` (or the `write` shorthand).

## 🔍 Verification Commands Used
During this lab, the following verification commands were utilized to ensure network stability and correct configuration application:
* `show running-config` (sh run) – To view current configurations in RAM.
* `show startup-config` – To verify the saved configuration in NVRAM.
* `show ip interface brief` – To quickly check L3 interface states.
* `show interfaces status` – To check L2 port negotiation (speed/duplex) and VLAN assignments.

---
*Documented as part of the CCNA 200-301 study progression.*
