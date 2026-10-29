# Lab 002: Basic Router Security & Password Precedence

Step-by-step implementation of basic Cisco IOS security, physical device interconnection, password precedence rules, and credential encryption.

---

## 🎯 Objectives & Key Concepts
* **Interconnect Devices:** Connect two Cisco routers via GigabitEthernet interfaces.
* **Hostnames:** Assign unique identifiers (`R1` and `R2`).
* **Password Precedence:** Demonstrate that `enable secret` always overrides `enable password`.
* **Credential Encryption:** Compare Type 5 (MD5 hash) against Type 7 reversible cipher via `service password-encryption`.
* **State Persistence:** Save changes from volatile RAM to non-volatile NVRAM.

---

## 🛠️ Topology
* **Devices:** 2x Cisco 2911 Routers (`R1` and `R2`)
* **Connection:** `R1 (G0/0)` $\leftrightarrow$ `R2 (G0/0)` (Copper Straight-Through / Crossover)
