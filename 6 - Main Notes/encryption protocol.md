2025-08-24 20:09

Tags: [[Networking]] [[Security]]

---

# Flow
```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant CA as Certificate Authority

    Note over Client, Server: TLS/SSL Handshake Process
    
    Client->>Server: 1. Client Hello<br/>(TLS version, cipher suites, random number)
    
    Server->>Client: 2. Server Hello<br/>(Selected TLS version, cipher suite, random number)
    
    Server->>Client: 3. Server Certificate<br/>(Public key + CA signature)
    
    Server->>Client: 4. Server Hello Done
    
    Note over Client: Client validates certificate
    Client->>CA: 5. Certificate Verification<br/>(Optional: OCSP/CRL check)
    CA-->>Client: Certificate Status
    
    Client->>Server: 6. Client Key Exchange<br/>(Pre-master secret encrypted with server's public key)
    
    Note over Client, Server: Both generate master secret from:<br/>• Client random<br/>• Server random<br/>• Pre-master secret
    
    Client->>Server: 7. Change Cipher Spec<br/>(Switch to encrypted communication)
    
    Client->>Server: 8. Finished<br/>(Encrypted handshake verification)
    
    Server->>Client: 9. Change Cipher Spec<br/>(Confirm encrypted communication)
    
    Server->>Client: 10. Finished<br/>(Encrypted handshake verification)
    
    Note over Client, Server: Secure Data Transmission
    
    loop Application Data Exchange
        Client->>Server: Encrypted Application Data<br/>(Using symmetric encryption)
        Server->>Client: Encrypted Application Data<br/>(Using symmetric encryption)
    end
    
    Note over Client, Server: Session Termination
    Client->>Server: Close Notify Alert
    Server->>Client: Close Notify Alert
```
## Handshake Initiation (Steps 1-4)
- Client sends supported TLS versions and cipher suites
- Server responds with selected parameters and its certificate
- Certificate contains the server's public key
## Certificate Verification
- Client validates the server's certificate against trusted CAs
- May check certificate revocation status
## Key Exchange
- Client generates a pre-master secret
- Encrypts it with server's public key and sends it
- Only the server can decrypt this with its private key
## Session Key Generation
- Both parties independently generate the same master secret
- Uses client random (random number from client's initial message) + server random (random number from server's response) + pre-master secret
- Master secret is used to derive symmetric encryption keys
## Handshake Completion
- Both parties switch to encrypted communication
- Exchange encrypted "Finished" messages to verify handshake integrity
## Secure Data Exchange
- All application data is encrypted using symmetric encryption
- Much faster than asymmetric encryption used in handshake
## Session Termination
- Graceful closure with encrypted close notifications

---
# References
- [[Session management strategies]]