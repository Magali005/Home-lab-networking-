# Lab 6 - Access Control Lists (ACL)

**Objective:** Block a specific network from reaching a specific server while allowing all other traffic to pass normally.

**Topology:** Uses the same topology as Lab 5 (3 networks connected via 2 routers).

**Goal:** Block PC6/PC7 (network C, 192.168.40.0/24) from reaching Server0 (192.168.10.10) on network A, while keeping access open for PC4/PC5 (network B).

**ACL Configuration (on Router1):**

access-list 100 deny ip 192.168.40.0 0.0.0.255 host 192.168.10.10
access-list 100 permit ip any any

interface gigabitEthernet0/1
ip access-group 100 in

**Troubleshooting notes:**
1. Forgot the space in the wildcard mask (192.168.40.0.0.0.255), causing an invalid input error. Corrected by adding the space (192.168.40.0 0.0.0.255).
2. Typed permit any any without specifying the protocol, causing an invalid input error. Corrected to permit ip any any.

**Test Results:**

Before ACL - Ping PC6 to Server0 (192.168.10.10): 0% loss - SUCCESS

After ACL applied:
Ping PC6 to Server0 (192.168.10.10): Destination host unreachable, 100% loss - BLOCKED as expected
Ping PC4 to Server0 (192.168.10.10): 0% loss - SUCCESS (unaffected, confirms ACL is selective)

**Key takeaway:** ACLs allow granular control over network traffic, blocking specific source and destination combinations while leaving all other traffic unaffected. The final permit ip any any line is critical, since ACLs deny all traffic by default once any rule is applied. ACLs should generally be applied as close to the source of the traffic being filtered as possible.

**Status:** Completed
![Lab 1 Topology](images/lab1-topology.png)
![Lab 1 Ping Result](images/lab1-ping-result.png)
