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
- Enable you to launch resources in a virtual private network that you define
- Subnet: a section in VPC in which you can place group of isolate resources
![[Cloud Practitioner Essentials 2025-01-13 09.33.03.excalidraw]]
- Internet Gateway: a gate to handle request between VPC's ==public subnet== and  the internet
- Virtual Private Gateway: a gate to handle requests between VPC's ==private subnets== and the corporate network through internet -> 
- If you want a more stable connection for private subnet  -> use AWS direct connection
- To more detailed manage the access to VPC -> use the:
	- Network Access Control List (ACL) (==a virtual firewall for subnets==). Default:
		- Default network ACL allow all inbound and outbound traffic
		- Custom network ACL deny all inbound and outbound traffic (
		- Perform Stateless packet filtering
	- Security groups: a ==virtual firewall for EC2 instance or group of instances==:
		- By default ==denies all in== traffic and ==allow all out== traffic
		- Perform stateful packet filtering: remember the previous decision that were made
## Interact with global network
- DNS (Domain Name System)
![[Cloud Practitioner Essentials 2025-01-13 11.02.51.excalidraw]]
- Amazon Route 53: 
	- Route user to internet application
	- Connect user request to infra inside/outside of AWS
	- Manage DNS record for domain name
![[Cloud Practitioner Essentials 2025-01-13 11.10.56.excalidraw]]
# Module 5: Storages and Database
## Storage

### Block storage
- File are separated into blocks of data
- Used for application that run on Amazon EC2 instances (because data is frequently changed)
- Example: SSD, USB, 
- **Instance Store** (store that attached to an instance -> when the instance is down -> the store is deleted), 
- **Amazon EBS Volumes**
	- store attached to an instance (single availability zone), but when the instance is down -> data is persistent
	- EBS snapshot: is backup. Only changed data since last snapshot is backed up
### Object storage
- Data in object store is objects with ==data==, ==metadata== and ==key==
- Amazon Simple Storage Service (**Amazon S3**):
	- Stores objects in ==buckets==
	- Unlimited number of objects, maximum 5TB per object
	- Set ==permission== to control access to objects
	- There are ==many storage (classes) types== that could be chosen for different use cases:
		- S3 standard:
			- Designed for ==frequently accessed== data
			- Data stored in minimum of 3 Availability Zones
		- S3 standard-IA:
			- For ==infrequently accessed== data
			- Similar to standard but ==lower price for store and higher price for retrieval==
		- S3 One Zone-IA:
			- Similar to standard-IA but only store data in 1 Availability Zone -> lower availibility
			- Lower price than standard-IA
		- S3 Intelligent-Tiering:
			- For unknown or changing access frequency
			- Require small monthly monitor and automation fee (per object)
		- S3 Glacier:
			- Low-cost
			- Ideal for data archiving
			- Retrieve very slowly (minutes to hours)
		- S3 Glacier Deep Archive
			- Lowest-cost
			- Retrieve objects within 12h
### File storage (Amazon Elastic File System - EFS)
- Multiple clients (server, user, application) can access to data stored in shred file folders
- Store data in scalable file system
- Provide data to thousands of EC2 instance concurrently
- Store data in and across multiple Availability Zone
## Databases
### Amazon Relational Database Service (RDS)
- ==Operate and scale== relational databases in AWS Cloud
- ==Automate== time-consuming ==administrative tasks==
- Store and transmit data ==securely==
- Supported all engines: Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, Microsoft SQL Server
- Amazon Aurora:
	- store data in an enterprise-class relational database
	- reduce cost by remove unnecessary I/O operation
	- replicate 6 copies in 3 Availability zones
### Amazon DynamoDB
- For non-relational database
- Is a server-less key-value database
- Automatically scale
- Can handle 10 trillions requests per day
### AWS Database Migration Service (DMS)
- Used to migrate relational/non-relational/other database types to another
### Other DB service
- Amazon Redshift: query and analyze data across a data warehouse
- Amazon DocumentDB: Run MongoDB workload in a document database service
- Amazon Neptune: Run application that use highly connected dataset
- Amazon QLDB: to review changes history of data (like blockchain)
- Amazon Managed Blockchain: Run a decentralize ledger DB
- Amazon ElasticCache: adding caching layers for application to increase speed
- Amazon Dynama Accelerator: Improve Dynamo response time (from single digit mili-seconds to microseconds)

# Module 6: Security
## Shared responsibility model
- Customer: take responsibility for what they created
	- Customer data
	- Platform, application, Identity and Access management
	- Operating System, Network and Firewall config
		- Client-side encrypt
		- Server-side encrypt
		- Networking Traffic protection (security group, access list)
- AWS:
	- Hardware/AWS Global Infra
		- Religions
		- Availability Zones
		- Edge location
	- Software:
		- Computing
		- Storage
		- Database
		- Networking 
## AWS Identity and Access Management (IAM)
- Allow manage access to AWS services and resources
- Features:
	- IAM user
		- Each user has access key, secret access key and password
	- IAM policy: define the action could be take with objects in some location
	- IAM role: 
		- identity that can assume to gain ==temporary== access to permissions
		- user can have ==multiple roles==
	- IAM group: multiple users
	- Multi-factor authentication (MFA)
		- Beside username and password, it require 1 or more things
> [!i] Best practices:
> - Use root user (first user) to create another user (User A) -> use user B to create other other. Avoid using root user
> - Create different user for each person that need to access
> - For policies: follow the security principle of least privilege
> - Attach policy to group instead of individual
> - 


# Module 7: Monitoring and Analytics
# Module 8: Pricing and Support 
# Module 9: Migration and Innovation
# Module 10: AWS Certified Cloud Practitioner Basic 

---