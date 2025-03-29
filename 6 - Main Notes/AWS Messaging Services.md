{{date}} {{time}}

Tags: #AWS #Cloud #Messaging

---

- AWS Messaging Services facilitate communication between application components
- These services enable decoupled and distributed application architectures

## Amazon Simple Notification Service (SNS)

- A publish/subscribe messaging service
- Key characteristics:
  - Messages are published to topics
  - Subscribers immediately receive messages for their subscribed topics
  - Supports multiple subscriber types (Lambda, SQS, email, SMS, HTTP endpoints)
  - Provides immediate, push-based delivery

## Amazon Simple Queue Service (SQS)

- A fully managed message queuing service
- Key characteristics:
  - Sends, stores, and receives messages between software components
  - Queues messages without requiring other services to be available
  - Supports standard queues (high throughput) and FIFO queues (exactly-once processing)
  - Enables asynchronous processing and workload decoupling

## Use Cases

- Application integration
- Event-driven computing
- Microservices coordination
- Distributed system communication
- Workload decoupling

---

# References

- [[AWS Core Service Categories]]
- [[Server-less Computing]]
