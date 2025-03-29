{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Messaging]]

---

# AWS Messaging Services

AWS offers specialized messaging services that facilitate communication between distributed components of applications.

## Amazon Simple Notification Service (SNS)

- Publish-subscribe service for messaging
- Publishers send messages to topics
- Subscribers immediately receive messages from topics they subscribe to
- Supports multiple subscriber types (Lambda, SQS, email, SMS, HTTP endpoints)
- Real-time message delivery to subscribers
- Highly available and durable across multiple Availability Zones

### How SNS Works

1. Create a topic (communication channel)
2. Add subscribers to the topic
3. Publish messages to the topic
4. Messages are immediately delivered to all subscribers

## Amazon Simple Queue Service (SQS)

- Fully managed message queuing service
- Enables decoupling of application components
- Stores messages until they are processed
- Allows asynchronous processing between components
- Messages remain in queue until processed and deleted
- Components can operate independently at their own pace

### How SQS Works

1. Sender sends a message to an SQS queue
2. Message is stored reliably until a consumer retrieves it
3. Consumer processes the message
4. Consumer deletes the message when processing is complete

## Comparison

- **SNS**: Immediate push-based delivery (one-to-many)
- **SQS**: Pull-based messaging (components retrieve messages when ready)

---

# References

- [[AWS Core Service Categories]]
- [[AWS Lambda]]
- [[AWS Serverless Computing]]
