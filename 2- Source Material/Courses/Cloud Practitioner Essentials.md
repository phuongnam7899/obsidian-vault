Source link: 

Status: #source-eating 

---

# Module 1: Introduction to AWS
- What is cloud computing?
	- Allow clients to ==access the services== on demands
	- ==Avoid upfront investment==
	- ==Pay only for what used==
- Cloud-based deployment:
	- Run all application's part on cloud
	- Migrate existing applications to cloud
	- Create new application on cloud
- On-premises (Private cloud) deployment:
	- Use virtualization and resource management to deploy
	- Use application management to control resources used
- Hybrid deployment:
	- Combine cloud and on-premises -> connect services
- Amazon tried AWS with its own retail business first -> then sell it to other

> [!s] Benefits of cloud
> - No upfront investment (servers, data center, system manager,...). Only pay for what you used
> - Can focus on application and customer (not care about the infrastructure)
> - No need to care about how much resource the system need -> scale in/out as needed
> - Small gap between wanting and having resources (if on-premises, you need to order new resources by yourself)
> - Global access fast
> - Cheaper pay-on-demand because of aggregated usage

- Core AWS service categories:
	- Compute
	- Storage
	- Database
	- Security, Identity & Compliance
	- Management and Governance

# Module 2: Compute in the cloud
## Amazon EC2 (Elastic Cloud Compute): 
- Is a ==virtual machine==
- Use ==secure and sizable== compute capacity
- Boot server instance in minutes
- Pay for what you use
- How it works:
	![[Cloud Practitioner Essentials 2025-01-10 10.10.41.excalidraw]]
### EC2 types: 
- (https://aws.amazon.com/ec2/instance-types/)

|                       | Feature                                                      | Ideal for                                                        |
| --------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| General purpose       | ==balance== compute, memory and networking                   | ==Broad range== of workload                                      |
| Compute optimized     | Higher performance ==processor==                             | ==High computing application== and ==batch processing== workload |
| Memory Optimized      | Fast ==performance for memory== intensive work               | ==High performance DB==                                          |
| Accelerated computing | Use ==hardware accelerator== to expedite data processing     | Application ==streaming & graphic work==                         |
| Storage Optimized     | ==Low latency== and ==high I/O operation== per second (IOPS) | ==Distributed file system== and ==data warehouse== application   |
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
		- Use simple API calls to control Docker-enabled  application
	- AWS Elastic Kubernetes Service (EKS):
		- Run and scale K8S application
- **AWS Faregate**
	- Run server-less containers with Amazon ECS or EKS
	- Pay only for used resources
# Module 3: Global infrastructure and Reliability
- Build a global footprint: route user to nearest available footprint
![[Cloud Practitioner Essentials 2025-01-13 08.05.33.excalidraw]]
## Select region
Determine religion for services, data, applications based on:
- Legal: is it allowed to placed there?
	- For example: GDPR (General Data Protection Regulation): data from EU is not allowed to move to outer of EU
- Nearest to customer: to reduce delay
- Available services within religion: some new religions may not support all services (might need to use from other regions -> slower)
- Price
## Availability zones
![[Cloud Practitioner Essentials 2025-01-13 08.35.12.excalidraw]]
- Each religion contain multiple logically isolated zone that contain data centers of that religion -> when an availability zone got problem -> use other one to ensure the availability
## Global content delivery
- Amazon CloudFront: is a CDN service provided by Amazon, put (cache) the content to Edge Location - nearer location from user -> increase speed 
- AWS Outpost: Extend AWS infra and services to your on-premises data center
## Interact with AWS services
- Actions:
	- Launch EC2 instances
	- Create load balancer
	- Invoke lambda function
- Can trigger action through:
	- AWS management console
	- AWS CLI
	- Software development kits
# Module 4: Networking
## Amazon VPC (Virtual Private Cloud)
- 
# Module 5: Storages and Database
# Module 6: Security
# Module 7: Monitoring and Analytics
# Module 8: Pricing and Support 
# Module 9: Migration and Innovation
# Module 10: AWS Certified Cloud Practitioner Basic 

---