2025-04-05 13:48

Tags: [[Networking]]

---

- Transmission Control Protocol
- a **connection-oriented** protocol that **ensures reliable data delivery**

# Key characteristic

- Connection oriented:
  - Establish connection before send data
  - Maintain connection during transferring data
  - Close connection after completion
- Reliable:
  - Guarantee delivery
  - Orders packets correctly
  - Check for errors
  - Retransmit lost packets

# TCP Handshake (Connection Establish)

```mermaid
sequenceDiagram
    participant Client
    participant Server
    Client->>Server: SYN (Synchronize)
    Server->>Client: SYN-ACK (Synchronize-Acknowledge)
    Client->>Server: ACK (Acknowledge)
    Note over Client,Server: Connection Established
```

# Use cases

```mermaid
graph TD
    TCP[TCP Protocol] --> Web[Web Browsing]
    TCP --> Email[Email]
    TCP --> FTP[File Transfer]
    TCP --> SSH[Secure Shell]
    TCP --> DB[Database Connections]
```

---

# References

- [[Common TCP Ports]]
- [[TCP vs UDP]]
