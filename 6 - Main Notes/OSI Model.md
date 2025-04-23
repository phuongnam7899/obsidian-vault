2025-04-05 14:10

Tags: [[Networking]]

---

```mermaid
graph LR
    subgraph "OSI Model"
        direction LR
        
        L7["Layer 7 - Application<br/>HTTP, FTP, SMTP, DNS<br/>⚙️ User Interface & Services"] -->
        L6["Layer 6 - Presentation<br/>SSL/TLS, JPEG, ASCII<br/>🔄 Data Format & Encryption"] -->
        L5["Layer 5 - Session<br/>NetBIOS, SQL<br/>🤝 Session Management"] -->
        L4["Layer 4 - Transport<br/>TCP, UDP<br/>📦 End-to-End Delivery"] -->
        L3["Layer 3 - Network<br/>IP, ICMP, Router<br/>🌐 Routing & Addressing"] -->
        L2["Layer 2 - Data Link<br/>Ethernet, Switch<br/>🔗 Node-to-Node Delivery"] -->
        L1["Layer 1 - Physical<br/>Cables, Hub<br/>📡 Physical Transmission"]
    end
```

| Layer           | Purpose                                                                    | Protocols/Standards                                                                                    | Functions                                                                                                                             |
| --------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| 7. Application  | - User interface<br>- Network services<br>- Direct user interaction        | - HTTP/HTTPS<br>- [[FTP]]/[[SFTP]]<br>- SMTP/POP3/IMAP<br>- DNS<br>- SSH<br>- [[Telnet]]<br>- [[DHCP]] | - Resource sharing<br>- Remote access<br>- Directory services<br>- Network virtual terminals<br>- File transfers<br>- Email handling  |
| 6. Presentation | - Data format translation<br>- Data representation<br>- Session encryption | - SSL/TLS<br>- JPEG, GIF, PNG<br>- ASCII, EBCDIC<br>- MPEG<br>- MIDI                                   | - Data compression<br>- Data encryption/decryption<br>- Character set conversion<br>- Media formatting<br>- Data transformation       |
| 5. Session      | - Session management<br>- Dialog control<br>- Communication coordination   | - NetBIOS<br>- SQL<br>- RPC (Remote Procedure Call)<br>- NFS<br>- SIP                                  | - Session establishment<br>- Session maintenance<br>- Session termination<br>- Authentication<br>- Authorization<br>- Synchronization |
| 4. Transport    | - End-to-end delivery<br>- Flow control<br>- Error handling                | - [[TCP]]<br>- [[UDP]]<br>- [[SCTP]]<br>- DCCP                                                         | - Segmentation/Reassembly<br>- Connection handling<br>- Error checking<br>- Flow control<br>- Packet sequencing                       |
| 3. Network      | - Logical addressing<br>- Path determination<br>- Packet forwarding        | - [[IPv4]]/[[IPv6]]<br>- ICMP<br>- IGMP<br>- OSPF<br>- BGP<br>- RIP                                    | - Packet routing<br>- IP addressing<br>- Path selection<br>- Traffic control<br>- Subnet handling                                     |
| 2. Data Link    | - Physical addressing<br>- Error detection<br>- Media access               | - Ethernet<br>- MAC addressing<br>- PPP<br>- Frame Relay<br>- ATM                                      | - Framing<br>- Physical addressing<br>- Error control<br>- Flow control<br>- Media access control                                     |
| 1. Physical     | - Bit transmission<br>- Physical topology<br>- Hardware specifications     | - RS-232<br>- Ethernet<br>- USB<br>- Bluetooth<br>- Wi-Fi                                              | - Bit transmission<br>- Signal encoding<br>- Physical connectivity<br>- Cable specifications<br>- Topology handling                   |



---
# References