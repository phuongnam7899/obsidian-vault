2025-08-24 19:11

Tags: [[Networking]] [[Azure Cloud]] 

---

- To securely connect from your on-premises network to AZ Cloud environment
# Why need?
- Extend on-premise network
- Secure hybrid connectivity: VPN gateway encrypt the traffic
- Resilient Connection: 
	- it support multiple connections
	- configured with redundancy using Availability Zone

# Types of VPN gateway
## Policy-based
- Pre-defined policies to direct traffic through certain tunnel
- Primarily used in static configuration
## Route-based
- Use dynamically updated routing table
- Better flexibility when network traffic pattern change

# Key points to choose
## Performance and bandwidth
- Choose a VPN Gateway SKU (size) aligns with the volume and performance needed
## VPN protocols
Azure support popular protocols:
- IKEv2
- OpenVPN
## Region matters
- The region that deploy the gateway can affect the latency and connectivity cost

---
# References
- [[VPN]]
- [[Gateway]]