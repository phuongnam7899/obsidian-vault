{{date}} {{time}}

Tags: #AWS #Cloud #Storage

---

- AWS offers various storage services to meet different data storage needs
- Storage types include block storage, object storage, and file storage

## Block Storage

- Storage where data is divided into fixed-size blocks
- Well-suited for applications requiring frequent data changes
- AWS block storage options:
  - **Amazon EBS (Elastic Block Store)**:
    - Persistent block storage volumes for EC2 instances
    - Data persists independently from instance lifecycle
    - Supports snapshots for point-in-time backups
  - **Instance Store**:
    - Temporary block storage directly attached to EC2 instances
    - Data is lost when the instance stops or terminates

## Object Storage

- Storage where data is stored as objects with data, metadata, and unique key
- AWS object storage service:
  - **Amazon S3 (Simple Storage Service)**:
    - Stores objects in "buckets" with unlimited storage capacity
    - Maximum object size of 5TB
    - Configurable permissions for access control
    - Multiple storage classes for different use cases:
      - S3 Standard: Frequently accessed data
      - S3 Standard-IA: Infrequently accessed data, lower storage cost but higher retrieval cost
      - S3 One Zone-IA: Lower availability but cheaper than Standard-IA
      - S3 Intelligent-Tiering: Automatically moves data between tiers based on access patterns
      - S3 Glacier: Low-cost archival storage with retrieval times of minutes to hours
      - S3 Glacier Deep Archive: Lowest-cost storage with retrieval times of up to 12 hours

## File Storage

- Storage that provides file-level access to multiple clients
- AWS file storage service:
  - **Amazon EFS (Elastic File System)**:
    - Fully managed file system for use with EC2 instances
    - Supports thousands of concurrent connections
    - Automatically scales as data is added or removed
    - Data stored across multiple Availability Zones for high availability

---

# References

- [[AWS Core Service Categories]]
- [[AWS Database Services]]
