# CCNA Lab: Day 11 - Configuring Static Routes

## 📌 Objective
The goal of this lab is to configure basic device settings, assign IPv4 addresses exclusively via the Command Line Interface (CLI), verify interface states, and establish end-to-end connectivity across multiple networks using static routing.

## 🛠️ Topology & Scope
* **Routers:** Configured interface IP addresses (`G0/0` and `G0/1`) and static routes.
* **Switches:** Applied basic administrative configurations (hostnames and port management) for practice and consistency.

## 📝 Configuration Steps & Execution

### 1. Basic Device & Switch Administration
* Configured `hostname` identifiers on all routers and switches to maintain clear CLI navigation.
* Performed foundational switch configurations to reinforce previously learned Layer 2 CLI skills.

### 2. CLI Interface Configuration & `no shutdown` Verification
* Transitioned fully from GUI configuration to pure CLI for assigning IPv4 addresses and subnet masks on router interfaces (`G0/0` and `G0/1`).
* Verified the impact of the `no shutdown` command:
  * **Before `no shutdown`:** `show ip interface brief` displays `Status: administratively down` and `Protocol: down`.
  * **After `no shutdown`:** Once connected to an active link, both states transition to `up / up`.

### 3. Static Routing Implementation
* Utilized Cisco IOS Context-Sensitive Help (`?`) to verify the exact command structure while building routing entries.
* Configured static routes in global configuration mode to allow routers to forward traffic to remote networks:
  ```text
  ip route [destination-network] [subnet-mask] [next-hop-ip | exit-interface]
