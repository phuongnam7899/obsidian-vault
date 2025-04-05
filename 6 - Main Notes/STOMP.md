2025-01-20 08:58

Tags: [[WebSocket]] [[Protocol]] [[Networking]]

---

- Stands for: Simple Text Oriented Message Protocol
- Is a protocol for messaging over WebSockets
- Key features:
  - Simple text-based format -> easy to read and debug
  - Inter-operability: STOMP clients can communicate with any STOMP-compliant message broker
  - Web socket support: to enable real-time messaging
  - Message models: support both point-to-point (queues) and pub-sub
- Commands:
  - CONNECT: establish connection with the message broker
  - SEND: Send message to destination (topic/queue)
  - SUBSCRIBE: Subscribe to a destination to receive messages
  - UNSUBSCRIBE: unsubscribe from a destination
  - DISCONNECT: Close connection with message broker

---

# References
