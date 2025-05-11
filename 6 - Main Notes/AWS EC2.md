2025-03-31 21:03

Tags: [[AWS]]

---

## Amazon EC2 (Elastic Cloud Compute):

- Is a ==virtual machine==
- Use ==secure and sizable== compute capacity
- Boot server instance in minutes
- Pay for what you use
- How it works:
  ![[Cloud Practitioner Essentials 2025-01-10 10.10.41.excalidraw]]
- Mainly consist ability of:
  - Renting VM (EC2)
  - Store data in virtual drives ([[EBS]])
  - Distribute load over machines ([[ELB]])
  - Scaling service in a scaling group ([[ASG]])

> [!info] Knowing EC2 is fundamental to understand how Cloud works

### EC2 sizing and config options

- OS: Linux, Windows, MacOS
- How much compute power and cores (CPU)
- How much RAM
- How much storage
- [[Network card]]: speed of card, public IP address
- Firewall rules: security group
- Bootstrap script (configure on launch): [[EC2 user data]]
  [[Launch an AWS EC2 instance]]

### EC2 Info (after created)

![[Pasted image 20250402201626.png]]

- Details:
  - Instance ID
  - [[EC2 IP addresses]]
  - Private DNS
  - Host name
  - State (Running/...)
  - Instance type
  - [[AMI ID]]
  - Platform
  - Key pair name
- Security:
  - [[Security group]]
  - Role 
	![[Pasted image 20250406082504.png]]
- Storage
- Status check
- Monitoring
- Tags

### Connect to EC2
- SSH: [[SSH connect to EC2]]

> [!w] You can only SSH to instances using their public IP

- EC2 Instance Connect (in the browser)

### EC2 placement group
[[EC2 placement group]]

### Elastic network interface (ENI)
[[AWS ENI]]

### EC2 Hibernate
[[EC2 Hibernate]]

### EC2 types:

[[EC2 Types]]

### Prices:
[[EC2 instance purhase options]]

### EC2 Instance Storage

[[EBS]]
[[AMI]]
[[EC2 Instance Store]]

### EC2 Auto scale

- When computing requirement changed -> the capacity is auto scaled up/down
- Use dynamic scale and predictive scale

### Elastic load balancing

- Automatically distribute traffic to multiple resources
- Provide single point of contact for auto-scale group

### AWS messaging services

- Amazon simple notification service (SNS):
  - Messages are published to topics
  - Subscribers immediately and directly receive message for their topics
    ![[Cloud Practitioner Essentials 2025-01-10 11.20.20.excalidraw]]
- Amazon Simple Queue Service (SQS)
  - Send, store and receive message between software components
  - Queue message ==without other services to be available==

### Server-less computing

- **AWS Lambda**:
  - Run code without provisioning or managing server
  - Pay for code running time
  - Use other AWS service to trigger code with Lambda
    ![[Cloud Practitioner Essentials 2025-01-10 11.40.22.excalidraw]]
- **Container Orchestration Service**:
  - Only need to use a container, not care about the server
  - AWS Elastic Container Service (ECS)
    - Run and scale containerized application
    - Use simple API calls to control Docker-enabled application
  - AWS Elastic Kubernetes Service (EKS):
    - Run and scale K8S application
- **AWS Faregate**
  - Run server-less containers with Amazon ECS or EKS
  - Pay only for used resources

---

# References
