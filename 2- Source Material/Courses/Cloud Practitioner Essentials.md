Source link:

Status: #source-eating

---

# Module 2: Compute in the cloud

[[AWS EC2]]
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


[[Amazon VPC (Virtual Private Cloud)]]
## Interact with global network

- DNS (Domain Name System)
  ![[Cloud Practitioner Essentials 2025-01-13 11.02.51.excalidraw]]
- Amazon Route 53: - Route user to internet application - Connect user request to infra inside/outside of AWS - Manage DNS record for domain name
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

## AWS Artifacts

Provide on-demand access to security and compliance reports and select online agreements:

## Customer Compliance Center

Contain resources to learn about AWS compliance

## AWS Web Application Firewall (WAF) and Shield

- WAF:
  - Primarily for layer 7 attacks (application layer) such as SQL Injection, XSS, HTTP Flood attacks
  - Allow to define custom rules to filter/block malicious requests
- Shield:
  - Protect application from level 3 & 4 attacks (network and transport) such as DoS/DDoS
  - 2 tiers: Standard and Advanced
- WAF and Shield could be used together for better protection

## AWS Key Management Service (KMS)

- Help customer perform encryption operation by using cryptographic keys
- Can custom the access level for each key

## Amazon GuardDuty

- Provide intelligent threats detection for AWS products/service
- It detect threats by analyze the logs of all actions of other services

# Module 7: Monitoring and Analytics

## Cloudwatch

- Track metric of service
- Provide dashboard

## CloudTrail

- ==Track user activities and API request== through the AWS infra
- Help trace for the process that make something happen or analyzing the actions
- Answer ==what, who, when, how== questions for each event
- Automatically ==detect unusual account== activity

## AWS Trust Advisor

- Give ==real-time guidance== to improve the AWS environment
- ==Compare== your infra ==to best practices== in 5 categories
- ==Evaluate and implement guidance== at all stage of deployment
- Provide dashboard to show:
  - Number of no-problem items
  - Number of recommended investigation
  - Number of recommended actions
- 2 level: Basic and Advanced (cost)

# Module 8: Pricing and Support

- Free: https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all
- Overall concepts:
  - Pay as you go
  - Pay less where you reserve
  - Pay-less with volume-based discount
- Calculator: https://calculator.aws/#/
- AWS cost explorer to visualize and understand the cost
- Support:
  - Basic:
    - Technical paper, docs and communities
    - AWS Personal Heath Dashboard
    - Limited Trust Advisor

# Module 9: Migration and Innovation

## Perspectives

- Business Capacities:

| Perspective | Goal                                                                                              | Main Roles                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Business    | Ensure that ==IT aligns with business== ==needs== and <br>IT investment linked to business result | - Business Manager<br>- Finance Manager<br>- Budget Owner<br>- Strategy stakeholders |
| People      | Develop ==change management strategy== for the <br>cloud adoption through the organization        | - HR<br>- Staffing<br>- People manager                                               |
| Governance  | Focus on ==skills and processes== to align IT strategy<br> and business strategy                  | - CIO<br>- Program managers<br>- Enterprise architect<br>- BA<br>- Portfolio manager |

- Technical Capacities:

| Perspective | Goal                                                                                                                    | Main Roles                                               |
| ----------- | ----------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Platform    | Includes ==principles and patterns== for implement new<br>solution in cloud + ==migrate on-premises== workload to cloud | - CTO<br>- IT manager<br>- SA                            |
| Security    | Ensure the ==organization meet security objectives== for visibility,<br>auditability, control and agility               | - CISO<br>- IT Security manager<br>- IT security analyst |
| Operations  | Enable, run, use, operate and recover IT workloads to the agreed level                                                  | - IT Operation Manager<br>- IT Support Manager           |

## Migration strategies

### 1. Re-host

- Only change the host, every thing else keep the same

### 2. Re-platform

- Change the platform of 1 or more component in the architect
- Example:

---
