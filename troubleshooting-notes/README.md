## Troubleshooting Scenarios;

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
3. The device ARPs for the gateway’s MAC address
4. The frame is sent to the router, which routes the packet toward the internet

If the default gateway is missing, incorrect, or unreachable, the packet never leaves the local network—even though local communication continues to function normally.

---

### Diagnostic Steps

To confirm a Layer 3 issue:
- Verify the client’s IP configuration (IP address, subnet mask, default gateway)
- Ping the default gateway
- Attempt to ping a known public IP address (bypassing DNS)
- Check router interface status and routing configuration

These steps isolate whether the failure is due to gateway misconfiguration, routing failure, or upstream connectivity issues.

---

### Resolution

The issue was resolved by correcting the default gateway configuration on the client device. Once Layer 3 routing was restored, internet connectivity resumed immediately.

---

### Why the OSI Model Matters Here

The OSI model allowed the problem to be narrowed down quickly by eliminating functioning layers and focusing on the point where traffic logically failed.

Instead of guessing, the issue was identified through structured layer-based reasoning, which is repeatable across different network environments.
