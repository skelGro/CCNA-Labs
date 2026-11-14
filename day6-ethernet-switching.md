🛠️ Step-by-Step Execution & Analysis

1. Packet Flow Analysis (PC1 pinging PC3)

The Problem: Because PC1's ARP table was initially empty, it did not know the Layer 2 MAC address associated with PC3's IP address (192.168.1.3).

The Sequence:

ARP Request (Broadcast): PC1 generated an ARP Request using the broadcast MAC address (FFFF.FFFF.FFFF). The switch performed flooding, forwarding the frame out of all active ports except the receiving port. Every device on the local network received it.

ARP Reply (Unicast): PC3 recognized its own IP address and responded with a direct unicast ARP Reply containing its MAC address.

ICMP Traffic: With the MAC address resolved, PC1 transmitted the actual ICMP Echo Request (ping), which was acknowledged by an ICMP Echo Reply from PC3.

2. Simulation Mode Verification

I verified the theoretical packet flow using Cisco Packet Tracer's Simulation Mode:

Initiated a ping from PC1 (Desktop > Command Prompt) to PC3 (ping 192.168.1.3).

Inspected the Protocol Data Units (PDUs) at each step to examine the Ethernet Header (Source/Destination MAC fields) and Ethernet Trailer (FCS / CRC).

3. Dynamic MAC Learning

To populate the switches' MAC address tables, I generated ICMP traffic across the network. This forced the switches to inspect incoming frames, read the Source MAC addresses, and map them to their respective incoming interface ports.

4. CLI Verification Commands

I accessed the switch Command Line Interface (CLI) in Privileged EXEC mode to inspect the results:

Switch# show mac address-table dynamic


The switch successfully displayed all dynamically learned MAC addresses mapped to their respective interface ports. (Note: show mac address-table static returned no entries since no static bindings were configured).

5. Clearing the MAC Table

To reset the switches to their initial state and test dynamic re-learning, I executed:

Switch# clear mac address-table dynamic


After executing this command, the MAC address tables were verified as completely empty, concluding the lab.
