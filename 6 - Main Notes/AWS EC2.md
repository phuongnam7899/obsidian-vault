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
- OS: Linux, Widows, MacOS
- How much compute power and cores (CPU)
- How much RAM
- How much storage
-  [[Network card]]: speed od card, public IP address
- Firewall rules: security group
- Bootstrap script (configure on launch): [[EC2 user data]]
[[Launch an AWS EC2 instance]]

### EC2 Info (after created)
![[Pasted image 20250402201626.png]]
- Details:
	- Instance ID
	- Public [[IPv4]] address (==When the instance is restarted, the public IP may change==)
	- Private IPv4 address (==Never change when instance is restarted==)
	- Private DNS
	- Host name
	- State (Runing/...)
	- Instance type
	- [[AMI ID]]
	- Platform
	- Key pair name
- Security:
	- [[Security group]]
	- Role
- Storage
- Status check
- Monitoring
- Tags
### EC2 types:

- (https://aws.amazon.com/ec2/instance-types/)
- Naming convention: m5.2xlarge
	- m: instance class
	- 5: generation (AWS improve the hardware overtime)
	- 2xlarge: size (the more, the more CPU and storage)

|                       | Feature                                                      | Ideal for                                                                                                                                                                                          |
| --------------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| General purpose ()    | ==balance== compute, memory and networking                   | ==Broad range== of workload (web server, code repo)                                                                                                                                                |
| Compute optimized (c) | Higher performance ==processor==                             | ==High computing application== , ==batch processing== workload, media transcoding, high-performance web server, high perform computing - HPC, scientific modeling, machine learning, gaming server |
| Memory Optimized      | Fast ==performance for memory== intensive work               | ==High performance DB==, Distributed we scale cache stores, [[In-memory databases]] optimized for BI, Application perform real-time processing of unstructured data                                |
| Accelerated computing | Use ==hardware accelerator== to expedite data processing     | Application ==streaming & graphic work==                                                                                                                                                           |
| Storage Optimized     | ==Low latency== and ==high I/O operation== per second (IOPS) | ==Distributed file system== and ==data warehouse== application                                                                                                                                     |

### Prices:

- On demand:
  - No upfront cost / minimum contract
  - Ideal for short term, irregular workload
- Spot:
  - When there's some free resource of the amazon system, client can use it. But when it is needed again, client will be disconnected from it
  - Cheaper than on-demand (-90%)
  - Ideal for flexible start and end time work and can withstand interruption
- Reserved:
  - Require 1-year or 3-year term commitment
  - Cheaper than on-demand
- Computed saving:
  - 1 or 3 year commitment
  - Cheaper than on-demand for consistent computing

### Dedicated computing:

- Dedicated Instance:
  - When don't want to share the infra of instance with other customers, AWS still manage its placement
  - Higher price
- Dedicated host
  - When you want to run in completely separate physical server (do not share with other customers).
  - You have full control on the server than dedicated instance
  - Most expensive option

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