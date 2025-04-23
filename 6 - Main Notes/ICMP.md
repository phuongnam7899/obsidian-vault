2025-04-05 14:40

Tags: [[Networking]]

---

- Internet Control Message Protocol
- is a [[network layer]] protocol
- used for **diagnostic and control** purposes

# Use cases

```mermaid
graph TB
    ICMP["ICMP Protocol"] 
    --> D["Network Diagnostics"]
    --> T["Troubleshooting"]
    --> M["Monitoring"]
    --> E["Error Reporting"]
    
    D --> D1["ping"]
    D --> D2["traceroute"]
    
    T --> T1["Connectivity Tests"]
    T --> T2["Path Analysis"]
    
    M --> M1["Network Health"]
    M --> M2["RTT Measurement"]
    
    E --> E1["Host Unreachable"]
    E --> E2["Port Unreachable"]
```

# Benefit
✓ Network diagnostics
✓ Error reporting
✓ Path discovery
✓ Network testing
✓ Performance measurement

# Limitation
× Can be blocked by firewalls
× Security concerns
× Limited bandwidth usage
× Not for data transfer
× Can be rate limited


---
# References