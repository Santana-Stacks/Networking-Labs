# Lab 03: LAN with Router (Gateway Intro)

**Date:** 2025-11-05  
**Tool:** Cisco Packet Tracer 8.x  

---

## 🎯 Goal
Connect two separate LANs using a router as the default gateway and verify cross-subnet communication.

---

## 🛠️ Steps
1. Placed **PC0**, **Router 1941**, and **PC1** in the workspace.  
   ![Topology before cables](./01-topology-before-cables.png)

2. Connected PCs to the router using **Copper Straight-Through** cables  
   (PC0→Gi0/0, PC1→Gi0/1).  
   ![Cables connected](./02-cables-connected.png)

3. Configured router interfaces with IPs and enabled them.  
   ![Router config](./03-router-config.png)

4. Verified both interfaces were **up/up**.  
   ![Interfaces up](./04-interfaces-up.png)

5. Assigned static IPs and default gateways to each PC.  
   - PC0 → 192.168.1.2 /24  GW 192.168.1.1  
   - PC1 → 192.168.2.2 /24  GW 192.168.2.1  
   ![PC0 config](./05-pc0-ip-config.png)  
   ![PC1 config](./06-pc1-ip-config.png)

6. Tested ping from **PC0 → PC1** (first ping 1 lost = ARP delay).  
   ![Initial ping](./07-pc0-ping-initial.png)  
   Retested → 4 success.  
   ![Ping success](./08-pc0-ping-success.png)

7. Verified reverse ping from **PC1 → PC0**.  
   ![PC1 ping success](./09-pc1-ping-success.png)

8. Checked router tables.  
   ![Router route and ARP](./10-router-route-and-arp.png)

---

## ✅ Results
- Router correctly routed packets between **192.168.1.0/24** and **192.168.2.0/24**.  
- ARP learning confirmed at both router interfaces.  
- First ICMP packet dropped due to ARP, subsequent pings succeeded.  

---

## 🔑 Key Takeaways
- Each subnet needs its **own gateway** (router interface).  
- PCs must point to that gateway for off-network traffic.  
- The router’s `show ip route` shows directly-connected networks.  
- ARP resolves MAC addresses before communication starts.
