{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Compute]]

---

# Amazon EC2 (Elastic Cloud Compute)

- Virtual machines running in AWS cloud
- Provides secure and resizable compute capacity
- Servers can be launched in minutes
- Pay-as-you-go pricing model

## EC2 Instance Types

| Type                  | Features                                        | Ideal Use Cases                                                     |
| --------------------- | ----------------------------------------------- | ------------------------------------------------------------------- |
| General Purpose       | Balanced compute, memory, and networking        | Broad range of workloads, web servers, small databases              |
| Compute Optimized     | High-performance processors                     | Batch processing, scientific modeling, high-performance web servers |
| Memory Optimized      | Fast performance for memory-intensive workloads | High-performance databases, in-memory caches                        |
| Accelerated Computing | Hardware accelerators for data processing       | Machine learning, graphics processing                               |
| Storage Optimized     | Low latency and high I/O operations per second  | Distributed file systems, data warehousing applications             |

## EC2 Pricing Models

- **On-Demand Instances**:
  - No upfront costs or minimum contracts
  - Ideal for short-term, irregular workloads
- **Spot Instances**:
  - Use spare EC2 capacity
  - Up to 90% discount compared to On-Demand
  - Can be terminated when capacity is needed elsewhere
  - Ideal for workloads with flexible start/end times
- **Reserved Instances**:
  - 1 or 3-year term commitment
  - Significant discount compared to On-Demand
  - Ideal for predictable workloads
- **Compute Savings Plans**:
  - 1 or 3-year commitment to consistent amount of compute usage
  - Flexible across instance family, size, OS, and region

## EC2 Dedicated Hosting Options

- **Dedicated Instances**:
  - Run on hardware dedicated to a single customer
  - May share hardware with other instances from the same AWS account
  - AWS manages instance placement
- **Dedicated Hosts**:
  - Physical server dedicated entirely to your use
  - Full control over instance placement
  - Visibility into underlying physical server
  - Most expensive option

---

# References

- [[AWS Core Service Categories]]
- [[EC2 Auto Scaling]]
- [[Elastic Load Balancing]]
