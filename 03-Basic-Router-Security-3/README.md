# Day 03: Basic Router Security Configuration

**Source:** Jeremy's IT Lab (CCNA 200-301)  
**Tools:** Cisco Packet Tracer  

## Objective
Secure basic administrative access to a Cisco router via a console connection by setting a hostname, configuring an encrypted Privileged EXEC password (`enable secret`), enforcing console line authentication, encrypting plaintext passwords, and saving the configuration to NVRAM.

## Topology & Physical Connection
* **Connection:** PC1 (`RS-232`) ── *(Console / Rollover cable)* ── R1 (`Console`)
* **Terminal Settings:** Default serial parameters (`9600` baud rate, 8 data bits, no parity, 1 stop bit, no flow control)

---

## Configuration Steps

### 1. Set Hostname & Privileged EXEC Password
Enter Global Configuration mode, rename the router to `R1`, and configure an MD5-hashed (Type 5) `enable secret` password:

```text
Router> enable
Router# configure terminal
Router(config)# hostname R1
R1(config)# enable secret cisco
```

### 2. Configure Console Line Password & Login Enforcement
Set the console password to `ccna` and enable password checking upon console connection using the `login` command:

```text
R1(config)# line console 0
R1(config-line)# password ccna
R1(config-line)# login
R1(config-line)# exit
```

### 3. Check Running Configuration (Before Encryption)
Inspect the running configuration to check whether the console password is encrypted:

```text
R1(config)# do show running-config
```

* **Observation:** The `enable secret` is stored as a Type 5 (MD5) hash, while the `line console 0` password (`ccna`) is still visible in **plaintext**.

### 4. Enable Password Encryption
Encrypt all current and future plaintext passwords in the configuration using Cisco's Type 7 encryption:

```text
R1(config)# service password-encryption
R1(config)# end
```

### 5. Verify & Save Configuration
Confirm that the console password is now obfuscated in the running configuration, then save the active configuration to NVRAM (`startup-config`):

```text
R1# show running-config
R1# copy running-config startup-config
```

*(Shorthand alternative: `write memory` or `wr`)*

---

## Verification & Testing
1. Verified in `show running-config` that `enable secret` uses **Type 5** hashing and `line console 0` password uses **Type 7** encryption.
2. Exited the CLI (`exit`) and reconnected via PC1's Terminal to confirm the router prompts for the console password (`ccna`) before User EXEC mode, and the `enable secret` (`cisco`) before Privileged EXEC mode.

## Key Takeaways
* **`login` is mandatory on `line console 0`:** Setting a password alone does not enforce authentication on the console port until `login` is configured.
* **Type 5 vs. Type 7:** `enable secret` automatically uses stronger one-way hashing (Type 5 / MD5), whereas `service password-encryption` applies reversible Type 7 obfuscation meant primarily to prevent shoulder surfing.
* **Verify before saving:** Always inspect `show running-config` before committing changes to `startup-config` to avoid saving misconfigurations permanently.
