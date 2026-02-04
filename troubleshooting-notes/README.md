## Troubleshooting Scenarios:

"Local Network Works, Internet Does Not"

### Problem Description
A user reports that their device is connected to the local network and can communicate with other internal devices, but cannot access any internet resources.

Observed behavior:
- Active Ethernet/Wi-Fi connection
- Successful communication with local hosts
- All external websites fail to load

This indicates that basic connectivity exists, but traffic is failing beyond the local network.

---

### Initial Layer Elimination (OSI-Based)

**Layer 1 – Physical**  
The device has an active link and is transmitting data. No physical connectivity issue is present.

**Layer 2 – Data Link**  
Local communication succeeds, confirming that ARP resolution and switch forwarding are working correctly.

Because both Layer 1 and Layer 2 are functioning, the issue is unlikely to be related to cabling, NICs, or switching.

---

### Suspected Layer

**Layer 3 – Network**

Internet access requires routing traffic outside the local subnet. If a device can reach local hosts but not remote networks, the problem is likely related to routing or gateway configuration.

---

### Packet Flow Explanation

When a device attempts to reach an external destination:
1. The destination IP is evaluated against the local subnet
2. Because the address is outside the subnet, traffic is forwarded to the default gateway
3. The device ARPs
