# Lab 3 — Basic VLANs

**Objective:** Segment a switch into two VLANs to isolate traffic between 
two departments (Marketing and IT).

**Topology:** PC0, PC1, PC2, PC3 — Switch0 — Server0

**VLAN Configuration:**
| VLAN | Name      | Ports         |
|------|-----------|---------------|
| 10   | Marketing | Fa0/1, Fa0/2  |
| 20   | IT        | Fa0/4, Fa0/5  |

**IP Addressing:**
- VLAN 10 (Marketing): 192.168.10.0/24
- VLAN 20 (IT): 192.168.20.0/24

**Troubleshooting note:**
Initially assigned port Fa0/4 to the wrong VLAN (10 instead of 20). 
Corrected by re-entering interface configuration mode and reassigning 
the port with `switchport access vlan 20`. Verified the fix using 
`show vlan brief`.

**Test Results:**
**Key takeaway:** VLANs isolate broadcast domains and traffic even when 
devices share the same physical switch, which is used in real networks 
to separate departments for security and organization.

**Status:** ✅ Completed
