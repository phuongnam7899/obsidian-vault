{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Messaging]]

---

# AWS Messaging Services

AWS provides specialized messaging services to facilitate communication between distributed system components:

## Amazon Simple Notification Service (SNS)

- Pub/sub messaging service
- Messages are published to topics
- Subscribers receive messages immediately
- Enables parallel processing
- Push-based delivery

![SNS Model](placeholder-for-sns-diagram)

## Amazon Simple Queue Service (SQS)

- Fully managed message queuing service
- Enables decoupling of application components
- Messages can be stored until other services are available to process them
- Acts as a buffer between components
- Pull-based delivery

These messaging services help build applications with loosely coupled, distributed components that can scale independently.

---

# References

[[AWS Core Service Categories]]
[[Amazon EC2]]
